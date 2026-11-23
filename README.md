# Skillforge

Catalogue de skills partagés par les équipes pour développer des services basés
sur Arclith. Les projets conservent leurs skills spécifiques dans leurs propres
marketplaces.

## Catalogue

- [Développement](skills/dev/) : socle Arclith, lib, entités, ports, use cases,
  adapters, configuration, résilience et instrumentation.
- [Tests](skills/test/) : stratégie, tests unitaires, intégration, contrats,
  reprise après crash et mesures de performance.
- [Revues spécialisées](skills/review/) : validation des composants et des risques.
- [Documentation](skills/documentation/) : rédaction et mise à jour.
- [Delivery](skills/delivery/) : commits, PR, releases et préparation du déploiement.

Les 48 skills s’appuient sur les [référentiels communs](references/quality-criteria.md)
et les [workflows](workflows/). Les étapes sélectionnées sont séquentielles :
un échec bloque la suite, demande une correction et fait rejouer les validations
affectées.

Le catalogue source doit rester accompagné de ses références. Le format
d’installation et le moteur d’agents restent à définir ; le diagnostic reste
optionnel et ses skills ne sont pas encore créés.

## Documents antérieurs

Les documents de règles antérieurs et la proposition détaillée sont conservés
dans [_rules/](_rules/). Leur contenu n’est pas automatiquement incorporé aux
skills : il sera examiné et intégré progressivement. Le README de ce dossier
conserve un instantané de la proposition initiale.
