---
name: write-contract-tests
description: "Vérifier un contrat API ou événement entre producteurs et consommateurs identifiés."
---

# write-contract-tests

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [testing](../../../references/testing.md)
- [compatibility](../../../references/compatibility.md)
- [messaging](../../../references/messaging.md)

## Exécution

1. Identifier propriétaires, versions et consommateurs couverts par le contrat.
2. Tester formes, sémantique utile, erreurs et compatibilité des combinaisons de versions pertinentes.
3. Indiquer quelles garanties proviennent de tests de contrat et lesquelles nécessitent encore une intégration réelle.

## Résultat et passage de relais

Tests de contrat et matrice des consommateurs ou versions couverts.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-tests`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
