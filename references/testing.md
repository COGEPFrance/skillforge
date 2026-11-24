# Tests et preuves

- Choisir des tests qui vérifient les comportements et risques du changement, plutôt que reproduire son implémentation.
- Distinguer tests unitaires, intégration entre composants réels, contrats entre services et scénarios de crash ou de charge.
- Isoler les dépendances des tests unitaires ; utiliser une infrastructure de test adaptée pour les garanties qui dépendent d’un système réel.
- Cibler cas nominaux, erreurs et limites pertinentes, avec des assertions capables de détecter le défaut recherché.
- Exécuter les tests existants dès le développement ; ne pas attendre la phase de création de nouveaux tests.
- Conserver commandes, environnement et résultats observés ; un test non exécuté ou une dépendance absente ne vaut pas réussite.
- Écrire ou adapter les tests uniquement pendant la phase de tests enregistrée. Elle peut précéder ou suivre code et documentation ; ne pas modifier ces artefacts en même temps. Distinguer un échec attendu sur le comportement absent d’un test défectueux. Si la production doit changer, suspendre la phase et appliquer la [boucle de correction](../workflows/correction-loop.md).

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
- Pour les nouveaux TU, utiliser des mocks pour les dépendances simulées :
  ne pas créer de fakes ni réutiliser ceux d’un helper existant. Les infrastructures
  réelles et leurs jeux de données dédiés appartiennent au niveau d’intégration décrit
  ci-dessous ; ils ne remplacent pas cette isolation. Un fake déjà présent hors
  du périmètre modifié ne déclenche pas une migration générale. Lors de sa
  conversion dans les TU concernés, préserver scénarios et garanties sans
  modifier la production pour adapter le double.
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

## Tests métier et intégration en CI

Isoler les règles métier (use cases, invariants, calculs et validations des
entités) dans une suite et un job CI dédiés, sans base ni réseau : composants
métier et données réels, dépendances mockées. Séparer les tests techniques des
adaptateurs et les tests d’intégration qui vérifient des composants réels.
Prioriser les règles métier sans reporter les garanties critiques d’un
adaptateur, comme l’isolation des données ou les transactions.

Pour l’intégration, utiliser une base ou une infrastructure dédiée aux tests,
avec jeux de données conçus pour les scénarios, préparation reproductible et
réinitialisation entre tests. Ne pas utiliser de données ou services de
production. Vérifier les contraintes et comportements du système réel.

Les jobs peuvent s’exécuter en parallèle pour vérifier des artefacts déjà
produits, avec les contrôles applicables requis avant fusion. Ce parallélisme CI
n’autorise pas la production simultanée de code, tests et documentation. Mesurer
et afficher la couverture métier séparément pour qu’une couverture technique
élevée ne masque pas des règles métier insuffisamment testées.

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

Conserver une couverture minimale de **80 %**, avec un objectif de **90 %**, sur
le périmètre non exclu. Appliquer un seuil supérieur si le projet l’impose ; une
configuration inférieure ne supprime pas l’objectif commun et son écart doit
être signalé. Les exclusions doivent être explicites et justifiées ; ne pas
exclure automatiquement entités, DTO ou assemblage porteurs de comportements.
Tester les garanties significatives indépendamment du pourcentage. Suivre
l’organisation du projet sans migration systématique vers un chemin de tests
imposé.
