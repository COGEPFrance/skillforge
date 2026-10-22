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
- 