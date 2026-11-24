---
name: integrate-service-components
description: "Assembler les composants existants d’un service et vérifier leur intégration."
---

# integrate-service-components

## Références

Commencer par la [sélection des exigences communes](../../../references/quality-criteria.md), même pour une invocation isolée, puis lire les références spécialisées ci-dessous.

- [architecture](../../../references/architecture.md)
- [configuration](../../../references/configuration.md)
- [observability](../../../references/observability.md)
- Si le brief retient Arclith : [profil et délégation](../../../references/profiles/python-arclith.md)

## Exécution

1. Vérifier les composants, contrats et revues nécessaires puis identifier les implémentations réellement à assembler.
2. Relier dépendances et configuration validée au point d’assemblage du projet, hors métier. Pour un registre, utiliser une initialisation explicite ou celle du framework ; ne pas dépendre d’effets de bord d’imports.
3. Vérifier démarrage, cycle de vie et un chemin représentatif ; si le choix d’un handler dépend d’une configuration, vérifier sa couverture et le refus explicite d’un type inconnu. Ne pas réimplémenter les composants pour les relier.

## Résultat et passage de relais

Assemblage et preuves d’intégration, dépendances externes nécessaires et limites de vérification.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-service-integration`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
