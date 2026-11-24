---
name: implement-usecase
description: "Implémenter une intention applicative à partir des entités et des ports disponibles."
---

# implement-usecase

## Références

Commencer par la [sélection des exigences communes](../../../references/quality-criteria.md), même pour une invocation isolée, puis lire les références spécialisées ci-dessous.

- [architecture](../../../references/architecture.md)
- [domain-models](../../../references/domain-models.md)
- [code-quality](../../../references/code-quality.md)

## Exécution

1. Lire les critères d’acceptation, modèles et ports disponibles. Représenter une intention métier autonome avec contrats d’entrée et de sortie typés, Pydantic en Python ; une variante purement technique ne devient pas un nouveau use case.
2. Orchestrer au travers des ports, préserver les invariants et appliquer les autorisations au périmètre métier. Garder parsing, payloads de protocole, fichiers, stockage et sérialisation dans les composants techniques appropriés.
3. Placer les DTO et transformations techniques dans les composants prévus par le projet ; garder un helper à usage unique privé au composant. Ne pas extraire une boucle métier simple ni créer un service de préparation uniquement parce que plusieurs dépendances sont appelées ; examiner une extraction si une responsabilité technique autonome apparaît.
4. Demander au repository des objets typés et sauvegarder l’état métier validé, sans `to_document()` ni reconstruction par dictionnaire dans le use case. Définir erreurs et effets partiels ; ne pas masquer l’échec principal. Consulter le [cas best effort](../../../references/code-quality.md#effets-secondaires-optionnels) uniquement si un effet est explicitement optionnel.

## Résultat et passage de relais

Use case typé, dépendances et effets attendus, limites de cohérence identifiées.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-usecases`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
