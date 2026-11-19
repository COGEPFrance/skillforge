---
name: integrate-service-components
description: "Assembler des composants existants dans un service Arclith et vérifier leur intégration."
---

# integrate-service-components

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [architecture](../../../references/architecture.md)
- [configuration](../../../references/configuration.md)
- [observability](../../../references/observability.md)
- [profiles/python-arclith](../../../references/profiles/python-arclith.md)

## Exécution

1. Vérifier que contrats et composants nécessaires sont disponibles et revus.
2. Relier ports, implémentations, configuration et points d’entrée au point d’assemblage du service.
3. Vérifier la résolution effective des dépendances, le démarrage et un chemin représentatif ; ne pas réimplémenter les composants pour les relier.

## Résultat et passage de relais

Assemblage et preuves d’intégration, dépendances externes nécessaires et limites de vérification.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-service-integration`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
