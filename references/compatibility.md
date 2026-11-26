# Compatibilité

- Identifier les consommateurs des API, événements, configurations et schémas persistés modifiés.
- Examiner les transitions entre versions, y compris coexistence de producteurs et consommateurs ou services déployés progressivement.
- Préserver les contrats requis ou expliciter la rupture, sa migration et son déploiement coordonné.
- Maîtriser les versions des dépendances ; vérifier la compatibilité avec le socle Arclith et le blueprint retenus.
- Considérer reprise, rejeu d’anciens messages et retour à une version de code précédente.

## Valeurs acceptées et validations

Appliquer ces contrôles lorsqu’un champ d’entrée ou de configuration, une
contrainte, un défaut, un validateur ou un modèle de validation change.

- Comparer les valeurs acceptées avant et après, avec un exemple de frontière
  pertinent, la conséquence d’un refus et le test qui couvre le comportement.
  Passer d’un conteneur non validé à un modèle validé peut modifier le contrat
  même si les types de champs semblent identiques.
- Selon le champ, examiner bornes inclusives/exclusives (`gt`/`ge`, `lt`/`le`),
  zéro, négatifs, absence, `None`, chaîne vide, casse, espaces et alias. Vérifier
  dans le contrat des dépendances les valeurs sentinelles, comme zéro signifiant
  désactivé ou sans limite ; ne pas déduire leur sens du seul nom du champ.
- Suivre les représentations acceptées à travers normalisation, recherche,
  comparaison, persistance et sérialisation. Une forme alternative doit conserver
  la même identité et les mêmes effets, ou être explicitement refusée.
- Pour la configuration, suivre une valeur auparavant valide dans le chargeur
  ou la factory réels, la construction du modèle, l’injection et le démarrage ou
  traitement. Distinguer erreur gérée et service qui ne peut plus démarrer.
- Une valeur supportée hors défaut fait partie du contrat. Signaler une régression
  démontrée avec sa configuration déclenchante et son effet, même sans preuve de
  son utilisation actuelle en production.

## Preuves attendues

Énoncer les versions et consommateurs couverts, les cas de transition examinés et les inconnues restantes. Une réussite avec les seules versions les plus récentes ne prouve pas une transition compatible.
