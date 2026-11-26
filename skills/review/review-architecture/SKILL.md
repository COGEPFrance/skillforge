---
name: review-architecture
description: "Examiner les frontières hexagonales et l’autonomie des microservices modifiés. Produire une revue spécialisée sans corriger les fichiers."
---

# review-architecture

## Périmètre

Examiner les frontières hexagonales et l’autonomie des microservices modifiés. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

Appliquer d’abord la [méthode commune de revue](../../../references/review-method.md)
pour cadrer le dépôt, les sources et la comparaison, même en invocation seule.

- [architecture](../../../references/architecture.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Suivre les imports et dépendances effectifs entre domaine, ports, use cases et adapters.
3. Vérifier propriété des données, assemblage et absence de dépendance aux détails techniques dans le domaine ; justifier chaque abstraction nouvelle.
4. Utiliser les contrôles pertinents disponibles, dans un environnement de test isolé et autorisé, sans mutation de la production. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Choix du projet

Comparer au brief technique et aux frontières effectivement retenues. Pour Python, Pydantic est une dépendance assumée du domaine. Une divergence structurante doit être explicitée et validée ; ne pas reproduire une dette uniquement parce qu’elle est fréquente. Les [tests d’architecture](../../../references/testing.md#contrôles-darchitecture-et-couverture) peuvent protéger les frontières critiques sans imposer un outil particulier.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
