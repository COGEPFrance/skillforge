# Transitions de contrats et de versions

Les instructions opérationnelles sont dans [`implement-port`](../skills/dev/implement-port/SKILL.md), [`implement-adapter`](../skills/dev/implement-adapter/SKILL.md), [`implement-persistence`](../skills/dev/implement-persistence/SKILL.md), [`write-contract-tests`](../skills/test/write-contract-tests/SKILL.md), [`prepare-release`](../skills/delivery/prepare-release/SKILL.md), [`review-compatibility`](../skills/review/review-compatibility/SKILL.md).

Lire lors d’un changement d’API, événement, schéma persisté, configuration publique ou dépendance affectant les consommateurs.

Établir les combinaisons réellement attendues pendant le déploiement : ancien producteur/nouveau consommateur, inverse, coexistence ou rejeu d’anciens messages selon le système. Couvrir uniquement les combinaisons promises ; ne pas exiger une compatibilité perpétuelle.

Pour une rupture voulue, documenter consommateurs, migration et coordination. Vérifier les versions du socle et des dépendances retenus par le brief technique. Distinguer retour de code et données encore lisibles par l’ancienne version.

La revue énonce versions couvertes, résultats et inconnues. Les seuls composants à jour ne prouvent pas la transition.
