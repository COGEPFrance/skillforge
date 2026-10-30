# Règles de développement

## Préparation et périmètre

- Créer une branche dédiée depuis la dernière version de `origin/main` avant de
  commencer le travail.
- Examiner l'architecture, les dépendances et les implémentations existantes avant
  d'écrire du code.
- Les règles de ce document priment sur les habitudes du code existant. Conserver
  une convention locale seulement si elle respecte ces règles et répond au besoin ;
  sinon, corriger la dette directement liée au changement sans lancer de refonte
  globale. Préserver la compatibilité sans reproduire les mauvaises pratiques.
- En cas d'ambiguïté ayant un impact architectural, demander une clarification,
  analyser la réponse et proposer une règle réutilisable si elle évite la même
  ambiguïté dans d'autres projets.
- Limiter chaque changement aux modifications et refactorings directement
  nécessaires à la demande. Traiter séparément toute amélioration sans rapport
  direct afin de faciliter la review, les tests et un éventuel retour arrière.
- Lorsqu'une amélioration importante mais hors périmètre est découverte, ne pas
  l'implémenter : créer ou compléter `upgrade.md` à la racine. Rechercher d'abord
  un bloc similaire pour le mettre à jour plutôt que le dupliquer. Chaque bloc
  indique un titre, le constat et son contexte, le risque, l'évolution attendue,
  le périmètre probable et les critères de validation, avec assez d'informations
  pour permettre à une IA de créer une issue dédiée.
- Après un commentaire de review, rechercher le même problème dans le périmètre
  concerné afin de corriger sa cause, pas seulement la ligne signalée.
- Si une suggestion dégrade le typage, l'architecture ou la lisibilité, expliquer
  le risque et proposer une meilleure solution.

## Architecture et responsabilités

- Définir clairement la responsabilité de chaque composant et séparer logique
  métier, orchestration, transformation et infrastructure.
- Respecter la direction des dépendances : le métier dépend de contrats, jamais
  d'implémentations techniques.
- Préférer la composition pour réutiliser ou combiner des comportements. Utiliser
  l'héritage uniquement lorsqu'il représente une véritable relation de
  spécialisation et respecte le contrat du type parent.
- Concevoir la solution la plus simple qui satisfait complètement le besoin.
- Avant de créer une classe, identifier sa nature et sa responsabilité principale,
  puis la placer dans la couche correspondante. Son emplacement dépend de son rôle,
  jamais de la proximité de son premier consommateur.
- Une fonction ou méthode possède une responsabilité unique ; une classe possède
  une raison principale de changer.
- Avant de créer un contrat, un modèle ou un mapping, vérifier si un équivalent
  existe déjà et le réutiliser lorsqu'il possède la même signification et la même
  responsabilité. Extraire une logique dans un composant partagé uniquement si
  elle représente un concept autonome ou sert plusieurs consommateurs réels ;
  sinon, la conserver près de son unique consommateur.
- Avant de créer une solution spécifique, privilégier une fonctionnalité du
  langage ou de sa bibliothèque standard lorsqu'elle est compatible avec la
  version ciblée et rend le code plus simple, lisible ou mieux typé. Ne pas
  modifier une implémentation uniquement pour utiliser une fonctionnalité plus
  récente sans bénéfice concret.

## Interfaces, protocoles et mixins

- En Python, utiliser une `ABC` pour une famille fermée d'implémentations internes
  qui héritent explicitement d'un même contrat.
- Utiliser un `Protocol` lorsqu'un besoin réel de typage structurel existe, par
  exemple pour accepter une implémentation externe sans héritage ou typer la
  surface limitée attendue par un mixin.
- Ne pas utiliser de mixin pour fragmenter ou recomposer le comportement d'un
  modèle Pydantic. Une classe `*Mixin` ne doit pas hériter de `BaseEntity`,
  `BaseModel` ou d'une base d'agrégat afin d'être recombinée dans une entité.
