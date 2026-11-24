---
name: implement-messaging
description: "Implémenter un échange asynchrone justifié et ses garanties applicatives."
---

# implement-messaging

## Références

Commencer par la [sélection des exigences communes](../../../references/quality-criteria.md), même pour une invocation isolée, puis lire les références spécialisées ci-dessous.

- [messaging](../../../references/messaging.md)
- [data-consistency](../../../references/data-consistency.md)
- [resilience](../../../references/resilience.md)
- Si le brief retient Arclith : [profil et délégation](../../../references/profiles/python-arclith.md)

## Exécution

1. Définir bénéfice, contrat, producteur, consommateur et effets attendus.
2. Réutiliser le socle et intégrer publication, consommation, acquittement et erreurs au bon niveau.
3. Traiter doublons, ordre utile, retries et cohérence des effets ; identifier les scénarios de coupure à transmettre aux tests.

## Résultat et passage de relais

Flux implémenté, garanties et fenêtres de panne explicites.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-messaging`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
