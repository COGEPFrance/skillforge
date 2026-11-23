---
name: refactor
description: "Refactorer le code nécessaire au besoin courant sans modifier le comportement attendu."
---

# refactor

## Références

Commencer par la [sélection des exigences communes](../../../references/quality-criteria.md), même pour une invocation isolée, puis lire les références spécialisées ci-dessous.

- [code-quality](../../../references/code-quality.md)
- [architecture](../../../references/architecture.md)
- [compatibility](../../../references/compatibility.md)

## Exécution

1. Établir le lien avec la demande ou le refactoring explicitement demandé ; consigner la dette importante indépendante selon le workflow de périmètre.
2. Préserver les contrats et invariants. Ne pas fusionner des modèles parce que leurs champs se ressemblent ; une sous-classe sans ajout peut porter une identité publique ou un schéma utile : vérifier les consommateurs avant suppression.
3. Mutualiser une fonction stateless pour un concept partagé, ou un service lorsqu’il possède des collaborateurs. Garder dans l’agrégat ses invariants et opérations métier ; ne pas créer des mixins ou micro-fonctions pour réduire une métrique.
4. Comparer comportements avant/après et exécuter les contrôles affectés. Pour des modèles Python, conserver une chaîne Pydantic unique et une mise à jour validant l’état final.

Consulter le [périmètre de refactoring](../../../workflows/refactoring-scope.md) avant de modifier le code.

## Résultat et passage de relais

Refactoring borné, comportements préservés et preuves ; dette indépendante décrite séparément.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-code`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
