---
name: implement-configuration
description: "Centraliser et valider une variation de configuration utile à un service."
---

# implement-configuration

## Références

Commencer par la [sélection des exigences communes](../../../references/quality-criteria.md), même pour une invocation isolée, puis lire les références spécialisées ci-dessous.

- [configuration](../../../references/configuration.md)
- Si le brief retient Arclith : [profil et délégation](../../../references/profiles/python-arclith.md)

## Exécution

1. Identifier option, consommateurs, défauts, alias et sources autorisées ; ne pas rendre un invariant métier désactivable.
2. Utiliser le chargement typé du socle retenu et définir priorité et validation au démarrage ; séparer les secrets des fichiers partagés.
3. Vérifier dans le même changement déclaration, valeur effectivement injectée et utilisée, exemples d’environnement, documentation et tests de chargement/défaut. Suivre les emplacements du projet, sans imposer `adapters/config/settings.py`.
4. Lors d’un retrait ou remplacement, rechercher les anciens noms de composants/options dans le dépôt et confronter chaque occurrence à l’implémentation finale, sans effacer les références historiques légitimes.

## Résultat et passage de relais

Option centralisée, validation, consommateur et exemples sans secrets.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-configuration`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
