---
name: write-unit-tests
description: "Écrire des tests unitaires des comportements d’un composant isolé."
---

# write-unit-tests

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [testing](../../../references/testing.md)

## Exécution

1. Identifier comportement public et scénarios utiles, en consultant les tests existants.
2. Isoler les dépendances du composant sans simuler la logique testée ; utiliser des assertions sur les effets pertinents.
3. Exécuter les tests et démontrer qu’ils détectent le comportement incorrect, sans dépendance réelle à une infrastructure externe.

## Résultat et passage de relais

Tests unitaires, commande et résultats ; comportements couverts et limites.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-tests`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
