---
name: integrate-service-components
description: "Assembler les composants existants d’un service et vérifier leur intégration."
---

# integrate-service-components

## Références

Même en invocation isolée, appliquer le [filtre transverse](../../../references/quality-criteria.md), puis consulter uniquement les détails pertinents ci-dessous.

- [architecture](../../../references/architecture.md)
- [configuration](../../../references/configuration.md)
- [observability](../../../references/observability.md)

## Exécution

1. Vérifier les contrats, composants et validations nécessaires ; identifier les implémentations et ressources à assembler.
2. Relier ports, implémentations, configuration validée et points d’entrée à un point d’assemblage identifié, hors logique métier.
3. Vérifier dépendances effectivement injectées, cycle de vie des ressources, démarrage et chemin représentatif. Ne pas réimplémenter un composant pour masquer un prérequis manquant.

## Résultat et passage de relais

Assemblage et preuves d’intégration, dépendances externes nécessaires et limites de vérification.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-service-integration`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
