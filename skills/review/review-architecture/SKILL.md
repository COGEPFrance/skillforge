---
name: review-architecture
description: "Examiner les frontières hexagonales et l’autonomie des microservices modifiés. Produire une revue spécialisée sans corriger les fichiers."
---

# review-architecture

## Périmètre

Examiner les frontières hexagonales et l’autonomie des microservices modifiés. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

- [architecture](../../../references/architecture.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Comparer les dépendances effectives au brief technique. Pour une architecture hexagonale, suivre domaine, ports, use cases et adapters sans fuite vers les implémentations concrètes.
3. Vérifier propriété des données, assemblage et absence de dépendance aux détails techniques dans le domaine ; justifier chaque abstraction nouvelle.
4. Utiliser les contrôles pertinents disponibles dans un environnement de test isolé et autorisé ; ne pas modifier la production ni les systèmes partagés hors du périmètre de la tâche. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
