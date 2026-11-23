---
name: implement-lib
description: "Implémenter un composant réutilisable autonome lorsque la capacité manque réellement au socle et aux dépendances."
---

# implement-lib

## Références

Commencer par la [sélection des exigences communes](../../../references/quality-criteria.md), même pour une invocation isolée, puis lire les références spécialisées ci-dessous.

- [architecture](../../../references/architecture.md)
- [code-quality](../../../references/code-quality.md)
- Si le brief retient Arclith : [profil et délégation](../../../references/profiles/python-arclith.md)

## Exécution

1. Identifier la capacité manquante dans le socle, les dépendances et la bibliothèque standard des versions ciblées. Ne pas changer une implémentation seulement pour employer une API plus récente.
2. Définir responsabilité, contrat typé et consommateurs réels ; mutualiser un concept autonome ou partagé, pas seulement du code qui se ressemble. Préférer composition ou fonction stateless ; utiliser l’héritage pour une spécialisation qui respecte le contrat parent.
3. Si un dispatch est nécessaire, lire les [critères de contrat et registre](../../../references/architecture.md#contrats-python-et-dispatch). Garder le composant sans transport ou stockage imposé ; une évolution propre à un framework se propose à son propriétaire sans modification externe hors périmètre.

## Résultat et passage de relais

Composant ciblé, contrat, justification du manque et contraintes pour ses consommateurs.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-lib`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
