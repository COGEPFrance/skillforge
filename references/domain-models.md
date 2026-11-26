# Modèles et invariants

- Pour les projets Python, utiliser Pydantic pour les classes de données structurées et distinguer identité métier, objets valeur, DTO, commandes et configuration.
- Définir identité, invariants, transitions autorisées et règles de mutabilité avant d’implémenter une entité.
- Exprimer les contraintes locales par les types et contraintes de champs ; réserver les validations plus larges aux règles qui les nécessitent.
- Préciser conversions acceptées, champs supplémentaires et comportement des mises à jour ; une entité doit rester valide pendant tout son cycle de vie.
- Ne pas réutiliser automatiquement une entité comme contrat HTTP, événement ou document de persistance.
- Justifier toute construction contournant la validation. Pour Pydantic, vérifier les garanties de la version retenue ; ne pas présumer qu’une copie avec mise à jour revalide les invariants.

## Règles métier avant mécanismes

Partir des sources des règles métier, des états permis et des transitions, puis
examiner les mécanismes qui les protègent. Une validation de champs correcte ne
prouve pas qu’une transition est autorisée. Inversement, ne pas inventer de règle
métier pour combler un silence documentaire : distinguer faits, hypothèses et
décision indispensable à faire préciser. Vérifier les chemins publics réellement
utilisés et les consommateurs avant de conclure sur un contournement possible.

## Preuves attendues

Identifier les cas valides, invalides et les transitions à vérifier, y compris après modification. Une simple instanciation nominale ne démontre pas la préservation des invariants.

## Python / Pydantic

Consulter ces critères lors de la création, mutualisation ou mise à jour d’un
modèle Python. Les classes de données structurées métier, internes et techniques
utilisent Pydantic explicitement typé ; cela n’impose pas de transformer tout
algorithme, collection dynamique ou objet de comportement en modèle.

- Séparer entité (identité, cycle de vie, invariants), valeur, agrégat, DTO,
  commande, query et contexte. Les placer et les nommer selon leur responsabilité
  et les conventions du projet, sans imposer de chemin ni de suffixe commun.
- Déclarer chaque champ Pydantic avec `Field`, même sans contrainte additionnelle,
  et renseigner une `description` explicite ainsi que des `examples` représentatifs,
  synthétiques et sans données sensibles. Les champs hérités conservent les
  métadonnées de leur base ; ne pas les redéclarer sans besoin.
- Exprimer les contraintes locales déclaratives par les types et les paramètres
  de `Field`. Employer un `field_validator` pour une transformation/validation
  locale non exprimable ainsi ; un `model_validator` pour un invariant réellement
  croisé. Ne pas dupliquer une contrainte locale dans un validateur de modèle.
- Une mise à jour métier nommée contrôle champs autorisés et transitions, valide
  tout l’état final avant remplacement et laisse l’ancien état intact en cas
  d’échec. Pour plusieurs champs interdépendants, construire un nouvel état validé
  plutôt que muter successivement l’objet. Vérifier la version et les chemins
  réels : copie avec `update`, validation d’une instance déjà construite ou API
  contournant la validation ne sont pas des preuves de revalidation.
- Garder une chaîne d’héritage Pydantic unique. Ne pas recombiner des bases
  `BaseModel`/entité par des mixins de champs, validateurs, sérialiseurs ou
  configuration. Une base de champs partagés doit porter un contrat cohérent et
  réellement partagé ; ne pas l’extraire pour la seule ressemblance. La nommer
  selon sa responsabilité et les conventions du projet.
- Garder les opérations qui protègent les invariants dans l’agrégat et leurs
  détails privés. Ne pas extraire un mixin pour réduire sa taille. Avant de
  supprimer une sous-classe sans ajout, vérifier identité métier, contrats
  publics, consommateurs et schémas générés.
- Réserver la conversion des documents de stockage aux adapters concernés.
  `model_dump()` n’est pas une API de mise à jour métier : ni merge de documents
  bruts dans le core ni exposition automatique d’un agrégat entier. Préférer une
  projection typée ; un passage entre contrats distincts doit reconstruire et
  valider le modèle cible. Dans les logs, ne sélectionner que les champs utiles
  et non sensibles, sans sérialisation complète par défaut.
