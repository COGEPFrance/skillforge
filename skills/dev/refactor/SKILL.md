---
name: refactor
description: "Refactorer le code nécessaire au besoin courant sans modifier le comportement attendu."
---

# refactor

## Références

Même en invocation isolée, appliquer le [filtre transverse](../../../references/quality-criteria.md), puis consulter uniquement les détails pertinents ci-dessous.

- [code-quality](../../../references/code-quality.md)
- [architecture](../../../references/architecture.md)
- [compatibility](../../../references/compatibility.md)

## Exécution

1. Établir le lien avec le besoin courant ou le refactoring explicitement demandé ; pour une dette indépendante, suivre le workflow de périmètre.
2. Identifier comportements, erreurs et contrats à préserver. Mutualiser uniquement les concepts partagés ; limiter les nouvelles abstractions à une responsabilité réelle.
3. Comparer avant et après avec les outils configurés et les tests pertinents ; examiner consommateurs et transitions si des contrats ou données persistées changent.

Consulter le [périmètre de refactoring](../../../workflows/refactoring-scope.md) avant de modifier le code.

## Résultat et passage de relais

Refactoring borné, comportements préservés et preuves ; dette indépendante décrite séparément.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-code`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
