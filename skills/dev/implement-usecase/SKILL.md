---
name: implement-usecase
description: "Implémenter une intention applicative à partir des entités et des ports disponibles."
---

# implement-usecase

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [architecture](../../../references/architecture.md)
- [domain-models](../../../references/domain-models.md)
- [code-quality](../../../references/code-quality.md)

## Exécution

1. Vérifier les modèles, ports et critères de réussite ; ne pas inventer silencieusement un prérequis manquant.
2. Orchestrer les opérations nécessaires au travers des ports, en gardant les invariants métier au bon niveau.
3. Définir résultat et erreurs ; éviter accès direct au réseau, au stockage ou à la configuration brute.

## Résultat et passage de relais

Use case typé, dépendances et effets attendus, limites de cohérence identifiées.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-usecases`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
