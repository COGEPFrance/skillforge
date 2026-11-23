# Validation des modèles et mises à jour

Les instructions opérationnelles sont dans [`implement-entity`](../skills/dev/implement-entity/SKILL.md), [`review-domain-models`](../skills/review/review-domain-models/SKILL.md).

Pour les projets Python, utiliser Pydantic pour les entités ; sa présence dans le domaine est une dépendance assumée, avec ou sans Arclith. Pour les autres langages, appliquer les invariants avec les outils retenus par le projet.

Pour Pydantic, vérifier les garanties de la version installée pour les conversions implicites, champs supplémentaires, mutations et copies avec mise à jour. Ne pas supposer qu’une copie revalide les invariants ; justifier une construction qui contourne la validation.

`review-domain-models` suit les chemins réellement utilisés : construction, modification et transitions. Vérifier un cas invalide après mise à jour, pas seulement une instanciation nominale. L’entité métier ne sert de DTO HTTP, événement ou document persisté que si les contrats restent effectivement compatibles.
