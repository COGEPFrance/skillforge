---
name: review-configuration
description: "Examiner les sources et consommateurs d’une configuration ajoutée ou modifiée. Produire une revue spécialisée sans corriger les fichiers."
---

# review-configuration

## Périmètre

Examiner les sources et consommateurs d’une configuration ajoutée ou modifiée. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

Appliquer d’abord la [méthode commune de revue](../../../references/review-method.md)
pour cadrer le dépôt, les sources et la comparaison, même en invocation seule.

- [configuration](../../../references/configuration.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Tracer chaque option de sa source au consommateur avec type, défaut, priorité et validation au démarrage.
3. Vérifier valeurs invalides, exemples sans secrets et absence de paramètres dispersés ou d’invariants désactivables.
4. Utiliser les contrôles pertinents disponibles, dans un environnement de test isolé et autorisé, sans mutation de la production. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Cohérence du changement

Suivre déclaration, alias, chargement, défauts, injection et consommateur jusqu’aux exemples et à la documentation. Pour une suppression ou un remplacement, rechercher les anciens noms et vérifier les occurrences encore valides ; ne pas se limiter au fichier de settings.

Comparer aussi les [valeurs acceptées avant et après](../../../references/compatibility.md#valeurs-acceptées-et-validations),
notamment frontières, sentinelles et formes normalisées. Suivre une valeur
auparavant valide dans le chargeur réel jusqu’au démarrage ou au traitement.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
