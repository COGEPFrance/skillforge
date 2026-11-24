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
2. Choisir unité pour la logique isolée, intégration pour les garanties de composants réels et contrats pour les consommateurs concernés ; ajouter crash ou charge selon les effets et objectifs. Prioriser les règles métier sans reporter les garanties critiques des adaptateurs. Prévoir la [suite métier et les jobs CI distincts](../../../references/testing.md#tests-métier-et-intégration-en-ci), ainsi que l’infrastructure et les données dédiées aux tests d’intégration.
3. Pour Python, lire les [tests unitaires](../../../references/testing.md#tests-unitaires-python) et, si nécessaire, les [contrôles d’architecture](../../../references/testing.md#contrôles-darchitecture-et-couverture). Conserver 80 % minimum et 90 % visés sur le périmètre non exclu, ou le seuil supérieur du projet ; justifier les exclusions sans écarter les modèles porteurs de validations.
4. Définir prérequis, assertions et critères de sortie de la phase de tests, placée dans l’ordre choisi sans chevauchement avec code ou documentation. Distinguer comportement absent, test invalide et environnement indisponible ; réserver explicitement les preuves encore impossibles.

## Résultat et passage de relais

Plan de tests ciblé avec scénarios, niveau, prérequis et critères de réussite.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-tests`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
