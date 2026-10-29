- Comparer les pratiques existantes aux règles.
- Ne pas propager une mauvaise architecture dans du nouveau code. 
- Vérifier les responsabilités et la direction des dépendances.
- Rechercher les noms ambigus.
- Rechercher duplication, couplage et abstractions inutiles. 
- Vérifier le typage et la gestion des erreurs. 
- Examiner la complexité fonction par fonction. 
- Vérifier les cas limites et les risques de performance. 
- Exécuter les outils existants du projet : tests, lint, type-check,
  sécurité et quality gate. 
- Vérifier le résultat réel, pas seulement le succès des commandes. 
- Vérifier que chaque nouveau contrat, abstraction ou mécanisme suit les
  conventions architecturales valides par les regles. 
- Vérifier qu’aucun use case ne contient un DTO, helper ou détail technique
  devant appartenir à un composant dédié. 
- Toute contrainte portant sur un seul champ doit être déclarée dans son type ou
  dans `Field` : `pattern`, `min_length`, bornes numériques, enum, UUID, SIRET,
  e-mail, téléphone, normalisation déclarative, etc. 
- Réserver `field_validator` aux transformations qui ne peuvent pas être
  exprimées par le type ou `Field`. 
- Réserver `model_validator` aux invariants qui portent réellement sur plusieurs
  champs ou sous-objets. 
- Ne pas recopier dans un `model_validator` une validation locale déjà exprimable
  par Pydantic. 
- Ne jamais remplacer mécaniquement `dataclasses.replace()` par
  `model_copy(update=...)` sur une entité qui porte des invariants :
  `model_copy()` ne revalide pas les données mises à jour. 
- Interdire `# mypy: ignore-errors` au niveau d'un module de production
- Interdire les suppressions de typage globales destinées à faire passer Mypy.
- Toute modification Python doit satisfaire `ruff format --check` sur les
  fichiers touchés. 
- La CI ou la cible `make lint` doit exécuter `ruff format --check` en plus de
  `ruff check`. 
-  Une classe de champs Pydantic partagée est autorisée seulement si :
  1. elle a au moins deux consommateurs réels ;
  2. elle représente un contrat autonome et nommé avec le suffixe `*Fields` ;
  3. elle porte des champs, contraintes ou validateurs communs ;
  4. chaque modèle concret n’hérite que d’une seule base Pydantic de champs. 
- Ne pas nommer `*Mixin` une base de champs Pydantic. Utiliser `*Fields`,
  `*Base` ou un nom métier précis selon sa responsabilité
- Avant de créer un `Mixin`, l’agent doit indiquer :
  1. ses consommateurs réels ;
  2. le contrat qu’il apporte ;
  3. pourquoi une méthode privée, un helper, un service ou une base `*Fields`
     ne répond pas au besoin plus simplement.
  En l’absence de réponse démontrable, le mixin est interdit.
- 