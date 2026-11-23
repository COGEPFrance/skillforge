---
name: implement-messaging
description: "Implémenter un échange asynchrone justifié et ses garanties applicatives."
---

# implement-messaging

## Références

Même en invocation isolée, appliquer le [filtre transverse](../../../references/quality-criteria.md), puis consulter uniquement les détails pertinents ci-dessous.

- [messaging](../../../references/messaging.md)
- [data-consistency](../../../references/data-consistency.md)
- [resilience](../../../references/resilience.md)

## Exécution

1. Justifier le recours aux messages par découplage, différé ou charge ; définir producteurs, consommateurs, contrat et intention commande ou événement.
2. Réutiliser les capacités du socle et du broker effectivement disponibles ; définir concurrence, ordre nécessaire, doublons, tentatives bornées et destination des messages invalides ou épuisés.
3. Aligner acquittements sur les effets durables. Entre écriture et publication, identifier la fenêtre de perte ou duplication et choisir une garantie adaptée ; ne pas imposer systématiquement un outbox.
4. Propager la corrélation sans secrets ; rendre visibles retard, accumulation et tentatives. Transmettre scénarios de doublon, coupure et coexistence de versions aux tests et revues concernés.

## Résultat et passage de relais

Flux implémenté, garanties et fenêtres de panne explicites.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-messaging`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
