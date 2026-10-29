- Faire une nouvelle branch a partir de main distant qui est sur la dernière version avant de commencer le travail.
- Les règles primes sur les habitudes du code existant.
- Le code existant fournit du contexte, mais ne constitue jamais une preuve
  de qualité ni un modèle à reproduire.
- Examiner l’architecture et les dépendances avant d’écrire du code.
- Étudier les implémentations existantes de manière critique.
- Ne jamais reproduire une dette technique uniquement par cohérence.
- Préserver la compatibilité sans propager les mauvaises pratiques.
- En cas d’ambiguïté ayant un impact architectural, demander une clarification et analyser la reponse pour proposer une regles qui permet d'éviter davoir la meme question dans un autre projet.
- Définir clairement la responsabilité de chaque composant.
- Séparer logique métier, orchestration, transformation et infrastructure.
- Respecter strictement la direction des dépendances.
- Faire dépendre le métier de contrats, jamais d’implémentations techniques.
- Préférer la composition à l’héritage.
- Ne créer une abstraction que pour répondre à un besoin réel.
- Éviter les classes génériques, factories, mixins ou couches sans bénéfice
  démontrable.
- Concevoir la solution la plus simple satisfaisant complètement le besoin.
- Préférer un dispatch extensible uniquement s’il reste lisible et correctement
  typé ; ne pas remplacer systématiquement un `match` exhaustif. 
- Identifier les conventions architecturales établies dans le projet avant de
  choisir une nouvelle construction technique.
- Lorsqu’une convention existante est correcte et répond au besoin, la
  respecter plutôt que d’introduire une autre approche.
- [rework] Ne pas utiliser une fonctionnalité moderne uniquement parce qu’elle est
  disponible ; SOTA ne doit jamais primer sur la cohérence et KISS. 
- En Python, utiliser une interface `ABC` pour une famille fermée
  d’implémentations internes devant hériter explicitement d’un même contrat.
- Utiliser `Protocol` uniquement lorsqu’un besoin réel de typage structurel
  existe, notamment pour accepter des implémentations externes sans héritage.
- [rework] Un use case orchestre, il n’implémente pas un processus technique réutilisable.
 Il peut préparer des DTO, résoudre les dépendances nécessaires, choisir le service applicatif à appeler, appeler un port de sortie et construire le résultat.
 Il ne doit pas gérer lui-même une boucle de traitement, une pagination, une authentification, un flux temporaire, du parsing/formatage technique réutilisable, ni coordonner plusieurs appels techniques dépendants. Ces responsabilités vont dans un service applicatif ou un helper selon leur nature. chaque method de usecase doit implementer une entite qui etend de BaseModel. 
- Avant de créer une classe, identifier explicitement sa nature : entité,
  Value Object, DTO, contexte applicatif, service métier, helper ou adapter.
- Une entité représente un concept métier avec identité, cycle de vie et
  invariants ; elle est placée dans `core/domain/entity/` et utilise Pydantic. 
- Un DTO transporte des données entre composants sans identité métier ; il est
  placé dans `core/domain/dto/`, utilise Pydantic et porte le suffixe `Dto`. 
- Ne jamais placer un DTO dans `entity/`, même s’il contient des données
  métier, et ne jamais considérer un objet de contexte comme une entité. 
- Un use case orchestre l’opération métier : il ne déclare pas de DTO, contexte,
  serializer, helper ou détail technique dans son propre fichier.
- Toute logique de transformation ou sérialisation réutilisable appartient à
  un helper ou service dédié, hors du use case.
- Placer chaque nouvelle classe dans la couche correspondant à sa
  responsabilité, et non près de son premier consommateur par facilité.
- Ne jamais décrire ce que le code exprime déjà.
- Documenter uniquement une décision, un invariant, un risque ou un comportement non évident.
- Une docstring de module indique sa responsabilité en une phrase.
- Ne pas dupliquer une information entre module, classe, fonction et documentation.
- Avant d’ajouter un commentaire, vérifier que sa suppression ferait réellement perdre une information nécessaire.
- Avant d’ajouter un mapping, un catalogue de messages, un DTO de transformation
ou une politique d’erreur, rechercher le contrat standard déjà produit dans le
flux concerné et le réutiliser lorsqu’il porte la même sémantique.
- Ne créer une représentation supplémentaire que lorsqu’elle apporte une
responsabilité ou un invariant distinct, explicitement justifié. 
- Ne jamais reconstruire une erreur depuis une exception brute lorsqu’une réponse
standardisée existe déjà.
- En Python, utiliser directement les objets classes comme clés d’un registre,
  selon le principe de `Strategy::class` en PHP. 
