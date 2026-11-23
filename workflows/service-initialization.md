# Initialisation d’un service

## Entrées

Destination, besoin technique du service, versions Arclith et Python, blueprint existant identifié, configuration et dépendances de vérification disponibles.

## Séquence

1. `scaffold-arclith-service` génère le squelette sans écraser de code existant.
2. `apply-arclith-blueprint` applique le blueprint compatible et conserve les versions et changements effectués.
3. `review-service-foundation` vérifie structure, assemblage, configuration, démarrage et observabilité de base.
4. Sur `PASS`, transmettre le socle et les preuves au [parcours de fonctionnalité](feature-implementation.md). Sinon appliquer la [boucle de correction](correction-loop.md).

Ces deux tâches de production constituent le socle soumis à cette revue avant toute fonctionnalité. Les procédures Arclith restent la référence pour les opérations propres au framework. Sur un service existant, vérifier les écarts nécessaires plutôt que régénérer le projet. L’absence de blueprint adapté bloque le parcours.
