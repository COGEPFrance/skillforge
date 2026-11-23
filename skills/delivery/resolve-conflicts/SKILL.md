---
name: resolve-conflicts
description: "Résoudre les conflits Git d’une intégration autorisée en préservant les comportements des branches."
---

# resolve-conflicts

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [delivery](../../../references/delivery.md)
- [compatibility](../../../references/compatibility.md)

## Exécution

1. Identifier opération autorisée, branches et intentions des changements en conflit ; vérifier l’état distant si la résolution en dépend.
2. Résoudre selon les comportements attendus sans choix mécanique d’un côté ni écrasement de modifications indépendantes.
3. Examiner le diff résultant et rejouer les validations affectées, y compris celles déjà passées avant résolution. Ne pas réécrire un historique partagé sans autorisation ; transmettre le résultat à `review-delivery` avant publication.

## Résultat et passage de relais

Conflits résolus et preuves de cohérence ; état exact de l’intégration.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-delivery`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
