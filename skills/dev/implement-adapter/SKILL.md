---
name: implement-adapter
description: "Implémenter un port à la frontière d’un transport, stockage ou service externe."
---

# implement-adapter

## Références

Commencer par la [sélection des exigences communes](../../../references/quality-criteria.md), même pour une invocation isolée, puis lire les références spécialisées ci-dessous.

- [architecture](../../../references/architecture.md)
- [compatibility](../../../references/compatibility.md)
- Si le brief retient Arclith : [profil et délégation](../../../references/profiles/python-arclith.md)

## Exécution

1. Lire le port et les garanties attendues ; examiner les capacités du socle et des dépendances retenus avant de créer un mécanisme équivalent.
2. Isoler protocole, conversions et erreurs techniques dans l’adapter. Construire les sorties depuis les seules données nécessaires ; ne pas exposer automatiquement tout l’agrégat dans une API ou un événement.
3. Valider les entrées non fiables et préserver les autorisations et secrets ; prévoir les défaillances de la dépendance et restituer les erreurs du contrat sans faux succès.
4. Garder BSON, noms historiques, identifiants techniques et index dans l’adapter de persistance lorsqu’il est concerné. Le core reçoit des modèles typés, pas des documents bruts.

## Résultat et passage de relais

Adapter conforme au port, conversions et erreurs ; vérifications d’intégration nécessaires.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-adapters`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
