# Qualité du code et périmètre

- SRP : chaque composant a une responsabilité et une raison principale de changer.
- KISS : choisir la solution la plus simple qui satisfait le besoin et ses contraintes.
- DRY : mutualiser un concept réellement partagé ; ne pas fusionner des traitements sur leur seule ressemblance.
- SOTA signifie pratiques maintenues, éprouvées et adaptées au besoin, sans recherche systématique de nouveauté.
- Définir des entrées, sorties et erreurs explicitement typées ; isoler les formats externes aux frontières.
- Produire des erreurs actionnables, sans masquer un échec en faux succès. Ne pas ajouter d’abstraction ou de dépendance sans besoin identifié.
- Limiter le changement au besoin traité. Le refactoring nécessaire peut accompagner ce changement ; le refactoring indépendant suit le [parcours dédié](../workflows/refactoring-scope.md).

## Vérification

Utiliser les outils statiques et conventions effectivement configurés dans le projet. Relier tout constat à un effet concret sur le changement, sans imposer une refonte hors périmètre.
