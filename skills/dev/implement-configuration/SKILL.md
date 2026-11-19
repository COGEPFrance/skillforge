---
name: implement-configuration
description: "Centraliser et valider une variation de configuration utile à un service."
---

# implement-configuration

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [configuration](../../../references/configuration.md)
- [profiles/python-arclith](../../../references/profiles/python-arclith.md)

## Exécution

1. Identifier option, consommateurs, valeurs par défaut et sources autorisées.
2. Utiliser le chargement typé du socle et un fichier lisible ; séparer les secrets et définir la priorité des sources.
3. Relier le consommateur à la configuration validée et vérifier le rejet des valeurs invalides ; ne pas rendre les invariants métier optionnels.

## Résultat et passage de relais

Option centralisée, validation, consommateur et exemples sans secrets.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-configuration`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
