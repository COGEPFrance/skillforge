---
name: review-adapters
description: "Examiner la conformité d’un adapter à son port et ses conversions techniques. Produire une revue spécialisée sans corriger les fichiers."
---

# review-adapters

## Périmètre

Examiner la conformité d’un adapter à son port et ses conversions techniques. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

- [architecture](../../../references/architecture.md)
- [compatibility](../../../references/compatibility.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Comparer opérations, résultats et erreurs réels aux garanties du port.
3. Vérifier conversions, frontière technique et traitement des défaillances, sans déplacer la décision métier dans l’adapter.
4. Utiliser les contrôles pertinents disponibles, dans un environnement de test isolé et autorisé, sans mutation de la production. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
