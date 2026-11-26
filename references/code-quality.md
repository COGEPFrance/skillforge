# Qualité du code et périmètre

- SRP : chaque composant et chaque fonction ont une responsabilité et une raison principale de changer ; privilégier les petites fonctions faciles à comprendre, maintenir et tester.
- KISS : choisir la solution la plus simple qui satisfait le besoin et ses contraintes.
- DRY : ne pas dupliquer un même traitement ; le mutualiser dans une fonction ou un composant adapté. Identifier son sens et son contrat avant de traiter une ressemblance comme une duplication.
- SOTA signifie pratiques maintenues, éprouvées et adaptées au besoin, sans recherche systématique de nouveauté.
- Définir des entrées, sorties et erreurs explicitement typées ; isoler les formats externes aux frontières.
- Produire des erreurs actionnables, sans masquer un échec en faux succès. Ne pas ajouter d’abstraction ou de dépendance sans besoin identifié.
- Limiter le changement au besoin traité. Le refactoring nécessaire peut accompagner ce changement ; le refactoring indépendant suit le [parcours dédié](../workflows/refactoring-scope.md).

## Vérification

Utiliser les outils statiques et conventions effectivement configurés dans le projet. Relier tout constat à un effet concret sur le changement, sans imposer une refonte hors périmètre.

## Fonctions, responsabilités et mutualisation

- Garder les fonctions petites et centrées sur une intention. Décomposer une
  fonction longue en responsabilités et étapes nommées cohérentes ; le seul bon
  résultat à l’exécution ne justifie pas de conserver des blocs indépendants
  difficiles à comprendre ou tester isolément. Une exception doit être motivée
  par une contrainte concrète du projet, pas par la seule habitude.
- Limiter les paramètres en entrée et les informations distinctes en sortie.
  Séparer les intentions indépendantes ; regrouper des données qui portent un
  même concept dans un contrat typé adapté. Ne pas masquer une API trop large
  dans un dictionnaire, une liste de paramètres ou un objet fourre-tout.
- Rechercher les autres occurrences d’un même traitement et les remplacer par
  une capacité commune. Montrer le traitement répété et les points où une même
  évolution doit être reportée ; une divergence déjà produite n’est pas requise
  pour constater une duplication inutile.
- Pour des variantes d’un traitement commun, factoriser la partie partagée et
  isoler la variation. Héritage ou dérivation conviennent lorsqu’une abstraction
  et un contrat communs sont réellement respectés ; une fonction paramétrée ou
  la composition peuvent aussi convenir. Ne pas imposer un héritage qui change
  les préconditions ou résultats promis aux consommateurs.
- Des calculs ou opérateurs identiques dans des règles aux sens et évolutions
  distincts ne suffisent pas à établir un traitement commun. Expliciter cette
  distinction ; elle ne doit pas servir de prétexte à recopier la même règle.
- Ne pas découper mécaniquement ligne par ligne ni créer une forêt de fonctions
  sans responsabilité nommable pour satisfaire une métrique. Les petites
  fonctions doivent réduire la complexité à comprendre et à tester.

## Correction et effets locaux

Suivre les chemins nominaux, les bornes et les échecs pertinents. Examiner les
mutations des entrées, valeurs par défaut mutables, alias et états partagés entre
appels, ainsi que les effets secondaires et ressources du chemin concerné.
Un traitement d’erreur doit préserver l’échec et sa cause utile plutôt que
retourner une valeur interprétée comme un succès. Pour l’asynchronisme, suivre
les opérations réellement attendues, leurs erreurs et leur nettoyage ; ne pas
confondre création d’une coroutine et exécution de l’opération promise.

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
