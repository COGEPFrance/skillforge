---
name: fix-bug
description: "Corriger un défaut identifié dans un périmètre limité en conservant les preuves de sa cause."
---

# fix-bug

## Références

Même en invocation isolée, appliquer le [filtre transverse](../../../references/quality-criteria.md), puis consulter uniquement les détails pertinents ci-dessous.

- [code-quality](../../../references/code-quality.md)
- [testing](../../../references/testing.md)

## Exécution

1. Établir attendu, reproduction et cause ; distinguer fait et hypothèse quand la reproduction est incomplète.
2. Corriger le composant responsable et les occurrences de la même cause dans le périmètre. Ne pas mutualiser sur la seule ressemblance ni ajouter une abstraction sans besoin.
3. Exécuter les vérifications existantes pertinentes ; conserver le scénario qui détecte le défaut pour la phase de tests ou l’écrire d’abord selon le parcours retenu. Documenter les limites de reproduction.

## Résultat et passage de relais

Cause, correction ciblée et preuve de reproduction ou limites ; validation après correction.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-code`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
