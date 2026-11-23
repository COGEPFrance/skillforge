---
name: instrument-service
description: "Instrumenter un service avec logs, métriques et traces exploitables."
---

# instrument-service

## Références

Même en invocation isolée, appliquer le [filtre transverse](../../../references/quality-criteria.md), puis consulter uniquement les détails pertinents ci-dessous.

- [observability](../../../references/observability.md)
- [performance](../../../references/performance.md)
- [security](../../../references/security.md)

## Exécution

1. Partir des questions d’exploitation du changement ; choisir les logs, métriques ou traces utiles sans imposer les trois à chaque composant.
2. Réutiliser l’instrumentation du socle retenu ; propager la corrélation entre appels, messages et reprises. Rendre visibles erreurs, tentatives, abandons et traitements bloqués concernés.
3. Choisir latence, débit, ressources, accumulation ou délai selon le besoin ; éviter les identifiants non bornés en labels et les secrets dans tous les signaux.
4. Vérifier émission, corrélation et accès aux signaux sur un succès et un échec. Un collecteur indisponible limite la preuve ; la déclaration d’un exporteur ne valide pas la chaîne.

## Résultat et passage de relais

Signaux observés, moyens de consultation et limites de vérification.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-observability`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
