- Distinguer une convention répétée et cohérente d’une mauvaise pratique
  isolée dans le code existant.
- Toute divergence avec l’architecture établie doit répondre à un besoin
  concret et être justifiée avant l’implémentation.
- Interdire les séparateurs décoratifs dans les tests ; utiliser des noms de tests explicites.
- Éviter tout mécanisme d’enregistrement implicite dépendant de l’ordre des
  imports.
- Tester les comportements observables plutôt que l’implémentation interne
- Toute mutation d'une entité Pydantic doit reconstruire et valider le modèle
  (`Model(...)` ou `model_validate(...)`) lorsque les champs modifiés participent
  à un invariant.
- Pour chaque invariant modifiable, tester les chemins de création et de mise à
  jour, ainsi que le refus des valeurs invalides.
-  Un test d'architecture ne doit jamais dépendre de fichiers générés localement
  (`__pycache__`, caches d'IDE, couverture, artefacts temporaires) ni de
  l'historique des changements de branche. 
- Les tests d'architecture vérifient les fichiers source versionnés ou les
  modules importables, jamais le contenu brut non filtré du système de fichiers. 
- Une PR ne doit contenir aucun fichier que le formatteur configuré modifierait,
  sauf fichier généré explicitement identifié et exclu.
- Conserver des sous-classes nommées vides uniquement si elles préservent une  
 frontière publique, métier ou OpenAPI utile. 
- Ne pas fusionner des modèles seulement similaires lorsque leurs  
 responsabilités, invariants, cycle de vie ou frontière d’entrée/sortie  
 diffèrent.
- Un agrégat métier possède une seule hiérarchie Pydantic explicite :
  l’agrégat concret hérite d’une base de champs ou de `BaseEntity`, mais ne
  compose pas plusieurs sous-classes `BaseModel` par héritage multiple.
- Les méthodes qui ne concernent qu’un seul agrégat restent dans cet agrégat.
  Elles peuvent être privées si elles ne font partie d’aucun contrat public.
  Ne pas créer un module ou un mixin pour découper visuellement une classe.
- Ne pas utiliser l’héritage multiple entre plusieurs modèles Pydantic pour
  combiner des champs, serializers, validateurs ou configurations. Regrouper
  ces éléments dans une unique base de champs ou préférer la composition. 
- Une règle domaine ne convertit pas une entité Pydantic en dictionnaire pour
  la modifier puis la reconstruire. Elle utilise une méthode métier, un value
  object, un patch Pydantic typé ou `validated_update()` lorsque l'invariant est
  revalidé. 
- Les DTO API et événements ont leurs contrats Pydantic dédiés. Un agrégat
  n'est pas un payload HTTP, RabbitMQ ou MongoDB. Les builders ou mappers de
  sortie construisent les `*Output` et événements depuis l'agrégat. 