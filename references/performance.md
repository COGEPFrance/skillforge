# Charge et limites mesurées

Les instructions opérationnelles sont dans [`measure-performance`](../skills/test/measure-performance/SKILL.md), [`review-performance`](../skills/review/review-performance/SKILL.md).

Lire pour un objectif de performance, une évolution de charge ou un risque concret sur un chemin critique.

En revue, cibler complexité, accès aux données, appels distants, lots et concurrence dans la charge attendue ; ne pas demander un benchmark pour toute modification. Observer saturation, coût des signaux et goulots des dépendances lorsque ces facteurs sont pertinents.

Distinguer latence individuelle, débit global et accumulation. L’asynchronisme ne garantit pas un gain. Une mesure conserve scénario, données, environnement, versions et résultats comparables. Sans objectif, autoriser une exploration en explicitant qu’elle ne certifie ni objectif ni scalabilité.
