---
name: review-tests
description: "Examiner la pertinence et la fiabilité des tests et de leurs assertions. Produire une revue spécialisée sans corriger les fichiers."
---

# review-tests

## Périmètre

Examiner la pertinence et la fiabilité des tests et de leurs assertions. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

Appliquer d’abord la [méthode commune de revue](../../../references/review-method.md)
pour cadrer le dépôt, les sources et la comparaison, même en invocation seule.

- [testing](../../../references/testing.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Relier les scénarios aux comportements, risques, erreurs et limites du changement.
3. Vérifier que les assertions détectent le défaut utile, que le composant testé reste réel et que le niveau de test prouve la garantie annoncée.
4. Utiliser les contrôles pertinents disponibles, dans un environnement de test isolé et autorisé, sans mutation de la production. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Risques comportementaux

Vérifier les [tests de non-régression et représentations acceptées](../../../references/testing.md#non-régression-et-représentations-acceptées)
pour les corrections et validations modifiées. Pour les gardes historiques,
réservations et écritures multiples, lire les [critères de cohérence durable et concurrence](../../../references/testing.md#cohérence-durable-et-concurrence) :
vérifier les chemins de création et l’état final complet des gagnants et perdants,
pas seulement les codes d’erreur ou le nombre de succès.

## Points ciblés

Pour Python, appliquer les [critères mocks et fixtures](../../../references/testing.md#tests-unitaires-python). Vérifier le composant réel, l’indépendance des doubles et les assertions d’attente asynchrones pertinentes. Les [contrôles d’architecture](../../../references/testing.md#contrôles-darchitecture-et-couverture) analysent les sources du périmètre, y compris non ajoutées à Git, sans dépendre des caches locaux. Vérifier l’absence de fakes dans les nouveaux TU et ne pas imposer une migration hors périmètre. Contrôler 80 % minimum et 90 % visés sur le périmètre non exclu, ou le seuil supérieur du projet. Vérifier la suite métier et sa couverture séparées en CI, ainsi que l’infrastructure et les jeux de données reproductibles d’intégration. Une revue préliminaire réserve les mesures qui exigent un code encore absent.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
