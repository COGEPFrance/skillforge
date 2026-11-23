---
name: implement-lib
description: "Implémenter un composant réutilisable autonome lorsque la capacité manque réellement au socle et aux dépendances."
---

# implement-lib

## Références

Commencer par la [sélection des exigences communes](../../../references/quality-criteria.md#sélection-des-exigences-en-production), même pour une invocation isolée, puis lire les références spécialisées ci-dessous.

- [architecture](../../../references/architecture.md)
- [code-quality](../../../references/code-quality.md)
- [profiles/python-arclith](../../../references/profiles/python-arclith.md)

## Exécution

1. Vérifier l’absence de capacité équivalente dans Arclith et les dépendances retenues.
2. Définir responsabilité et contrat propres ; ne pas créer un paquet distinct sans besoin réel.
3. Implémenter le composant sans transport ou stockage imposé à ses consommateurs. Une évolution propre au framework doit être traitée dans Arclith, sans modification de ce dépôt externe hors périmètre.

## Résultat et passage de relais

Composant ciblé, contrat, justification du manque et contraintes pour ses consommateurs.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-lib`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