- Préférer ce registre aux successions de `if`, `isinstance` ou `match` pour
  sélectionner une stratégie ou une fonction selon un type de configuration.
- Typer précisément les classes de configuration, stratégies et retours.
- Refuser explicitement les types non enregistrés avec une erreur claire.
- Ajouter un test vérifiant que chaque configuration supportée possède une
  stratégie ou une fonction enregistrée.
- Utiliser des noms précis exprimant l’intention métier. 
- Nommer une méthode avec un verbe décrivant son action réelle.
- Nommer une variable selon son rôle et son contenu.
- Employer le même vocabulaire dans le code, les tests et la documentation.
- Éviter les noms vagues ou ambigus hors contexte.
- Éviter les abréviations non standard.
- Préférer un nom explicite, même plus long.
- Si une méthode est difficile à nommer, vérifier qu’elle ne possède pas
  plusieurs responsabilités. 
- Une fonction ou méthode possède une responsabilité unique. 
- Une classe possède une raison principale de changer. 
- Utiliser les fonctionnalités modernes de la version du langage ciblée.
- Préserver la sûreté du typage.
- Éviter les casts forcés, types trop génériques et valeurs magiques.
- Produire des erreurs explicites, précises et actionnables.
- Ne jamais masquer silencieusement une erreur.
- Éviter les captures d’exceptions trop larges.
- Ne pas ajouter de fallback donnant l’apparence d’un succès.
- Limiter les commentaires aux décisions non évidentes.
- Ne pas modifier du code sans rapport avec le besoin. 
- Éviter les commentaires superflus qui répètent ce que le code exprime déjà.
- Commenter uniquement les décisions, contraintes ou intentions non évidentes
- Lorsqu’au moins quatre paramètres représentent un même concept, rechercher
  un objet métier ou un objet de contexte existant avant d’en créer un.
- Remplacer les valeurs métier répétées par un type, un enum ou une constante.
- Éviter les paramètres booléens qui modifient le comportement d’une fonction ;
  préférer des opérations explicitement nommées.
- Évaluer la complexité de chaque fonction, pas uniquement la moyenne.
- Viser une complexité cyclomatique inférieure ou égale à 10.
- Réduire également la complexité cognitive et l’imbrication. 
- Limiter naturellement l’imbrication à deux niveaux.
- Utiliser des retours anticipés lorsqu’ils améliorent la lecture.
- Refactorer selon les responsabilités, jamais pour tromper une métrique.
- [rework] Ne pas fragmenter artificiellement le code en micro-fonctions.
- Évaluer la complexité algorithmique selon le volume réel des données.
- [rework] Ajouter des benchmarks uniquement pour les traitements critiques.
- Ne pas considérer les conventions locales comme automatiquement correctes.
- Corriger la dette directement liée au changement lorsqu’elle empêche une
  solution propre. 
- Ne pas lancer une refonte globale sans nécessité.
- Isoler les améliorations afin de conserver un changement lisible et sûr. 
- Vérifier la nature, le nom et l’emplacement de chaque nouvelle classe avant
  son implémentation.
- Après un commentaire, rechercher le même problème dans tout le périmètre
  concerné afin de corriger la cause plutôt que l’unique ligne signalée.
- Si une suggestion dégrade le typage, l’architecture ou la lisibilité,
  expliquer pourquoi et proposer une meilleure solution.
- Préférer un fonctionnalité native au lieu de créer une méthode spécifique.
- Interdire `# mypy: ignore-errors` au niveau d'un module de production
- Interdire les suppressions de typage globales destinées à faire passer Mypy.
- Toute exception de typage doit être locale, minimale, justifiée et associée à
  un code d'erreur Mypy précis.
- Lorsqu'un mixin dépend d'une surface limitée de son hôte, définir un `Protocol`
  étroit plutôt qu'une classe fictive, `Any`, un cast large ou une désactivation
  de Mypy. 
- L'arborescence des tests unitaires doit refléter l'arborescence des modules
  testés.
- Lorsque deux modèles ont le même contrat et la même responsabilité, 
  factoriser les champs et comportements dans un modèle commun. 
