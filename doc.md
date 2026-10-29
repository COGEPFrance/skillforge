- Lorsqu’une fonctionnalité ajoute, supprime ou remplace une option de configuration, vérifier dans la même modification :
    •sa déclaration dans adapters/config/settings.py avec son alias ;
    •son utilisation effective dans le conteneur de dépendances et le code ;
    •sa présence dans les exemples .env et la documentation des variables ;
    •les descriptions d’architecture qui dépendent de son activation ;
    •les tests de chargement et de valeur par défaut de la configuration.
les tests de chargement et de valeur par défaut de la configuration.
Une variable d’environnement ne doit être documentée que si elle est effectivement déclarée et utilisée. Réciproquement, toute variable déclarée doit être documentée avec la même valeur par défaut que le code.
Après un changement d’architecture réalisé pendant une PR, rechercher les noms des composants et options supprimés dans l’ensemble du dépôt avant la validation finale. Une documentation issue d’une première version de la conception ne doit pas être conservée sans être confrontée à l’implémentation finalement retenue.
- 