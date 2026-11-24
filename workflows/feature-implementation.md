# Implémentation par composants

## Préparer le parcours

Partir des briefs et d’un socle vérifié selon le projet. L’ordre ci-dessous convient aux composants hexagonaux ; ne pas créer de couche pour remplir une étape ou modifier une autre architecture sans décision explicite. Identifier le besoin, les critères de réussite, les composants existants et les dépendances. Enregistrer les phases dans l’ordre choisi selon [production-sequences.md](production-sequences.md) ; le tableau ci-dessous organise uniquement la phase de code et n’impose pas sa place par rapport aux tests ou à la documentation.

## Ordre de référence

| Production | Première revue avant l’étape suivante |
| --- | --- |
| `implement-lib`, uniquement si une capacité manque réellement | `review-lib` |
| `implement-entity` | `review-domain-models` |
| `implement-port` | `review-ports` |
| `implement-usecase` | `review-usecases` |
| `implement-adapter` | `review-adapters` |
| `integrate-service-components` | `review-service-integration` |

Réutiliser et vérifier les composants existants conformes. Ne pas créer une lib, un port ou une entité sans besoin pour remplir une étape. Si une lib dépend d’un contrat métier à créer, réordonner explicitement ces dépendances avant exécution, sans inversion architecturale.

Configuration, messages, persistance, résilience et instrumentation sont confiés aux skills dédiés au niveau du composant concerné ; les insérer avant sa revue et consigner l’ordre. Examiner les capacités du socle retenu avant de développer un équivalent. Si Arclith est choisi, utiliser ses skills ; une capacité manquante bloque uniquement les garanties et étapes qui en dépendent, sans modification externe hors périmètre.

Après les revues intermédiaires applicables, clôturer la phase de code avant la phase suivante enregistrée selon [production-sequences.md](production-sequences.md). Ne pas écrire les tests ou la documentation pendant cette phase. La séquence concerne les phases de production, pas une obligation de faire une PR par composant. Aucun enchaînement parallèle implicite. Les erreurs suivent [correction-loop.md](correction-loop.md).
