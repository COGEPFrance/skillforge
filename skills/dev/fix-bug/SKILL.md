---
name: fix-bug
description: "Corriger un défaut identifié dans un périmètre limité en conservant les preuves de sa cause."
---

# fix-bug

## Références

Commencer par la [sélection des exigences communes](../../../references/quality-criteria.md), même pour une invocation isolée, puis lire les références spécialisées ci-dessous.

- [code-quality](../../../references/code-quality.md)
- [testing](../../../references/testing.md)

## Exécution

1. Établir comportement attendu, reproduction et cause ; distinguer faits et hypothèses avant correction.
2. Corriger la cause dans les composants du périmètre, y compris les occurrences révélées par une review. Challenger une suggestion qui dégrade typage, architecture ou lisibilité et proposer une correction adaptée.
3. Exécuter les vérifications existantes pertinentes ; conserver une preuve avant/après et prévoir un test de non-régression qui détecte le défaut. Transmettre le scénario à une phase de tests distincte, même si la demande inclut le correctif et sa non-régression ; ne pas annoncer la régression couverte avant exécution. Pour un défaut comportemental testable, la validation finale inclut la non-régression exécutée.

## Résultat et passage de relais

Cause, correction ciblée et preuve de reproduction ou limites ; validation après correction.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-code`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
