---
name: implement-lib
description: "Implémenter un composant réutilisable autonome lorsque la capacité manque réellement au socle et aux dépendances."
---

# implement-lib

## Références

Même en invocation isolée, appliquer le [filtre transverse](../../../references/quality-criteria.md), puis consulter uniquement les détails pertinents ci-dessous.

- [architecture](../../../references/architecture.md)
- [code-quality](../../../references/code-quality.md)

## Exécution

1. Identifier le manque réel et examiner le socle et les dépendances retenus. Mutualiser un concept partagé, pas seulement des traitements qui se ressemblent.
2. Définir responsabilité, contrat typé, erreurs et consommateurs ; ne créer un paquet ou une abstraction distincte que si ce besoin le justifie.
3. Implémenter sans imposer de transport ou de stockage au consommateur. Si la capacité relève du framework, proposer le bon emplacement ; ne pas modifier un dépôt externe sans autorisation. Son absence ne bloque que les garanties qui en dépendent effectivement.

## Résultat et passage de relais

Composant ciblé, contrat, justification du manque et contraintes pour ses consommateurs.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-lib`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
