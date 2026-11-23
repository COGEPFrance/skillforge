---
name: review-compatibility
description: "Examiner les transitions de versions et contrats affectés par le changement. Produire une revue spécialisée sans corriger les fichiers."
---

# review-compatibility

## Périmètre

Examiner les transitions de versions et contrats affectés par le changement. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

- [compatibility](../../../references/compatibility.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Identifier consommateurs et versions des API, événements, données et configurations modifiés.
3. Examiner coexistence, migration, rejeu et retour arrière ; signaler les combinaisons non vérifiées.
4. Utiliser les contrôles pertinents disponibles, dans un environnement de test isolé et autorisé, sans mutation de la production. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
