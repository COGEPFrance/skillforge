---
name: review-service-integration
description: "Examiner l’assemblage et le chemin d’exécution des composants d’un service. Produire une revue spécialisée sans corriger les fichiers."
---

# review-service-integration

## Périmètre

Examiner l’assemblage et le chemin d’exécution des composants d’un service. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

- [architecture](../../../references/architecture.md)
- [configuration](../../../references/configuration.md)
- [observability](../../../references/observability.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Vérifier les implémentations effectivement injectées, leur configuration et leur cycle de vie.
3. Exercer un chemin représentatif avec les dépendances disponibles ; ne pas conclure sur la seule présence des composants.
4. Utiliser les contrôles pertinents disponibles dans un environnement de test isolé et autorisé ; ne pas modifier la production ni les systèmes partagés hors du périmètre de la tâche. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
