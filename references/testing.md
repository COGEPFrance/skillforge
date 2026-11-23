# Niveaux de tests et portée des preuves

Les instructions opérationnelles sont dans [stratégie](../skills/test/define-test-strategy/SKILL.md), [unité](../skills/test/write-unit-tests/SKILL.md), [intégration](../skills/test/write-integration-tests/SKILL.md), [contrats](../skills/test/write-contract-tests/SKILL.md), [crash](../skills/test/test-crash-recovery/SKILL.md), [mesures](../skills/test/measure-performance/SKILL.md) et [revue](../skills/review/review-tests/SKILL.md).

Choisir le niveau qui peut détecter le défaut visé. Des doubles sont adaptés à une logique isolée ; ils ne prouvent pas une transaction, un broker ou un protocole réel. Les tests de crash et de charge suivent respectivement les détails de [résilience](resilience.md) et de [performance](performance.md).

La revue relie scénarios, comportements et assertions, puis distingue résultats observés, dépendances absentes et tests non exécutés. Conserver commandes, environnement et résultats utiles. Les vérifications existantes pertinentes s’exécutent pendant le développement ; il n’est pas nécessaire de créer une nouvelle suite pour chaque changement.

Dans un parcours tests d’abord, un échec dû au comportement absent est attendu ; un test défectueux ou un environnement manquant ne valide pas ce scénario. La validation finale requiert le comportement implémenté et vérifié.
