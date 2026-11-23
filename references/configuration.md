# Configuration

- Centraliser les variations utiles et identifiées dans des fichiers lisibles, de préférence YAML ou un format équivalent adapté.
- Configurer les variations d’environnement et de déploiement ainsi que les seuils, délais, tailles de lots et limites pertinents ; ne pas rendre chaque détail paramétrable.
- Typer et valider la configuration au démarrage, définir les valeurs par défaut et la priorité des sources.
- Éviter les lectures dispersées de fichiers ou de variables d’environnement dans les composants métier.
- Fournir les secrets séparément des fichiers partagés ; ne pas les exposer dans les exemples ou les sorties.
- Ne pas transformer les invariants métier en options désactivables.

## Preuves attendues

Pour une option ajoutée ou modifiée, identifier sa source, son type, sa validation, son consommateur et ses valeurs effectives selon les sources. Vérifier le comportement d’une configuration invalide et les exemples maintenus.