- Lorsqu'un mixin non-Pydantic répond à un besoin démontré, typer la surface
  minimale de son hôte avec un `Protocol` étroit plutôt qu'avec une classe fictive,
  `Any`, un cast large ou une désactivation de Mypy.

## Modèles et contrats de données

- Toute classe qui transporte des données structurées utilise un modèle Pydantic
  explicitement typé, y compris pour des données internes ou techniques.
- Une entité représente un concept métier doté d'une identité, d'un cycle de vie
  et d'invariants ; elle vit dans `core/domain/entity/`.
- Un DTO transporte des données entre composants sans identité métier ; il vit
  dans `core/domain/dto/` et porte le suffixe `Dto`.
- Choisir selon le besoin entre entité, agrégat, value object, commande, query,
  DTO et contexte. Ne jamais placer un DTO dans `entity/` ni considérer un objet
  de contexte comme une entité.
- Lorsqu'au moins quatre paramètres représentent un même concept, rechercher un
  objet métier ou de contexte existant avant d'en créer un.
- Remplacer les valeurs métier répétées par un type, un enum ou une constante.
- Éviter les paramètres booléens qui modifient le comportement d'une fonction ;
  préférer des opérations explicitement nommées.

## Use cases, services et adapters

- Un use case représente une intention métier autonome et possède des contrats
  d'entrée et de sortie Pydantic explicitement typés.
- Un use case orchestre des dépendances au travers de ports. Il peut préparer des
  entrées typées, choisir le service applicatif à appeler et construire le
  résultat, mais n'implémente pas de processus technique réutilisable.
- Déléguer les boucles de traitement, la pagination, l'authentification, les flux
  temporaires, le parsing, la sérialisation et la préparation de données provenant
  de plusieurs sources à un service, un helper ou un adapter selon leur nature.
- Un use case ne déclare pas de DTO, contexte, serializer ou helper technique dans
  son propre fichier. Une transformation qui n'a qu'un consommateur reste dans un
  module privé limité à ce composant ; elle ne devient partagée que si elle sert
  plusieurs consommateurs ou représente un concept autonome.
- Remettre en question toute méthode privée de use case qui récupère plusieurs
  dépendances, transforme leurs résultats et construit un DTO pour un autre
  service ; cette orchestration appartient généralement à un service de
  préparation dédié.
- Un use case ne lit pas directement le système de fichiers, ne manipule pas
  `Path`, ne parse pas de JSON et ne connaît aucun format de stockage. Les données
  externes sont lues par un adapter derrière un port.
- Un use case ne parse, ne sélectionne ni ne sérialise des payloads de protocole.
- Une variante technique ou un sous-processus devient un service, un helper ou une
  stratégie, pas un nouveau use case.

## Dispatch et registres typés

- Pour une famille fermée, petite et stable, utiliser un `match` exhaustif s'il
  reste lisible et vérifiable par le typage.
- Utiliser un registre typé lorsque les stratégies sont extensibles, nombreuses ou
  enregistrées séparément. En Python, utiliser directement les classes comme clés,
  selon le principe de `Strategy::class` en PHP.
- Typer précisément les configurations, stratégies et retours, puis refuser tout
  type non enregistré avec une erreur claire.
- Tester que chaque configuration supportée possède un handler lorsque le choix
  repose sur un registre.

## Persistance et frontières du core

- Le core manipule des agrégats, value objects, commandes, queries et DTO typés ;
  il ne reçoit ni ne retourne de document de persistance brut. Cela inclut
  `dict[str, Any]`, `_id` et les formes Mongo historiques.
- Un port de repository retourne un agrégat, un value object ou un DTO de lecture
  typé. Interdire les signatures telles que `-> dict`, `-> list[dict]`,
  `document: dict[...]` ou `payload: dict[...]` lorsqu'elles représentent un objet
  métier ou persistant.
