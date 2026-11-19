## Règle : Mocks pour les tests unitaires

Privilégie les mocks pour isoler les dépendances du composant testé,
y compris les dépendances internes : repositories, services, clients,
loggers, caches, gestionnaires d'authentification et rate limiters.

- Utilise `unittest.mock` : `Mock`, `MagicMock`, `AsyncMock`,
  `create_autospec` et `patch` selon le besoin.
- Lorsque l'interface est disponible, privilégie
  `create_autospec(..., instance=True, spec_set=True)` pour respecter
  les signatures et les attributs de la dépendance.
- Utilise `AsyncMock` pour les méthodes asynchrones.
- Instancie réellement le composant testé et exécute sa logique métier.
  Ne mocke pas la méthode dont tu veux vérifier le comportement.
- Utilise des objets réels pour les données, entités, DTO et objets valeur
  manipulés par le composant testé.
- Configure uniquement les comportements nécessaires au scénario :
  `return_value` pour une valeur retournée et `side_effect` pour une
  exception ou une succession de résultats.
- Privilégie l'injection des mocks dans le composant testé.
  Si `patch` est nécessaire, applique-le dans le module où le symbole
  est utilisé.
- N'utilise pas les fakes de `tests/test_helpers.py` pour les nouveaux TU
  et ne crée pas de nouveaux fakes.

---
## Migration des fakes existants vers des mocks

Lors de l'analyse ou de la modification des tests, si tu détectes
un fake utilisé pour simuler une dépendance du composant testé,
remplace-le directement par un mock adapté, sans demander
de confirmation.

- Applique cette migration aux tests concernés par la tâche.
- Utilise `AsyncMock` uniquement pour les méthodes asynchrones
des dépendances simulées, jamais pour la méthode testée.
- Configure les comportements nécessaires avec `return_value`
  et `side_effect`, en conservant les scénarios et les garanties
  vérifiés par les tests.
- Remplace les assertions propres au fake par des assertions
  sur les résultats observables ou les interactions pertinentes.
- Adapte les fixtures concernées. Avant de modifier une fixture
  partagée, vérifie tous ses usages et adapte les tests dépendants.
  Si certains usages doivent conserver le fake, utilise un mock local
ou une fixture de mock distincte selon les règles de partage des fixtures.
- Ne remplace pas les objets réels servant de données de test
  ni le composant dont la logique est testée.
- Ne modifie pas le code de production pour effectuer cette migration.

---
## Fixtures pytest (`tests/conftest.py`)

Les fixtures sont injectées par paramètre dans la signature du test.

Exemple de nommage pour des fixtures fournissant des mocks :
`def test_xxx(mock_dossier_repository, mock_logger, mock_mdm_client)`

- Avant d'utiliser une fixture, vérifie sa définition et le type
  de dépendance qu'elle fournit.
- Réutilise les fixtures existantes lorsqu'elles fournissent des mocks
  adaptés au besoin.
- Les fixtures fournissant des fakes ne doivent pas être utilisées
  pour les nouveaux TU.
- Lorsqu'une fixture adaptée existe, injecte-la par paramètre :
  ne l'appelle pas directement.
- Chaque test doit disposer de mocks indépendants. Privilégie
  le scope `function` pour les fixtures de mocks.
- Les variables d'environnement MDM sont automatiquement configurées
  par la fixture autouse `setup_test_env_vars`.

Ne crée pas de nouveaux fichiers `conftest.py` dans les sous-dossiers.
Si une nouvelle fixture partagée est nécessaire, ajoute-la dans
`tests/conftest.py`.

---

## Gestion des fixtures

- Avant de créer une nouvelle fixture dans `tests/conftest.py`,
  vérifie si une fixture existante couvre déjà le besoin.
- Pour une configuration propre à un scénario, configure le mock
  directement dans le test, qu'il provienne d'une fixture ou soit
  créé localement.
- Si aucune fixture adaptée n'existe et que le besoin est local,
  crée le mock directement dans le fichier de test.
- Ne modifie jamais la définition d'une fixture partagée pour
  la rendre spécifique à un cas de test.
- Ne transforme pas les fixtures de fakes existantes en fixtures
  de mocks sans vérifier les tests qui en dépendent.

Exemples de configuration dans un test :

`mock_dossier_repository.get_by_id.return_value = dossier`

