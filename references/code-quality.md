# Qualité du code et périmètre

- SRP : chaque composant a une responsabilité et une raison principale de changer.
- KISS : choisir la solution la plus simple qui satisfait le besoin et ses contraintes.
- DRY : mutualiser un concept réellement partagé ; ne pas fusionner des traitements sur leur seule ressemblance.
- SOTA signifie pratiques maintenues, éprouvées et adaptées au besoin, sans recherche systématique de nouveauté.
- Définir des entrées, sorties et erreurs explicitement typées ; isoler les formats externes aux frontières.
- Produire des erreurs actionnables, sans masquer un échec en faux succès. Ne pas ajouter d’abstraction ou de dépendance sans besoin identifié.
- Limiter le changement au besoin traité. Le refactoring nécessaire peut accompagner ce changement ; le refactoring indépendant suit le [parcours dédié](../workflows/refactoring-scope.md).

## Vérification

Utiliser les outils statiques et conventions effectivement configurés dans le projet. Relier tout constat à un effet concret sur le changement, sans imposer une refonte hors périmètre.

## Typage Python et contrôles

Pour du Python modifié, conserver des types précis ; ne pas cacher un objet
métier connu derrière `dict`/`Any` ni contourner le type checker par un cast large.
Interdire `# mypy: ignore-errors` et les désactivations globales dans un module de
production. Une exception indispensable reste locale, minimale, justifiée et
associée au code d’erreur concerné ; ne pas dégrader un contrat pour rendre un
outil silencieux.

Une valeur métier répétée mérite un type, enum ou constante si elle porte une
signification partagée ; ne pas extraire toutes les valeurs identiques par
principe. Capturer les erreurs attendues ; une capture large à une frontière
doit préserver la cause et un échec explicite, sans transformer toute erreur en
succès.

Exécuter les outils configurés avec leurs versions de projet. Si Ruff est retenu,
vérifier séparément lint et format (`ruff check`, `ruff format --check`) sur le
périmètre applicable. Signaler un contrôle de format absent de la CI lorsque
c’est pertinent, sans réécrire la CI hors demande. Une exclusion doit être
explicite dans la configuration, pas obtenue en retirant silencieusement un
fichier du contrôle.

En revue, examiner la complexité par fonction touchée : les repères historiques
10 (cyclomatique) et deux niveaux d’imbrication sont des signaux à discuter, pas
des seuils bloquants hors quality gate configurée. Ne pas fragmenter le code
pour contourner une métrique. Examiner un groupe de paramètres ou des booléens
qui portent plusieurs intentions ; le seuil de quatre paramètres et la seule
présence d’un booléen ne justifient pas un nouvel objet ou une API distincte.

## Effets secondaires optionnels

Consulter ce cas uniquement si le contrat distingue explicitement un succès
métier et un effet optionnel exécuté après lui. Ne jamais requalifier en
`best effort` une écriture ou publication nécessaire à ce succès. Définir les
opérations éligibles à un seul endroit, filtrer avant exécution et garder les
échecs observables. Tester les effets inclus, exclus et en échec ; un échec du
traitement principal conserve sa réponse d’erreur standard lorsqu’elle existe.
