# Architecture et réutilisation

- Respecter les frontières domaine, cas d’usage, ports et adapters ; les dépendances vont vers les contrats et le domaine, jamais vers les adapters concrets.
- Le domaine ne dépend ni du transport ni du stockage. Pydantic y est une dépendance assumée pour les entités.
- Assembler et injecter les dépendances à un point identifié, hors de la logique métier.
- Arclith est le socle : examiner ses capacités et les dépendances retenues avant de développer un mécanisme équivalent.
- Donner à chaque microservice une responsabilité métier, des données dont il est propriétaire et un déploiement indépendant. Aucun accès direct aux données internes d’un autre service.
- Ne pas multiplier les couches, interfaces ou services sans responsabilité réelle. Garder les changements limités au besoin.

## Preuves attendues

Présenter les dépendances des composants modifiés, les ports utilisés et les contrôles de frontières disponibles. Justifier une nouvelle abstraction ou dépendance par un besoin concret. Une revue de structure ne prouve pas le comportement en exécution.
