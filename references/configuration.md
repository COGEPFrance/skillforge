# Configuration

- Centraliser les variations utiles et identifiées dans des fichiers lisibles, de préférence YAML ou un format équivalent adapté.
- Configurer les variations d’environnement et de déploiement ainsi que les seuils, délais, tailles de lots et limites pertinents ; ne pas rendre chaque détail paramétrable.
- Typer et valider la configuration au démarrage, définir les valeurs par défaut et la priorité des sources.
- Éviter les lectures dispersées de fichiers ou de variables d’environnement dans les composants métier.
- Fournir les secrets séparément des fichiers partagés ; ne pas les exposer dans les exemples ou les sorties.
- Ne pas transformer les invariants métier en options désactivables.

## Valeurs effectives et modes supportés

- Tracer chargement, alias, défauts, priorité des sources, validation, conversion
  d’unité et consommateur réel. Une déclaration valide ne prouve ni l’injection
  ni l’usage ; examiner les options devenues sans effet.
- Définir les contraintes entre options selon les modes : adresse ou secret
  requis quand une capacité est activée, sans les rendre systématiquement
  obligatoires lorsqu’elle est désactivée. Suivre les valeurs absentes et les
  valeurs explicites qui diffèrent du défaut.
- Sélectionner les combinaisons selon les dépendances et les risques du
  changement ; ne pas demander toutes les combinaisons de toutes les options.
- Respecter le moment d’application prévu : démarrage ou rechargement si ce
  dernier est promis. Ne pas réclamer de rechargement à chaud par défaut.
- Refuser les valeurs invalides selon le contrat, avant les opérations qu’elles
  doivent empêcher. Un défaut de secours n’est acceptable que s’il est prévu ;
  ne pas masquer un échec de validation en service démarré sur d’autres valeurs.

Pour une contrainte, un défaut ou un modèle modifié, appliquer les
[contrôles de compatibilité des valeurs](compatibility.md#valeurs-acceptées-et-validations)
en plus du contrôle des configurations invalides : une valeur précédemment
acceptée peut désormais empêcher le démarrage.

## Preuves attendues

Pour une option ajoutée ou modifiée, identifier sa source, son type, son unité,
sa validation, son consommateur et ses valeurs effectives selon les sources et
modes pertinents. Vérifier le comportement d’une configuration invalide et les
exemples maintenus. Distinguer règle confirmée et comportement simplement observé.
