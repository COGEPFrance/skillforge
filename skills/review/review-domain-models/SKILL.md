---
name: review-domain-models
description: "Examiner les états et transitions des modèles métier avant leurs mécanismes de validation, et vérifier la préservation des invariants. Produire une revue sans corriger les fichiers."
---

# review-domain-models

## Périmètre

Examiner les états et transitions des modèles métier avant leurs mécanismes de validation, et vérifier la préservation des invariants.

## Critères partagés

- [domain-models](../../../references/domain-models.md)

## Cadrage du contrat

Identifier le besoin, les consommateurs et les sources applicables : instructions,
brief, documentation des contrats, décisions et usages existants. Distinguer
promesses explicites, comportement observé et hypothèses ; une implémentation
existante ne suffit pas à définir le comportement attendu.

Préciser révision, phase et périmètre : changement ou projet. Pour un changement,
lire les dépendances utiles mais séparer la dette indépendante des défauts qui
bloquent ce changement ; pour une revue globale, inclure les défauts existants
du périmètre annoncé. L’absence de documentation ne bloque pas automatiquement.
Une décision indispensable non déterminable produit `BLOCKED`, avec le besoin
d’arbitrage ; un défaut démontré produit `FAIL`. Ne pas créer une couche ou un
composant pour satisfaire le parcours.

## Examen

1. Reconstituer identité, états autorisés, invariants et transitions à partir des règles métier applicables ; distinguer entité, valeur, agrégat, DTO et modèle externe.
2. Suivre création, transitions, mutations et reconstructions utilisées par les consommateurs. Vérifier les refus attendus, l’absence d’état partiellement modifié après échec et les chemins contournant la validation.
3. Vérifier où sont protégées les règles : un modèle structurellement valide peut accepter une transition métier interdite. Ne pas inventer une règle métier absente.
4. Examiner ensuite les mécanismes de la technologie retenue, les conversions aux frontières et les métadonnées exigées. Respecter les décisions Python/Pydantic du catalogue.
5. Exercer les cas valides, invalides et transitions pertinents dans un environnement isolé et autorisé ; limiter les garanties aux chemins réellement examinés.

## Points ciblés Python

Appliquer les [critères Pydantic](../../../references/domain-models.md#python--pydantic) : chaque champ déclaré utilise `Field` avec `description` explicite et `examples` représentatifs, synthétiques et sans données sensibles ; vérifier les métadonnées héritées sans exiger une redéclaration. Contrôler aussi les contraintes locales déclaratives, invariants croisés, état inchangé après mise à jour refusée, absence de contournement par copie ou dictionnaire, chaîne d’héritage unique. Vérifier la responsabilité de chaque modèle avant une mutualisation ; un nom ou des champs similaires ne prouvent pas un contrat commun.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Préciser les sources du contrat et distinguer faits et hypothèses. Pour chaque défaut, donner la promesse violée, le scénario, l’emplacement, la preuve, l’effet et le principe de correction ; séparer dette indépendante et suggestions.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
