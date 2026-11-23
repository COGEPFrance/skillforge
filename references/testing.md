# Tests et preuves

- Choisir des tests qui vérifient les comportements et risques du changement, plutôt que reproduire son implémentation.
- Distinguer tests unitaires, intégration entre composants réels, contrats entre services et scénarios de crash ou de charge.
- Isoler les dépendances des tests unitaires ; utiliser une infrastructure de test adaptée pour les garanties qui dépendent d’un système réel.
- Cibler cas nominaux, erreurs et limites pertinentes, avec des assertions capables de détecter le défaut recherché.
- Exécuter les tests existants dès le développement ; ne pas attendre la phase de création de nouveaux tests.
- Conserver commandes, environnement et résultats observés ; un test non exécuté ou une dépendance absente ne vaut pas réussite.
- Les tests peuvent précéder le code. Dans ce cas, distinguer un échec attendu sur le comportement absent d’un test lui-même défectueux.

## Preuves attendues

Relier les scénarios aux comportements et risques. Pour les tests de crash et de charge, lire aussi les référentiels de résilience et de performance.

## Tests unitaires Python

Consulter ce détail pour écrire ou modifier des TU Python, pas pour imposer des
mocks aux tests d’intégration ou de contrat.

- Privilégier `unittest.mock` pour les dépendances des nouveaux TU :
  `create_autospec(..., instance=True, spec_set=True)` si une interface exploitable
  existe, `AsyncMock` seulement pour les opérations asynchrones, assertions
  `assert_awaited...` pour les attentes contractuelles. Le composant testé et les
  données Pydantic restent réels. Injecter avant de recourir à `patch`, appliqué
  là où le symbole est utilisé ; configurer seulement le scénario nécessaire.
- Ne pas créer un fake propre au scénario si un mock simple suffit. Un fake
  existant ne déclenche pas sa migration automatique : la réserver au périmètre
  où elle apporte une isolation ou une preuve utile, ou à une demande explicite.
  Préserver scénarios et garanties ; ne pas modifier la production pour convertir
  les doubles. L’interdiction historique d’un fichier `tests/test_helpers.py`
  particulier ne s’étend pas à tous les projets.
- Lire la définition d’une fixture avant réemploi, l’injecter par paramètre et
  garder un état indépendant par test (scope `function` pour les mocks, sauf
  isolation équivalente démontrée). Réglages communs dans la fixture, scénario
  dans le test. Examiner tous les usages avant de modifier une fixture partagée ;
  garder un mock local si les usages divergent.
- Partager une fixture lorsqu’un vrai réglage commun est réutilisé ; ne pas
  imposer un `conftest.py` racine ni le partage automatique dès deux fichiers.
  Suivre l’organisation du projet, sans supposer des variables ou fixtures MDM.
- Vérifier résultats, erreurs, états ou interactions qui font partie du contrat,
  sans assertions sur une méthode privée ni ordre d’appels sans exigence. Nommer
  le comportement et le contexte ; utiliser le mode asynchrone configuré par le
  projet plutôt qu’imposer un marqueur pytest particulier.
- Pour un invariant sur des champs modifiables, couvrir création et chemins de
  mise à jour valides/invalides pertinents, dont état inchangé après refus. Éviter
  les tests d’instanciation triviaux. Les TU n’appellent ni réseau réel ni
  infrastructure externe et ne dépendent pas d’attentes temporelles réelles.

## Contrôles d’architecture et couverture

Lire ce détail si une frontière critique justifie une protection automatique ou
si la couverture fait partie de la validation du projet.

Définir les sources analysées et les éventuels artefacts produits par une
préparation explicite et reproductible. Inclure les nouvelles sources de ce
périmètre, même non ajoutées à Git ; exclure caches, fichiers temporaires,
dépendances externes et résidus étrangers. Ne pas assimiler tout répertoire à un
module du projet. À sources et préparation identiques, les résultats restent
indépendants des résidus locaux.

Un test d’import, d’AST ou l’outil du projet peut protéger une frontière critique
ou la couverture d’un registre ; ne pas en ajouter pour chaque convention de
style. Ne pas bannir tout import `pathlib`/`json` ou toute dataclass par une
recherche textuelle aveugle : vérifier la responsabilité et le périmètre Python
concernés, en conservant Pydantic pour les classes de données structurées.

Les seuils et exclusions de couverture viennent de la configuration du projet.
Les objectifs historiques 80/90 % et exclusions automatiques des entités, DTO ou
du conteneur ne sont pas généralisés : ils peuvent masquer des invariants ou un
assemblage important. Tester les comportements significatifs indépendamment du
calcul de couverture et suivre l’organisation de tests établie sans migration
systématique vers `tests/units/`.
