# Architecture et réutilisation

- Respecter les frontières domaine, cas d’usage, ports et adapters ; les dépendances vont vers les contrats et le domaine, jamais vers les adapters concrets.
- Le domaine ne dépend ni du transport ni du stockage. Pour Python, Pydantic y est une dépendance assumée pour les données structurées.
- Assembler et injecter les dépendances à un point identifié, hors de la logique métier.
- Examiner le socle et les dépendances retenus par le brief technique avant de développer un mécanisme équivalent. Lorsqu’Arclith est retenu, utiliser ses skills spécialisés.
- Donner à chaque microservice une responsabilité métier, des données dont il est propriétaire et un déploiement indépendant. Aucun accès direct aux données internes d’un autre service.
- Ne pas multiplier les couches, interfaces ou services sans responsabilité réelle. Garder les changements limités au besoin.

## Preuves attendues

Présenter les dépendances des composants modifiés, les ports utilisés et les contrôles de frontières disponibles. Justifier une nouvelle abstraction ou dépendance par un besoin concret. Une revue de structure ne prouve pas le comportement en exécution.

## Contrats et erreurs existants

Avant d’ajouter un mapping, un catalogue de messages, un DTO de transformation
ou une politique d’erreur, rechercher le contrat déjà produit dans le flux
concerné. Le réutiliser lorsque sa sémantique et ses garanties correspondent au
besoin. Une autre représentation doit porter une responsabilité ou un invariant
distinct explicite ; une ressemblance de champs ne suffit pas à les fusionner.

Lorsqu’une réponse d’erreur normalisée existe dans ce flux, préserver ses
informations et garanties plutôt que reconstruire une erreur depuis l’exception
brute. Vérifier ce contrat aux frontières entre use case, port et adapter.

## Contrats Python et dispatch

Consulter ce détail pour créer un contrat, un mixin non-Pydantic ou une famille
de stratégies ; il n’impose pas ces mécanismes aux composants simples.

- Utiliser une `ABC` pour un contrat nominal partagé par des implémentations
  internes qui en héritent explicitement ; un `Protocol` pour un besoin réel de
  typage structurel ou une surface d’hôte étroite. Ne pas créer une classe
  fictive, un `Any` ou un cast large pour faire passer le type checker.
- Un mixin non-Pydantic doit avoir un contrat et des consommateurs identifiés,
  avec un avantage sur une méthode privée, une fonction ou un service. Le nombre
  de consommateurs n’est pas à lui seul une justification. Les modèles Pydantic
  suivent les [contraintes propres aux modèles](domain-models.md#python--pydantic).
- Pour un ensemble petit et fermé, préférer un dispatch exhaustif simple et
  vérifiable. Un registre typé convient aux stratégies extensibles ou enregistrées
  séparément ; utiliser une clé stable et non ambiguë (classe si l’identité de
  type est la clé du contrat, discriminant explicite sinon). Pas de clé classe
  imposée à tous les registres.
- Initialiser explicitement ou par le mécanisme documenté du socle, sans dépendre
  d’un ordre d’import implicite. Refuser les types inconnus et tester qu’un handler
  existe pour chaque configuration supportée.
