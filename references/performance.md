# Performance et scalabilité

- Définir les volumes et objectifs attendus : latence, débit, ressources et délais de traitement selon le besoin.
- Examiner complexité algorithmique, accès aux données, appels distants, tailles de lots et bornes de concurrence selon la charge réelle.
- Mesurer les chemins critiques avant de conclure à un gain ; conserver scénario, jeu de données, environnement, versions et résultats.
- Distinguer latence individuelle, débit global et accumulation de travail. L’asynchronisme ne prouve pas à lui seul une amélioration.
- Examiner saturation, limites et coût d’observabilité ; éviter de déplacer un goulot vers une dépendance.

## Preuves attendues

Comparer aux objectifs et, si disponible, à une référence dans des conditions comparables. Sans objectif ou mesure suffisante, décrire ce qui reste à établir au lieu de certifier la scalabilité.
