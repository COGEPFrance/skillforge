---
name: implement-usecase
description: "Implémenter une intention applicative à partir des entités et des ports disponibles."
---

# implement-usecase

## Références

Même en invocation isolée, appliquer le [filtre transverse](../../../references/quality-criteria.md), puis consulter uniquement les détails pertinents ci-dessous.

- [architecture](../../../references/architecture.md)
- [domain-models](../../../references/domain-models.md)
- [code-quality](../../../references/code-quality.md)

## Exécution

1. Vérifier intention, critères de réussite, modèles et ports disponibles. Une règle métier indéterminée demande une précision ; ne pas inventer sa valeur.
2. Orchestrer au travers des ports ; garder les invariants dans les modèles et les autorisations au niveau où le périmètre métier est connu. Ne pas accéder directement au réseau, au stockage ou aux sources brutes de configuration.
3. Définir résultat et erreurs sans faux succès. Si plusieurs effets peuvent réussir séparément, préciser les états partiels et la reprise attendue ; transmettre ces fenêtres à la revue de cohérence.

## Résultat et passage de relais

Use case typé, dépendances et effets attendus, limites de cohérence identifiées.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-usecases`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
