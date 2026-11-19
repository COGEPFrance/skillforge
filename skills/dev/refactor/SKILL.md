---
name: refactor
description: "Refactorer le code nécessaire au besoin courant sans modifier le comportement attendu."
---

# refactor

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [code-quality](../../../references/code-quality.md)
- [architecture](../../../references/architecture.md)
- [compatibility](../../../references/compatibility.md)

## Exécution

1. Établir pourquoi le refactoring est nécessaire au besoin courant ; sinon suivre le workflow de périmètre.
2. Identifier les comportements et contrats à préserver puis modifier uniquement les composants concernés.
3. Comparer les garanties avant et après, exécuter les vérifications existantes et signaler les impacts.

Consulter le [périmètre de refactoring](../../../workflows/refactoring-scope.md) avant de modifier le code.

## Résultat et passage de relais

Refactoring borné, comportements préservés et preuves ; dette indépendante décrite séparément.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-code`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
