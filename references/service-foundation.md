# Socle du service

- Identifier la destination, la version du socle Arclith et le blueprint existant demandé avant toute génération.
- Utiliser les procédures disponibles de la marketplace ou de la documentation Arclith correspondant à cette version ; ne pas inventer des commandes ou des options.
- Scaffold puis application du blueprint sont deux tâches distinctes. Un blueprint absent ou incompatible bloque le parcours ; ne pas inventer une architecture de remplacement.
- Ne pas écraser un service existant : comparer le socle et appliquer uniquement les écarts nécessaires, dans le périmètre demandé.
- Vérifier structure, assemblage des dépendances, configuration, démarrage et signaux d’observabilité de base avant la première fonctionnalité.
- Enregistrer versions, blueprint appliqué, fichiers produits et commandes réellement exécutées. Ne pas ajouter de fonctionnalité métier à cette étape.

## Limite de validation

Le démarrage du socle et ses signaux ne garantissent pas les comportements métier futurs ni les propriétés de performance, de sécurité et de reprise du service complet.
