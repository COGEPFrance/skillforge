---
name: implement-resilience
description: "Implémenter les protections et la reprise d’un traitement face aux défaillances et aux crashes."
---

# implement-resilience

## Références

Commencer par la [sélection des exigences communes](../../../references/quality-criteria.md), même pour une invocation isolée, puis lire les références spécialisées ci-dessous.

- [resilience](../../../references/resilience.md)
- [data-consistency](../../../references/data-consistency.md)
- [observability](../../../references/observability.md)

## Exécution

1. Identifier effets, état durable et fenêtres de panne du traitement concerné.
2. Implémenter timeouts, tentatives bornées, idempotence et points de reprise nécessaires en réutilisant les mécanismes du socle.
3. Prévoir échec définitif, rejeu maîtrisé et arrêt propre ; vérifier aussi le cas où cet arrêt ne se produit pas.

## Résultat et passage de relais

Garanties applicatives et scénarios de crash avec observations attendues.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-resilience`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
