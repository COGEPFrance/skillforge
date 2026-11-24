# Socle du service

- Identifier destination, versions, état existant et garanties attendues du socle.
- Utiliser les skills du framework retenu pour sa génération, ses blueprints et
  ses intégrations. Pour Arclith, suivre le
  [parcours de délégation](../workflows/service-initialization.md) ; ne pas
  maintenir de procédure concurrente dans Skillforge.
- Respecter la phase active et faire valider ses livrables avant la suivante.
- Préserver les fichiers existants et limiter les changements au besoin.
- Vérifier les preuves de structure, assemblage, configuration, démarrage et
  observabilité qui s’appliquent au socle, sans ajouter de fonctionnalité métier.
- Enregistrer versions, opérations propriétaires utilisées, résultats et limites.

## Limite de validation

Le démarrage du socle et ses signaux ne garantissent pas les comportements métier
futurs ni les propriétés de performance, de sécurité et de reprise du service
complet. Les contrôles spécifiques du framework appartiennent à ses skills.
