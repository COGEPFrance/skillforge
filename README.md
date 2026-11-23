# Skillforge

Catalogue de skills partagés pour aligner les développements et les agents
autonomes. Le brief du projet fixe le besoin ; le brief d’architecture technique
fixe les choix applicables. Les projets conservent leurs règles métier propres.

Arclith est une bibliothèque Python privilégiée pour rationaliser les projets
qui la retiennent, sans être imposée à tous. Ses propres skills portent ses
procédures ; Skillforge les utilise dans ce contexte. Pour les projets Python,
Pydantic est la base commune des entités et une dépendance assumée du domaine,
avec ou sans Arclith.

## Catalogue

- [Développement](skills/dev/) : socle Arclith, lib, entités, ports, use cases,
  adapters, configuration, résilience et instrumentation.
- [Tests](skills/test/) : stratégie, tests unitaires, intégration, contrats,
  reprise après crash et mesures de performance.
- [Revues spécialisées](skills/review/) : validation des composants et des risques.
- [Documentation](skills/documentation/) : rédaction et mise à jour.
- [Delivery](skills/delivery/) : commits, PR, releases et préparation du déploiement.

Les 48 skills portent les instructions de leur périmètre et consultent les
[détails conditionnels](references/quality-criteria.md)
et les [workflows](workflows/). Les étapes sélectionnées sont séquentielles :
un échec bloque la suite, demande une correction et fait rejouer les validations
affectées.

Le [journal des arbitrages](docs/skill-personalization-decisions.md) explique la
répartition des règles ; il ne fait pas partie du contexte à charger à chaque tâche.

Le catalogue source doit rester accompagné de ses références. Le format
d’installation et le moteur d’agents restent à définir ; le diagnostic reste
optionnel et ses skills ne sont pas encore créés.

## Documents antérieurs

Les documents de règles antérieurs et la proposition détaillée sont conservés
dans [_rules/](_rules/). Leur contenu n’est pas automatiquement incorporé aux
skills : il sera examiné et intégré progressivement. Le README de ce dossier
conserve un instantané de la proposition initiale.
