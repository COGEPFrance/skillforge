# Socle d’un service Arclith

Les instructions opérationnelles sont dans [`scaffold-arclith-service`](../skills/dev/scaffold-arclith-service/SKILL.md), [`apply-arclith-blueprint`](../skills/dev/apply-arclith-blueprint/SKILL.md), [`review-service-foundation`](../skills/review/review-service-foundation/SKILL.md).

À utiliser seulement lorsque le brief d’architecture technique retient Arclith. Pour les autres projets, suivre le socle défini par ce brief ; ce parcours n’est pas un prérequis universel.

Suivre [l’initialisation Arclith](../workflows/service-initialization.md) : scaffold → blueprint compatible → revue du socle avant fonctionnalité. Les procédures propres à la bibliothèque sont fournies par ses skills ou sa documentation, selon les versions identifiées ; consulter le [profil](profiles/python-arclith.md).

La revue compare les fichiers produits et le blueprint, puis vérifie assemblage, configuration, démarrage et signaux de base. Un service existant se compare, il ne se régénère pas à l’aveugle. Ces preuves ne certifient pas les comportements métier, la performance, la sécurité ou la reprise du service futur.
