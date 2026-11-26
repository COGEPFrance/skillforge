# Cohérence des données

- Identifier les données possédées par le service, les invariants persistés et les frontières transactionnelles.
- Garder les représentations de stockage et les conversions dans les adapters, derrière des ports typés.
- Définir le comportement en cas de concurrence, mise à jour partielle ou conflit.
- Expliciter la cohérence entre écriture durable et publication d’un message. Choisir un mécanisme adapté au besoin et aux capacités disponibles plutôt qu’un pattern systématique.
- Prévoir les migrations et reprises nécessaires ; considérer le déploiement progressif et les données écrites par plusieurs versions.
- Distinguer retour arrière du code, réversibilité des données et effets externes irréversibles.

## Identité métier et historique

Pour un garde ou une recherche sur des enregistrements liés ou historiques,
comparer le prédicat à l’identité exacte protégée. Vérifier chaque dimension
utile : tenant ou système, entité, identifiant externe, type et statut, selon le
contrat métier. Un enregistrement périmé qui partage seulement une partie de la
clé ne doit pas bloquer une opération indépendante. Distinguer l’historique qui
doit réellement bloquer de celui qui n’est plus propriétaire de la réservation.

## Cycle de vie des réservations et de l’unicité

Si le changement introduit ou modifie unicité, claims, verrous, réservations,
idempotence ou écritures multiples, examiner les transitions applicables :
création, modification ou remplacement, rejeu, changement de propriétaire,
désactivation ou archivage, suppression et nettoyage. Pour chacune, vérifier
l’invariant après succès, refus de validation, échec de persistance, retry et
interruption du processus. Ne pas se limiter à modifier une entité préexistante.

Rechercher les entités partielles, identifiants consommés à tort, réservations
périmées ou orphelines, références incohérentes et libérations prématurées. Une
réponse d’erreur correcte ne suffit pas si l’opération a laissé des mutations
partielles incompatibles avec le contrat.

## Entrelacements concurrents

Pour plusieurs écritures, collections, appels de repository ou effets externes,
énumérer les entrelacements qui peuvent violer l’invariant : création/création,
modification/modification, modification/suppression et panne entre deux effets.
Si l’invariant est global, inclure les opérations entre sous-types ou collections.
Suivre les gagnants et les perdants jusqu’à leur fin, puis vérifier l’état durable
complet selon les [assertions de test attendues](testing.md#cohérence-durable-et-concurrence).
Ne pas imposer ces scénarios à un changement sans invariant concurrent concerné.

## Preuves attendues

Identifier les fenêtres de panne entre effets, les garanties transactionnelles réelles et les scénarios de reprise. Montrer comment un rejeu évite perte et duplication d’effets métier.