`mock_dossier_repository.save.side_effect = SomeError()`
.
- La fixture contient uniquement la configuration commune.
- Un mock utilisé uniquement dans un fichier peut être créé localement.
- Tout mock d'une même dépendance nécessaire dans au moins deux fichiers
de tests doit être fourni par une fixture dans `tests/conftest.py`.
La fixture fournit un mock indépendant pour chaque test et contient
uniquement la configuration commune. Les réglages propres aux scénarios
restent dans les tests.

---

## Structure des fichiers

Les tests se trouvent dans `tests/units/` et l'arborescence reflète
celle du code source.

Exemple :
`core/use_cases/update_dossier.py`
→ `tests/units/core/use_cases/test_update_dossier.py`

---

## Conventions

- Nommage : `test_<ce_qui_est_testé>_<contexte>`.
  Exemple : `test_update_dossier_raises_when_uuid_missing`.
  Chaque nom décrit le comportement vérifié. Ne pas utiliser de séparateurs
  décoratifs dans les tests ; utiliser si nécessaire les regroupements du
  framework pour structurer les scénarios. Réserver les commentaires aux
  explications utiles que les noms et la structure ne rendent pas évidentes.
- Pour les tests asynchrones, utilise `@pytest.mark.asyncio`
  et `async def`.
- Pour vérifier les appels asynchrones, utilise les assertions
  d'attente telles que `assert_awaited_once_with`.
- Objectif de couverture : 80 % minimum, 90 % idéalement,
  sur le périmètre non exclu.

---

## Exclusions de couverture

- `dependency_container.py`
- Les entités
- Les DTO

Ces exclusions concernent le calcul de couverture. Une entité contenant
une logique métier ou des validations significatives peut faire
l'objet de tests ciblés.

---

## Qualité des tests

- Avant d'écrire les tests d'un fichier, analyse les tests déjà présents
  dans `tests/units/` pour reprendre les conventions et structures
  compatibles avec ces règles.
- Ne génère pas de tests triviaux ou inutiles. Tester qu'un objet
  s'instancie sans erreur n'est pertinent que si son initialisation
  contient une logique réelle à valider.
- Chaque test doit vérifier les résultats, erreurs et effets de bord attendus
  à travers les interfaces du composant : une valeur retournée, une exception
  levée, un état modifié ou une interaction attendue avec une dépendance.
- Vérifie les interactions uniquement lorsqu'elles font partie
  du comportement attendu : arguments transmis, absence d'appel
  en cas de validation échouée, attente d'une opération asynchrone.
- Évite les assertions sur les détails internes, les méthodes privées
  ou l'ordre des appels, sauf lorsqu'elles vérifient une exigence explicite.
  Ne vérifie pas l'ordre des appels lorsqu'il n'a pas d'importance métier.
- Un test ne doit pas seulement vérifier qu'un mock retourne la valeur
  configurée : il doit vérifier le comportement du composant testé.
- Ne duplique pas les tests existants. Si un comportement est déjà
  couvert dans le même contexte, complète le test si nécessaire.
- Priorise les use cases et leurs règles métier avant les adaptateurs.
- Couvre les cas nominaux, les erreurs et les cas limites pertinents.
- Pour les entités, cible uniquement les règles métier et validations
  significatives.
- Les TU ne doivent effectuer aucun appel réseau réel ni dépendre
  d'une infrastructure externe ou de délais réels.
- Tester explicitement les invariants métier. Pour chaque invariant portant sur
  des champs modifiables, vérifier son respect à la création et par les chemins
  de mise à jour exposés. Couvrir les cas valides, invalides et les limites
  pertinentes. Vérifier qu'une mise à jour refusée laisse l'état existant
  inchangé.
- Ajouter un test de non-régression pour chaque bug corrigé.
- Privilégie des mocks simples, configurés uniquement pour le scénario,
  et des tests lisibles.
- Préserver les comportements existants sauf changement explicitement demandé.

---

## Tests d'architecture

- Définir explicitement le périmètre des sources et des éventuels artefacts issus
  d'une préparation explicite et reproductible analysés par les tests
  d'architecture. Inclure les nouvelles sources de ce périmètre, même non encore
  ajoutées à Git. Exclure les caches, fichiers temporaires, dépendances externes
  et autres fichiers étrangers à l'analyse. À sources et préparation identiques,
  les résidus locaux ne doivent pas influencer le résultat. Ne pas assimiler
  automatiquement un fichier ou un répertoire à un module du projet.

---

## Contraintes

- N'écris que des fichiers de test Python.
- Ne modifie pas le code de production.
- N'écris aucun rapport ou explication.
- N'exécute aucune commande terminal.