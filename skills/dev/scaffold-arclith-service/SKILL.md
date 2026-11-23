---
name: scaffold-arclith-service
description: "Générer le squelette initial d’un nouveau service Arclith, avant application du blueprint."
---

# scaffold-arclith-service

Ce parcours s’applique lorsque le brief d’architecture technique retient Arclith. Utiliser ses skills disponibles ou sa documentation pour ses procédures propres.

## Références

Commencer par la [sélection des exigences communes](../../../references/quality-criteria.md), même pour une invocation isolée, puis lire les références spécialisées ci-dessous.

- [service-foundation](../../../references/service-foundation.md)
- [profiles/python-arclith](../../../references/profiles/python-arclith.md)

## Exécution

1. Identifier destination et versions ; vérifier le contenu existant avant génération.
2. Retrouver la procédure Arclith réellement disponible et générer uniquement le squelette demandé. Si la procédure manque, signaler le prérequis au lieu d’inventer une commande.
3. Conserver les fichiers existants ; arrêter si la génération risque de les écraser. Transmettre le socle à l’étape blueprint.

## Résultat et passage de relais

Squelette, versions, procédure exécutée et écarts éventuels.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `apply-arclith-blueprint`, puis soumettre le socle à `review-service-foundation` après application du blueprint selon le [parcours d’initialisation](../../../workflows/service-initialization.md). Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
