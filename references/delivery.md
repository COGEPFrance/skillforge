# Livraison

- Organiser des changements cohérents, limités au besoin et revus avec leurs preuves de validation.
- Vérifier le contenu exact à committer et publier ; préserver les modifications qui ne font pas partie de la tâche.
- Utiliser les conventions et outils de versionnement du dépôt ; ne pas inventer une stratégie de branches ou de release. Réutiliser une branche de tâche adaptée lorsqu’elle existe ; pour une nouvelle branche, vérifier la base pertinente plutôt qu’imposer origin/main à chaque invocation.
- Préparer les versions, notes de release, migrations, prérequis de déploiement et moyens de reprise nécessaires.
- Distinguer préparation d’un artefact et publication effective. Exécuter commit, push, ouverture de PR, release ou déploiement uniquement dans le périmètre autorisé par la demande.
- Les contrôles applicables et revues sélectionnées doivent être validés avant la livraison correspondante.

## Preuves attendues

Identifier la révision et le contenu livrés, les validations, les dépendances de déploiement et les risques connus. Vérifier l’état distant avant une action qui en dépend.
