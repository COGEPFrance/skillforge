---
name: review-delivery
description: "Examiner le contenu et les prérequis d’un commit, d’une PR, d’une release ou d’un déploiement. Produire une revue spécialisée sans corriger les fichiers."
---

# review-delivery

## Périmètre

Examiner le contenu et les prérequis d’un commit, d’une PR, d’une release ou d’un déploiement. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

- [delivery](../../../references/delivery.md)
- [compatibility](../../../references/compatibility.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Identifier le type de livraison, la révision exacte, le périmètre et les validations préalables requises.
3. Examiner le contenu exact préparé et les conventions du dépôt ; ajouter version, notes, configuration, migrations, ordre et reprise seulement selon cet artefact. Vérifier les validations applicables et l’état distant si nécessaire ; ne pas publier pendant la revue.
4. Utiliser les contrôles pertinents disponibles dans un environnement de test isolé et autorisé ; ne pas modifier la production ni les systèmes partagés hors du périmètre de la tâche. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
