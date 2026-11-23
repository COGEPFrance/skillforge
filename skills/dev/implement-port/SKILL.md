---
name: implement-port
description: "Définir un contrat typé de dépendance pour un use case sans adapter concret."
---

# implement-port

## Références

Même en invocation isolée, appliquer le [filtre transverse](../../../references/quality-criteria.md), puis consulter uniquement les détails pertinents ci-dessous.

- [architecture](../../../references/architecture.md)
- [domain-models](../../../references/domain-models.md)

## Exécution

1. Partir des opérations réellement nécessaires au consommateur ; réutiliser les contrats existants sans créer une interface pour remplir une couche.
2. Définir entrées, sorties, erreurs et garanties observables : absence de résultat, conflit ou rejouabilité si ces cas existent. Éviter types de driver, protocole et adapter concret.
3. Placer le port selon les conventions du projet et identifier ses consommateurs affectés avant de changer un contrat existant.

## Résultat et passage de relais

Port minimal et garanties explicitement attendues de ses implémentations.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-ports`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
