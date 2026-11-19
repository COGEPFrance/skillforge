---
name: review-tests
description: "Examiner la pertinence et la fiabilité des tests et de leurs assertions. Produire une revue spécialisée sans corriger les fichiers."
---

# review-tests

## Périmètre

Examiner la pertinence et la fiabilité des tests et de leurs assertions. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

- [testing](../../../references/testing.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Relier les scénarios aux comportements, risques, erreurs et limites du changement.
3. Vérifier que les assertions détectent le défaut utile, que le composant testé reste réel et que le niveau de test prouve la garantie annoncée.
4. Utiliser les contrôles pertinents disponibles, sans mutation de l’environnement réel. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
