---
name: review-configuration
description: "Examiner les sources et consommateurs d’une configuration ajoutée ou modifiée. Produire une revue spécialisée sans corriger les fichiers."
---

# review-configuration

## Périmètre

Examiner les sources et consommateurs d’une configuration ajoutée ou modifiée. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

- [configuration](../../../references/configuration.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Tracer chaque option de sa source au consommateur avec type, défaut, priorité et validation au démarrage.
3. Vérifier valeurs invalides, exemples sans secrets et absence de paramètres dispersés ou d’invariants désactivables.
4. Utiliser les contrôles pertinents disponibles dans un environnement de test isolé et autorisé ; ne pas modifier la production ni les systèmes partagés hors du périmètre de la tâche. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
