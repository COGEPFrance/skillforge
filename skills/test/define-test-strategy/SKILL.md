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

1. Relier critères attendus et risques aux composants et contrats concernés.
2. Choisir les niveaux pertinents et les dépendances nécessaires, sans imposer toutes les catégories à chaque changement.
3. Définir cas nominaux, erreurs et limites, preuves attendues et place des tests dans le parcours choisi.

## Résultat et passage de relais

Plan de tests ciblé avec scénarios, niveau, prérequis et critères de réussite.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-tests`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
