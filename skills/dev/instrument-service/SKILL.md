---
name: instrument-service
description: "Instrumenter un service avec logs, métriques et traces exploitables."
---

# instrument-service

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [observability](../../../references/observability.md)
- [performance](../../../references/performance.md)
- [security](../../../references/security.md)
- [profiles/python-arclith](../../../references/profiles/python-arclith.md)

## Exécution

1. Identifier les questions d’exploitation, transitions et mesures utiles au service.
2. Réutiliser l’instrumentation Arclith ; ajouter les signaux manquants et propager la corrélation entre appels et messages.
3. Vérifier émission et corrélation sur un succès et un échec, sans secrets ni cardinalité incontrôlée.

## Résultat et passage de relais

Signaux observés, moyens de consultation et limites de vérification.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-observability`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
