---
name: implement-persistence
description: "Implémenter la persistance selon les contrats du projet en préservant les invariants et la cohérence."
---

# implement-persistence

## Références

Même en invocation isolée, appliquer le [filtre transverse](../../../references/quality-criteria.md), puis consulter uniquement les détails pertinents ci-dessous.

- [data-consistency](../../../references/data-consistency.md)
- [architecture](../../../references/architecture.md)
- [compatibility](../../../references/compatibility.md)

## Exécution

1. Identifier propriétaire des données, invariants persistés, contrat existant et frontières transactionnelles ; ne pas accéder directement aux données internes d’un autre service.
2. Garder schémas et conversions dans le composant de persistance prévu par le projet ; ne pas créer un port ou une couche pour satisfaire ce skill. Définir le comportement en concurrence, conflit ou mise à jour partielle en fonction des garanties réelles du stockage.
3. Si une publication accompagne une écriture, expliciter leur cohérence et les fenêtres de panne. Choisir le mécanisme selon le besoin et les capacités disponibles.
4. Préparer les migrations nécessaires et leur reprise en tenant compte des versions coexistantes. Distinguer retour arrière du code, réversibilité des données et effets irréversibles ; ne pas exécuter une migration hors environnement autorisé.

## Résultat et passage de relais

Persistance typée, cohérence et concurrence définies ; migrations et scénarios de panne concernés.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-data-consistency`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
