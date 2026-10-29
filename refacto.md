- Lorsqu’un comportement est utilisé par plusieurs agrégats :
  - extraire une fonction métier stateless dans un helper explicite ;
  - extraire un service métier si le comportement dépend de collaborateurs ;
  - utiliser une base `ABC` interne uniquement si une famille fermée
    d’implémentations partage un contrat réel.
- 