- Seul un adapter de persistance convertit un document en modèle Pydantic et
  inversement.
- Les mappers Mongo vivent dans `adapters/output/` et portent les noms, formats
  historiques, `_id`, encodages BSON, dates et index techniques. Ces détails ne
  sont pas connus de `core/domain/` ni de `core/use_cases/`.
- Un use case n'appelle jamais `to_document()` ou `from_document()` : il demande
  une entité typée au repository, applique une opération métier, puis sauvegarde
  l'entité typée.
- Interdire dans le core les merges tels que `{**entity.to_document(), **updates}`.
  Toute mise à jour passe par une méthode métier nommée qui valide les invariants
  et les transitions.
- Autoriser `model_dump()` uniquement à une frontière d'adapter, pour des logs
  structurés ou pour construire immédiatement un autre modèle Pydantic validé
  lorsque les contrats sont distincts et qu'aucune projection typée n'est adaptée.
  Ne jamais l'utiliser pour contourner une mise à jour métier typée.

## Typage et gestion des erreurs

- Préserver un typage précis : éviter les types trop génériques, les valeurs
  magiques, les `Any` et les casts larges utilisés pour contourner le type checker.
- Interdire `# mypy: ignore-errors` et toute désactivation globale de Mypy dans un
  module de production. Une exception doit être locale, minimale, justifiée et
  indiquer le code d'erreur Mypy concerné.
- Produire des erreurs explicites, précises et actionnables. Éviter les captures
  d'exceptions trop larges.
- Une erreur du traitement principal ne doit jamais être masquée ni transformée en
  faux succès. Réutiliser la réponse standard lorsqu'elle existe au lieu de la
  reconstruire depuis une exception brute.
- Un effet secondaire explicitement qualifié de `best effort`, exécuté après le
  succès métier, peut être isolé si les opérations éligibles ont une source unique
  et sont filtrées avant exécution. Toute défaillance reste journalisée et
  observable ; les cas inclus, exclus et en échec sont testés.

## Nommage et documentation

- Utiliser des noms précis qui expriment l'intention métier, avec un verbe pour une
  méthode et un nom décrivant le rôle ou le contenu pour une variable.
- Employer le même vocabulaire dans le code, les tests et la documentation. Éviter
  les noms vagues, ambigus hors contexte et les abréviations non standard.
- Préférer un nom explicite, même plus long. Une méthode difficile à nommer possède
  souvent plusieurs responsabilités.
- Documenter uniquement une décision, un invariant, un risque, une contrainte ou
  un comportement non évident. Ne jamais paraphraser le code ni dupliquer la même
  information entre le module, la classe, la fonction et la documentation.
- Une docstring de module résume sa responsabilité en une phrase.

## Complexité, lisibilité et performance

- Évaluer la complexité de chaque fonction, pas uniquement la moyenne, et viser
  une complexité cyclomatique inférieure ou égale à 10.
- Réduire aussi la complexité cognitive et limiter naturellement l'imbrication à
  deux niveaux. Utiliser des retours anticipés lorsqu'ils améliorent la lecture.
- Refactorer selon les responsabilités, jamais pour tromper une métrique ou
  fragmenter artificiellement le code en micro-fonctions.
- Évaluer la complexité algorithmique selon le volume réel des données et ajouter
  des benchmarks uniquement pour les traitements critiques.

## Tests et contrôles d'architecture

- L'arborescence des tests unitaires reflète celle des modules testés.
- Protéger par un test d'architecture toute frontière critique vérifiable
  automatiquement, notamment les dépendances interdites et l'exhaustivité des
  registres.
- Dans `core/use_cases/`, interdire notamment les dépendances directes à
  `pathlib`, `json`, `tempfile`, aux clients HTTP et aux adapters concrets.
- Interdire les dataclasses dans `core/` et `adapters/` avec une règle Ruff ou un
  test AST afin que les données structurées utilisent des modèles Pydantic typés.
