---
name: implement-persistence
description: "Implémenter la persistance selon les contrats du projet en préservant les invariants et la cohérence."
---

# implement-persistence

## Références

Commencer par la [sélection des exigences communes](../../../references/quality-criteria.md), même pour une invocation isolée, puis lire les références spécialisées ci-dessous.

- [data-consistency](../../../references/data-consistency.md)
- [architecture](../../../references/architecture.md)
- [compatibility](../../../references/compatibility.md)

## Exécution

1. Identifier les données possédées, invariants, contrat du repository et frontières transactionnelles selon l’architecture du projet ; ne pas créer une couche pour satisfaire ce skill.
2. Implémenter conversions et concurrence dans le composant de persistance. Les objets métier/persistants connus ont un contrat typé ; garder les documents bruts, noms historiques et détails du driver hors du domaine et des use cases.
3. Pour Mongo, garder `_id`, BSON, dates, index et compatibilité des anciens formats dans les mappers de l’adapter ; utiliser les emplacements du projet plutôt qu’imposer `adapters/output/`.
4. Préparer les migrations, garanties de publication et reprises nécessaires, en distinguant retour arrière du code et réversibilité des données ; ne pas exécuter sur un environnement non autorisé.

## Résultat et passage de relais

Persistance typée, cohérence et concurrence définies ; migrations et scénarios de panne concernés.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-data-consistency`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
