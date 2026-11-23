# Implémentation par composants

## Préparer le parcours

Partir des briefs et d’un socle vérifié selon le projet. L’ordre ci-dessous convient aux composants hexagonaux ; ne pas créer de couche pour remplir une étape ou modifier une autre architecture sans décision explicite. Identifier le besoin, les critères de réussite, les composants existants, les dépendances et le parcours code d’abord ou tests d’abord. Enregistrer les étapes applicables et leurs revues avant l’exécution.

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

Après les revues intermédiaires, poursuivre les tests, validations des risques, documentation et livraison selon [production-sequences.md](production-sequences.md). Aucun enchaînement parallèle implicite. Les erreurs suivent [correction-loop.md](correction-loop.md).
