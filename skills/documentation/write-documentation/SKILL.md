---
name: write-documentation
description: "Rédiger un document ciblé en distinguant comportement vérifié et contrat à réaliser."
---

# write-documentation

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [documentation](../../../references/documentation.md)

## Exécution

1. Définir public, tâche et emplacement du document à partir des sources propriétaires. Respecter la phase documentaire choisie ; si elle précède l’implémentation, présenter explicitement le contrat ou la conception à réaliser et réserver la vérification finale, sans coder ni écrire les tests.
2. Documenter décisions, invariants, risques et procédures non évidentes ; éviter de paraphraser le code et préférer un renvoi à une information dupliquée. Employer le même vocabulaire métier que le code et les tests.
3. Pour une option, appliquer la [vérification de configuration](../../../references/documentation.md#configuration-et-architecture) ; vérifier liens, exemples et commandes dans leur contexte, et distinguer exécuté, proposé et non vérifié.

## Résultat et passage de relais

Document ciblé, sources de vérité et vérifications réalisées.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-documentation`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
