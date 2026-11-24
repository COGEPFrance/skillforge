---
name: implement-entity
description: "Implémenter un modèle métier ou un contrat de données en distinguant entité, valeur et DTO ; utiliser Pydantic pour Python."
---

# implement-entity

## Références

Commencer par la [sélection des exigences communes](../../../references/quality-criteria.md), même pour une invocation isolée, puis lire les références spécialisées ci-dessous.

- [domain-models](../../../references/domain-models.md)
- [architecture](../../../references/architecture.md)
- Si le brief retient Arclith : [profil et délégation](../../../references/profiles/python-arclith.md)

## Exécution

1. Qualifier le concept : agrégat, entité, objet valeur, commande, query, DTO ou contexte. Identifier identité, cycle de vie et transitions seulement pour les concepts qui les portent ; ne pas les inventer pour un DTO technique. Réutiliser un modèle seulement si sa signification et ses contraintes sont les mêmes.
2. Pour les projets Python, utiliser des modèles Pydantic explicitement typés pour les classes de données métier, de contrat et de contexte, y compris techniques. Pydantic est une dépendance assumée du domaine ; séparer contrats d’API, événements et représentation persistée.
3. Pour Python, déclarer chaque champ Pydantic avec `Field`, une `description` explicite et des `examples` représentatifs, synthétiques et sans données sensibles. Exprimer les contraintes locales par les types et les paramètres de `Field` ; réserver les validateurs aux transformations non déclaratives et aux invariants croisés. Suivre les [règles Pydantic](../../../references/domain-models.md#python--pydantic) pour validation et héritage.
4. Exposer les mises à jour métier par des opérations nommées : valider l’état final proposé avant remplacement et préserver l’ancien état si la validation échoue. Ne pas passer par un export dictionnaire puis merge pour contourner cette opération ; vérifier création et mises à jour invalides.

## Résultat et passage de relais

Modèle ou contrat typé, rôle et invariants applicables ; scénarios à vérifier lors de la phase de tests.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-domain-models`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
