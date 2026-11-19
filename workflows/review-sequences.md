# Sélection et ordre des revues

Avant l’exécution, enregistrer le périmètre, la révision, la phase et la liste ordonnée des agents sélectionnés. Motiver les revues omises parce qu’elles sont hors périmètre ; ne pas omettre une revue applicable pour éviter un blocage.

## Revues intermédiaires

Suivre les binômes de [feature-implementation.md](feature-implementation.md). Ces validations portent sur le composant et les preuves disponibles ; les garanties comportementales non vérifiées restent réservées à la phase finale.

## Ordre de référence des revues finales applicables

1. Architecture.
2. Qualité locale du code.
3. Lib, modèles, ports, use cases, adapters et intégration, dans l’ordre des composants modifiés ; rejouer les revues intermédiaires si leur portée ou leurs preuves ont changé.
4. Configuration.
5. Pertinence et fiabilité des tests.
6. Messages.
7. Cohérence des données.
8. Résilience et reprise après crash.
9. Observabilité.
10. Sécurité.
11. Compatibilité.
12. Performance.
13. Documentation, après sa production.
14. Delivery, après sa préparation.

Cet ordre est le parcours par défaut. Le workflow du besoin peut enregistrer un ordre différent si les dépendances de validation le nécessitent, avant exécution. Tous les agents sélectionnés doivent produire `PASS` pour passer au suivant. Voir [review-result.md](review-result.md) et [correction-loop.md](correction-loop.md).

Ce document décrit un protocole d’orchestration ; il ne lance pas d’agents et ne constitue pas un moteur d’exécution.
