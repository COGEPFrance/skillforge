---
name: review-domain-models
description: "Examiner les modèles métier et la préservation de leurs invariants. Produire une revue spécialisée sans corriger les fichiers."
---

# review-domain-models

## Périmètre

Examiner les modèles métier et la préservation de leurs invariants. Identifier les fichiers, contrats et preuves utiles ; ne pas élargir cette revue en audit général.

## Critères partagés

- [domain-models](../../../references/domain-models.md)

## Examen

1. Identifier la révision examinée et la phase demandée : préliminaire ou finale.
2. Distinguer entité, valeur, DTO et modèle externe ; examiner identité et invariants.
3. Suivre création, transitions et mutations pour repérer validations contournées ou couplage au transport et au stockage.
4. Utiliser les contrôles pertinents disponibles, sans mutation de l’environnement réel. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
