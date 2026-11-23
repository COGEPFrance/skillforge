# Modèles et invariants

- Utiliser Pydantic pour les entités et distinguer identité métier, objets valeur, DTO, commandes et configuration.
- Définir identité, invariants, transitions autorisées et règles de mutabilité avant d’implémenter une entité.
- Exprimer les contraintes locales par les types et contraintes de champs ; réserver les validations plus larges aux règles qui les nécessitent.
- Préciser conversions acceptées, champs supplémentaires et comportement des mises à jour ; une entité doit rester valide pendant tout son cycle de vie.
- Ne pas réutiliser automatiquement une entité comme contrat HTTP, événement ou document de persistance.
- Justifier toute construction contournant la validation. Pour Pydantic, vérifier les garanties de la version retenue ; ne pas présumer qu’une copie avec mise à jour revalide les invariants.

## Preuves attendues

Identifier les cas valides, invalides et les transitions à vérifier, y compris après modification. Une simple instanciation nominale ne démontre pas la préservation des invariants.
