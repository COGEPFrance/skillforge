---
name: review-performance
description: "Examiner les objectifs et preuves de performance du changement. Produire une revue spécialisée sans corriger les fichiers."
---

# review-performance

## Périmètre

Examiner les objectifs et preuves de performance du changement. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

- [performance](../../../references/performance.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Comparer charge, environnement, résultats et référence ; examiner saturation et dépendances.
3. Distinguer gain mesuré, risque de complexité et hypothèse ; ne pas certifier un objectif absent ou non mesuré.
4. Utiliser les contrôles pertinents disponibles, dans un environnement de test isolé et autorisé, sans mutation de la production. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
