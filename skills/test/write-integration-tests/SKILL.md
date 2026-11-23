---
name: write-integration-tests
description: "Vérifier la collaboration de composants réels ou leur intégration à une infrastructure de test."
---

# write-integration-tests

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [testing](../../../references/testing.md)
- [data-consistency](../../../references/data-consistency.md)

## Exécution

1. Identifier la frontière que les tests unitaires ne prouvent pas et préparer une infrastructure ou base dédiée aux tests, indépendante de la production.
2. Exercer composants et dépendances réels concernés, avec jeux de données conçus pour les scénarios, préparation reproductible et réinitialisation entre tests. Prévoir un job CI distinct de la suite métier isolée.
3. Vérifier résultats persistés et erreurs pertinentes ; ne pas prétendre valider un broker ou stockage entièrement simulé.

## Résultat et passage de relais

Scénarios reproductibles, environnement de test et résultats observés.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-tests`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
