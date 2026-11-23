# Observabilité

- Utiliser logs structurés, métriques et traces pour expliquer et mesurer les comportements utiles au service.
- Propager la corrélation et le contexte de trace entre appels et messages, y compris traitements différés et tentatives successives.
- Rendre observables erreurs, retries, abandons, reprises et traitements bloqués ; ne pas transformer les échecs en succès apparents.
- Observer selon le besoin latence, débit, erreurs, ressources, accumulation des messages et délai de traitement.
- Maîtriser le coût de l’instrumentation et la cardinalité des métriques. Protéger secrets et données sensibles dans tous les signaux.
- Réutiliser l’instrumentation Arclith et vérifier les signaux effectivement produits, leur corrélation et leur accessibilité dans l’environnement de vérification.

## Preuves attendues

Suivre un scénario nominal et un échec avec leurs signaux. Une déclaration de logger ou d’exporteur ne prouve ni l’émission ni l’exploitation des traces ; signaler les collecteurs ou outils indisponibles au lieu de conclure à une validation.