- Un use case orchestre les services,mais ne compose pas lui-même plusieurs sources de données pour construire un contexte technique d'exécution. Lorsqu'un ensemble de données est préparé pour un autre service, créer un service de préparation dédié.
Une méthode privée de use case doit être remise en question lorsqu'elle récupère plusieurs dépendances, applique des transformations et construit un DTO destiné à un autre service. 
- Un use case ne lit pas directement le filesystem, ne manipule pas `Path`, ne parse pas JSON et ne connaît pas le format de stockage d'une configuration. Les données externes sont lues par un adapter derrière un port.
Ajouter un test d'architecture interdisant `pathlib`, `json`, `tempfile`, les clients HTTP et les adapters concrets dans `core/use_cases/`. 
- Toute classe qui transporte des données structurées doit être un modèle Pydantic, y compris si elle est interne et technique.
Lorsqu'un comportement varie selon un type de configuration fermé, utiliser un registre typé type de configuration -> fonction ou stratégie.
Interdire dataclass dans core/ et adapters/ avec une règle Ruff ou un test AST. Ajouter un test d'exhaustivité vérifiant que chaque type de StopConditionConfig possède un handler. 
- Une logique utilisée par un seul composant doit rester privée dans ce composant. Un module partagé est justifié seulement avec plusieurs consommateurs ou une abstraction autonome claire.
Lorsqu'un module est créé, vérifier qu'il a plusieurs consommateurs réels ou qu'il représente un concept autonome. 
- Un use case ne parse pas, ne sélectionne pas et ne sérialise pas des payloads de protocole. Une transformation technique stateless doit être extraite dans un helper explicitement nommé.
Le test d'architecture interdisant l'import json dans core/use_cases/ détecterait ce cas.
- Un nouveau use case est créé uniquement lorsqu'il représente une intention métier autonome avec son propre contrat d'entrée et de sortie. Une variante technique ou un sous-processus devient un service, un helper ou une stratégie.
- Interdire les mixins Pydantic de comportement pour découper les méthodes
  d’un même agrégat. Une classe `*Mixin` ne doit pas hériter de `BaseEntity`,
  `BaseModel` ou d’une base d’agrégat afin d’être recombinée dans une entité.
- Les agrégats, value objects, commandes métier et DTO internes transportent
  des données structurées via des modèles Pydantic explicitement typés.
- Un use case manipule des agrégats Pydantic, des commandes, des queries et des
  DTO. Il ne reçoit ni ne retourne un document de persistance
  (`dict[str, Any]`, `_id`, forme Mongo, champ historique, document brut). 
  Un port de repository retourne un agrégat, un value object ou un DTO de
  lecture typé. Interdire les signatures de ports de type `-> dict`,
  `-> list[dict]`, `document: dict[...]` ou `payload: dict[...]` pour représenter
  un objet métier ou persistant.
  Seul un adapter de persistance convertit :
  `document Mongo -> entité Pydantic`
  et
  `entité Pydantic -> document Mongo`.
- Les mappers Mongo vivent dans `adapters/output/`. Ils portent les noms,
  formats historiques, `_id`, encodages BSON, dates et index techniques. Ces
  détails ne sont pas connus de `core/domain/` ni de `core/use_cases/`. 
- Un use case ne doit jamais appeler `to_document()` ou `from_document()`.
  Il demande une entité typée au repository, applique une opération métier,
  puis sauvegarde l'entité typée. 
- Interdire les merges du type `{**entity.to_document(), **updates}` dans le
  core. Toute mise à jour passe par une méthode métier explicitement nommée,
  qui valide les invariants et les transitions associées. 
- `model_dump()` est autorisé uniquement :
  1. à une frontière d'adapter ;
  2. pour des logs structurés ;
  3. pour construire un autre modèle Pydantic immédiatement validé, lorsque
     les contrats sont distincts et qu'aucune projection typée n'est possible.
  Il ne doit pas servir à contourner une mise à jour métier typée.
-  Tout traitement auxiliaire déclaré “best effort” et exécuté après une opération métier, comme le tracking, la télémétrie ou une notification, doit être filtré avant exécution et isolé de la réponse métier. Une erreur de préparation, de validation ou de publication doit être journalisée sans faire échouer une commande déjà exécutée. Les opérations éligibles doivent avoir une source unique, et des tests doivent couvrir les opérations incluses, exclues et les défaillances du traitement secondaire.
- 