---
name: implement-configuration
description: "Centraliser et valider une variation de configuration utile à un service."
---

# implement-configuration

## Références

Même en invocation isolée, appliquer le [filtre transverse](../../../references/quality-criteria.md), puis consulter uniquement les détails pertinents ci-dessous.

- [configuration](../../../references/configuration.md)

## Exécution

1. Identifier la variation utile, ses consommateurs, défauts et sources ; suivre le format et le mécanisme du projet, sans imposer YAML ni rendre chaque détail paramétrable.
2. Centraliser le chargement, typer et valider au démarrage ; expliciter la priorité des sources. Fournir les secrets séparément des fichiers partagés et des exemples.
3. Injecter les valeurs validées aux consommateurs ; ne pas disperser les lectures de fichiers ou d’environnement dans le métier ni transformer un invariant métier en option. Vérifier une valeur invalide et une surcharge de source.

## Résultat et passage de relais

Option centralisée, validation, consommateur et exemples sans secrets.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-configuration`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
