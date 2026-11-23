- Lorsqu’un comportement est utilisé par plusieurs agrégats :
  - extraire une fonction métier stateless dans un helper explicite ;
  - extraire un service métier si le comportement dépend de collaborateurs ;
  - utiliser une base `ABC` interne uniquement si une famille fermée
    d’implémentations partage un contrat réel.
- Conserver une sous-classe sans ajout de comportement ou de données uniquement
  si son identité distincte préserve un contrat public, une distinction métier
  effectivement utilisée ou un schéma d'API pertinent. Avant de la supprimer ou
  de la remplacer par un alias, vérifier les impacts sur ses consommateurs et
  les schémas générés.
- Ne pas fusionner des modèles sur la seule base de champs similaires. Préserver
  des modèles distincts lorsque leurs responsabilités, contraintes de validité,
  cycles de vie ou contrats d'entrée/sortie diffèrent. Mutualiser uniquement les
  éléments dont la sémantique et les contraintes sont communes.
- Conserver dans l'agrégat les comportements qui relèvent de sa responsabilité
  métier et protègent ses invariants. Garder non publiques les méthodes servant
  uniquement à leur implémentation. Extraire une responsabilité distincte
  lorsqu'elle le justifie, mais ne pas créer de module ou de mixin uniquement pour
  réduire la taille apparente de la classe.