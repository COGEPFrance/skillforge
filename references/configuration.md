# Variations et sources de configuration

Les instructions opérationnelles sont dans [`implement-configuration`](../skills/dev/implement-configuration/SKILL.md), [`review-configuration`](../skills/review/review-configuration/SKILL.md).

Lire lors de l’ajout d’une option, d’une source ou d’un consommateur de configuration.

Choisir les variations utiles : environnement, déploiement, limites ou délais dont l’exploitation a besoin. Le format appartient au projet ; YAML n’est pas une obligation. Ne pas créer une option pour chaque constante ni pour désactiver un invariant métier.

La revue suit une option de la source au consommateur : type, défaut, priorité, validation et valeur effective après surcharge. Vérifier un cas invalide, l’absence de lecture brute dispersée et la cohérence des exemples sans secrets.
