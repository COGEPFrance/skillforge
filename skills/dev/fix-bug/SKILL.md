---
name: fix-bug
description: "Corriger un défaut identifié dans un périmètre limité en conservant les preuves de sa cause."
---

# fix-bug

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [code-quality](../../../references/code-quality.md)
- [testing](../../../references/testing.md)

## Exécution

1. Établir comportement attendu, reproduction et cause avant correction ; séparer faits et hypothèses.
2. Corriger le composant responsable et examiner les occurrences de la même cause dans le périmètre.
3. Exécuter les tests existants pertinents et transmettre le scénario de régression à la phase de tests, ou l’écrire d’abord si le parcours le prévoit.

## Résultat et passage de relais

Cause, correction ciblée et preuve de reproduction ou limites ; validation après correction.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-code`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
