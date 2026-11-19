---
name: implement-entity
description: "Implémenter une entité métier Pydantic avec identité, invariants et transitions explicites."
---

# implement-entity

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [domain-models](../../../references/domain-models.md)
- [architecture](../../../references/architecture.md)
- [profiles/python-arclith](../../../references/profiles/python-arclith.md)

## Exécution

1. Identifier le concept métier et distinguer entité, objet valeur et DTO. Réutiliser les types pertinents existants.
2. Exprimer champs et invariants dans le modèle, puis les opérations métier qui les préservent.
3. Vérifier les chemins de création et de modification, sans exposer de format HTTP ou de stockage dans le domaine.

## Résultat et passage de relais

Entité typée, invariants et transitions ; scénarios à vérifier lors de la phase de tests.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-domain-models`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
