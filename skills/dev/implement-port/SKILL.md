---
name: implement-port
description: "Définir un contrat typé de dépendance pour un use case sans adapter concret."
---

# implement-port

## Références

Commencer par la [sélection des exigences communes](../../../references/quality-criteria.md#sélection-des-exigences-en-production), même pour une invocation isolée, puis lire les références spécialisées ci-dessous.

- [architecture](../../../references/architecture.md)
- [domain-models](../../../references/domain-models.md)

## Exécution

1. Identifier les opérations requises par le consommateur et vérifier les ports existants.
2. Définir entrées, sorties, erreurs et garanties utiles sans détails de protocole ou de stockage.
3. Placer le contrat selon les conventions du socle ; éviter une interface sans besoin ou un contrat dicté par un client technique.

## Résultat et passage de relais

Port minimal et garanties explicitement attendues de ses implémentations.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-ports`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
