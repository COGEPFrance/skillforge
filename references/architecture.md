# Architecture et réutilisation

## Choix et cohérence globale

- Identifier le besoin et les décisions applicables dans les instructions du dépôt, briefs, documentation d’architecture et ADR. Tenir compte de leur portée et de leur statut ; une décision remplacée n’impose plus son ancienne contrainte.
- Distinguer architecture décidée, architecture observée et hypothèses. Sans documentation, analyser les faits et expliciter les limites ; ne pas imposer l’hexagonal, les microservices ou des interfaces supplémentaires par défaut.
- Donner aux composants des responsabilités cohérentes et des propriétaires identifiés pour les règles métier, données et contrats. Repérer les décisions dispersées, dupliquées ou placées dans une couche qui ne doit pas les posséder.
- Examiner cohésion, couplage, cycles et dépendances implicites. Suivre des scénarios représentatifs au-delà des imports, notamment appels distants, données partagées, configuration et initialisation.
- Préserver les détails internes aux frontières ; examiner les changements concrets qu’une évolution du besoin impose aux autres composants. Ne pas inventer des besoins futurs pour justifier des abstractions.
- Identifier le point de construction des composants et leur cycle de vie ; lorsque l’injection est retenue, la garder hors des décisions métier.
- Examiner le socle et les dépendances retenus par le brief technique avant de développer un mécanisme équivalent. Lorsqu’Arclith est retenu, utiliser ses skills spécialisés.
- Ne pas multiplier les couches, interfaces ou services sans responsabilité réelle. Garder les changements limités au besoin.

## Architecture hexagonale, si retenue

- Respecter les frontières domaine, cas d’usage, ports et adapters ; les dépendances vont vers les contrats et le domaine, jamais vers les adapters concrets.
- Le domaine ne dépend ni du transport ni du stockage. Pour Python, Pydantic y est une dépendance assumée pour les données structurées.
- Assembler et injecter les dépendances à un point identifié, hors de la logique métier. Vérifier le chemin réel, pas seulement le nom des dossiers.

## Microservices, si retenus

- Donner à chaque microservice une responsabilité métier, des données dont il est propriétaire et un déploiement indépendant. Aucun accès direct aux données internes d’un autre service.
- Examiner les dépendances de déploiement et les échanges qui contournent les contrats ou exposent les détails internes. Confier le détail des transitions de versions à la revue de compatibilité.

## Preuves attendues

Présenter l’architecture comprise, les décisions et leurs sources, les scénarios suivis, les dépendances et les contrôles de frontières disponibles. Justifier une nouvelle abstraction ou dépendance par un besoin concret. Une revue de structure ne prouve pas le comportement en exécution.

La lecture est globale, le verdict respecte le périmètre : pour un changement, distinguer ses défauts et conséquences de la dette indépendante ; pour une revue de projet, prioriser aussi les défauts existants dans le périmètre annoncé. Une préférence de style ne constitue pas un défaut. Une contradiction indispensable non résolue relève de `BLOCKED`, pas d’une architecture inventée par le reviewer.

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
