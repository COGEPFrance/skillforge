# Filtre de sécurité en production

Les instructions opérationnelles sont dans [`implement-adapter`](../skills/dev/implement-adapter/SKILL.md), [`implement-usecase`](../skills/dev/implement-usecase/SKILL.md), [`implement-configuration`](../skills/dev/implement-configuration/SKILL.md), [`instrument-service`](../skills/dev/instrument-service/SKILL.md), [`review-security`](../skills/review/review-security/SKILL.md).

À lire pendant toute implémentation, y compris isolée ; appliquer seulement les risques atteignables du changement.

- Entrée non fiable ou nouvelle frontière : valider les données et leurs conversions.
- Opération sensible : faire respecter les autorisations dans le périmètre métier concerné, y compris les refus.
- Intégration ou accès à une ressource : limiter les privilèges et vérifier l’activation des mécanismes de sécurité du socle retenu.
- Configuration, artefact ou télémétrie : protéger secrets et données sensibles.

Ce filtre ne déclenche pas un audit général. `review-security` approfondit les chemins concernés avec preuves et impact explicites ; une revue partielle ne garantit pas la sécurité globale du service.
