---
name: implement-persistence
description: "Implémenter la persistance derrière un port en préservant les invariants et la cohérence."
---

# implement-persistence

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [data-consistency](../../../references/data-consistency.md)
- [architecture](../../../references/architecture.md)
- [compatibility](../../../references/compatibility.md)

## Exécution

1. Identifier agrégat ou données possédées, port et frontières transactionnelles.
2. Implémenter stockage, conversions et concurrence dans l’adapter ; garder le domaine indépendant du schéma technique.
3. Préparer migrations et reprise nécessaires, sans les exécuter sur un environnement non autorisé.

## Résultat et passage de relais

Persistance typée, cohérence et concurrence définies ; migrations et scénarios de panne concernés.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-data-consistency`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
