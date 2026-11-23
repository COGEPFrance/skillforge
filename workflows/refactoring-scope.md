# Périmètre du refactoring

- Si le refactoring est explicitement demandé ou nécessaire au besoin courant, décrire son lien avec le changement, limiter le périmètre et appliquer `refactor` avec les revues et validations affectées.
- S’il est indépendant et important, ne pas le réaliser dans ce changement. Utiliser le suivi existant ; à défaut, créer ou compléter `upgrade.md` à la racine, sans bloc dupliqué : titre, constat et contexte, risque, évolution attendue, périmètre probable et critères de validation. Cette note prépare une issue avec les composants/consommateurs et risques de compatibilité ou de migration utiles.
- Ouvrir l’issue dans le dépôt concerné quand cette publication est autorisée ; sinon restituer le texte prêt à publier et son emplacement cible. Ne pas considérer la découverte d’une dette comme une autorisation générale de publication externe.
- Vérifier les issues pertinentes existantes avant d’en proposer une nouvelle ; relier les preuves au code réellement examiné.

Le retour de review peut révéler le même problème dans plusieurs composants du périmètre : corriger la cause commune nécessaire sans engager une refonte indépendante.
