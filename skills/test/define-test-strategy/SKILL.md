---
name: define-test-strategy
description: "Définir les scénarios et niveaux de tests adaptés aux comportements et risques d’un changement."
---

# define-test-strategy

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [testing](../../../references/testing.md)
- [resilience](../../../references/resilience.md)
- [compatibility](../../../references/compatibility.md)

## Exécution

1. Relier critères d’acceptation, invariants, risques et frontières modifiées aux scénarios de preuve ; éviter un inventaire systématique de tous les niveaux.
2. Choisir unité pour la logique isolée, intégration pour les garanties de composants réels et contrats pour les consommateurs concernés ; ajouter crash ou charge selon les effets et objectifs. Prioriser les comportements à risque, pas une catégorie de composants par principe.
3. Pour Python, lire les [tests unitaires](../../../references/testing.md#tests-unitaires-python) et, si nécessaire, les [contrôles d’architecture](../../../references/testing.md#contrôles-darchitecture-et-couverture). Reprendre les seuils et exclusions du projet sans exclure automatiquement entités ou DTO porteurs de validations.
4. Définir prérequis, assertions et place des tests dans le parcours code ou tests d’abord ; distinguer comportement absent, test invalide et environnement indisponible.

## Résultat et passage de relais

Plan de tests ciblé avec scénarios, niveau, prérequis et critères de réussite.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-tests`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
