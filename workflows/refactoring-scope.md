# Périmètre du refactoring

- Si le refactoring est explicitement demandé ou nécessaire au besoin courant, décrire son lien avec le changement, limiter le périmètre et appliquer `refactor` avec les revues et validations affectées.
- S’il est indépendant, ne pas le réaliser dans ce changement. Préparer une issue avec problème, composants et consommateurs affectés, risques de compatibilité ou de migration, périmètre et validations attendues.
- Ouvrir l’issue dans le dépôt concerné quand cette publication est autorisée ; sinon restituer le texte prêt à publier et son emplacement cible. Ne pas considérer la découverte d’une dette comme une autorisation générale de publication externe.
- Vérifier les issues pertinentes existantes avant d’en proposer une nouvelle ; relier les preuves au code réellement examiné.

Le retour de review peut révéler le même problème dans plusieurs composants du périmètre : corriger la cause commune nécessaire sans engager une refonte indépendante.
