---
name: scaffold-arclith-service
description: "Générer le squelette initial d’un nouveau service Arclith, avant application du blueprint."
---

# scaffold-arclith-service

Le brief d’architecture technique doit retenir Arclith pour ce parcours. Pour ses opérations propres, utiliser les skills Arclith disponibles ou sa documentation correspondant aux versions du projet.

## Références

Même en invocation isolée, appliquer le [filtre transverse](../../../references/quality-criteria.md), puis consulter uniquement les détails pertinents ci-dessous.

- [service-foundation](../../../references/service-foundation.md)
- [profiles/python-arclith](../../../references/profiles/python-arclith.md)

## Exécution

1. Identifier destination, versions Arclith et Python et contenu existant. Lire le [profil Arclith](../../../references/profiles/python-arclith.md) pour retrouver la procédure correspondant aux versions.
2. Générer uniquement le squelette demandé avec une procédure réellement disponible ; si elle manque, signaler le prérequis au lieu d’inventer une commande.
3. Ne pas écraser un service existant : comparer les écarts et arrêter une génération destructive. Conserver versions, fichiers et commandes réellement exécutées ; transmettre à l’étape blueprint sans fonctionnalité métier.

## Résultat et passage de relais

Squelette, versions, procédure exécutée et écarts éventuels.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `apply-arclith-blueprint`, puis soumettre le socle à `review-service-foundation` après application du blueprint selon le [parcours d’initialisation](../../../workflows/service-initialization.md). Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
