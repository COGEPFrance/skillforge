---
name: implement-port
description: "Définir un contrat typé de dépendance pour un use case sans adapter concret."
---

# implement-port

## Références

Commencer par la [sélection des exigences communes](../../../references/quality-criteria.md), même pour une invocation isolée, puis lire les références spécialisées ci-dessous.

- [architecture](../../../references/architecture.md)
- [domain-models](../../../references/domain-models.md)

## Exécution

1. Identifier les opérations requises par le consommateur et les ports existants ; exprimer un besoin métier plutôt que la surface d’un client technique.
2. Définir entrées, sorties, erreurs et garanties typées. Un objet métier ou persistant connu ne devient pas un `dict` ou `Any` dans le contrat ; un repository retourne un agrégat, un objet valeur ou un DTO de lecture typé.
3. En Python, choisir un contrat nominal interne ou structurel selon le besoin, avec les [critères ABC / Protocol](../../../references/architecture.md#contrats-python-et-dispatch). Ne pas créer une interface ni imposer un mécanisme d’héritage sans consommateur réel.

## Résultat et passage de relais

Port minimal et garanties explicitement attendues de ses implémentations.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-ports`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
