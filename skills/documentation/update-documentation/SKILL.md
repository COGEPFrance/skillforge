---
name: update-documentation
description: "Actualiser une documentation existante après un changement de comportement validé."
---

# update-documentation

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [documentation](../../../references/documentation.md)
- [compatibility](../../../references/compatibility.md)

## Exécution

1. Identifier pages, contrats, configuration, exemples et procédures affectés, ainsi que leur public.
2. Actualiser à partir de la version validée, en préservant les sources de vérité ; supprimer les contradictions sans réécriture indépendante.
3. Vérifier liens et cohérence des exemples avec leurs prérequis ; relever les commandes non exécutées et les garanties restant à établir.

## Résultat et passage de relais

Documents et exemples actualisés, incohérences corrigées et vérifications.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-documentation`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
