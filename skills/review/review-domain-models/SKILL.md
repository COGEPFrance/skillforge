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
4. Utiliser les contrôles pertinents disponibles, dans un environnement de test isolé et autorisé, sans mutation de la production. Relier les constats à un emplacement et un effet ; séparer faits et hypothèses.

## Points ciblés Python

Appliquer les [critères Pydantic](../../../references/domain-models.md#python--pydantic) : chaque champ déclaré utilise `Field` avec `description` explicite et `examples` représentatifs, synthétiques et sans données sensibles ; vérifier les métadonnées héritées sans exiger une redéclaration. Contrôler aussi les contraintes locales déclaratives, invariants croisés, état inchangé après mise à jour refusée, absence de contournement par copie ou dictionnaire, chaîne d’héritage unique. Vérifier la responsabilité de chaque modèle avant une mutualisation ; un nom ou des champs similaires ne prouvent pas un contrat commun.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
