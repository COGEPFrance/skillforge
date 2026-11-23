---
name: implement-entity
description: "Implémenter une entité métier avec identité, invariants et transitions explicites ; utiliser Pydantic dans les projets Python."
---

# implement-entity

## Références

Même en invocation isolée, appliquer le [filtre transverse](../../../references/quality-criteria.md), puis consulter uniquement les détails pertinents ci-dessous.

- [domain-models](../../../references/domain-models.md)
- [architecture](../../../references/architecture.md)

## Exécution

1. Identifier identité, invariants, transitions et mutabilité du concept ; distinguer entité, objet valeur, DTO et contrat externe.
2. Pour les projets Python, utiliser Pydantic comme dépendance assumée du domaine ; sinon employer les types et validations du projet. Exprimer les contraintes locales par les types et les champs ; réserver les validations croisées aux invariants qui les nécessitent. Garder transport et stockage hors du modèle métier.
3. Préserver les invariants à la création et lors des mises à jour ; définir conversions acceptées et champs supplémentaires. Pour un projet Python, lire le [détail conditionnel](../../../references/domain-models.md).

## Résultat et passage de relais

Entité typée, invariants et transitions ; scénarios à vérifier lors de la phase de tests.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-domain-models`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
