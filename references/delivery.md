# Préparation et publication

Les instructions opérationnelles sont dans [`prepare-commits`](../skills/delivery/prepare-commits/SKILL.md), [`prepare-pull-request`](../skills/delivery/prepare-pull-request/SKILL.md), [`prepare-release`](../skills/delivery/prepare-release/SKILL.md), [`prepare-deployment`](../skills/delivery/prepare-deployment/SKILL.md), [`resolve-conflicts`](../skills/delivery/resolve-conflicts/SKILL.md), [`review-delivery`](../skills/review/review-delivery/SKILL.md).

Consulter les contrôles correspondant à l’artefact préparé, sans imposer une release ou un déploiement à chaque tâche.

Pour la revue : contenu exact, révision ou état de travail, validations applicables et limites. Pour une release ou un déploiement : ajouter versions, migrations, prérequis, ordre et reprise nécessaires. Vérifier l’état distant avant une action qui en dépend.

Les skills préparent l’artefact avant `review-delivery`. Publication après `PASS` sur le contenu concerné et autorisation effective ; un verdict n’accorde aucune permission supplémentaire. Une modification après revue invalide les vérifications affectées. Suivre les conventions du dépôt, sans stratégie de branches imposée par Skillforge.
