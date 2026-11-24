---
name: update-documentation
description: "Actualiser une documentation en distinguant changements vérifiés et évolutions à réaliser."
---

# update-documentation

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [documentation](../../../references/documentation.md)
- [compatibility](../../../references/compatibility.md)

## Exécution

1. Identifier les documents, contrats, options et procédures affectés dans la phase documentaire choisie. Elle peut précéder code et tests : distinguer ce qui est proposé de ce qui est vérifié et réserver la confrontation finale, sans modifier les autres artefacts.
2. Pour une configuration livrée, vérifier déclaration, alias, consommateur effectif, défauts, exemples et documentation ; ne présenter aucune variable inexistante ou inutilisée comme active. Pour une évolution encore proposée, expliciter noms et défauts prévus et réserver la confrontation finale. Garder les secrets hors exemples.
3. Après un changement d’architecture ou un retrait d’option, rechercher les anciens noms dans le dépôt et corriger les descriptions obsolètes selon la [vérification ciblée](../../../references/documentation.md#configuration-et-architecture). Préserver les références historiques utiles.
4. Vérifier cohérence des pages, liens et exemples sans réécriture indépendante ; conserver une source de vérité par information.

## Résultat et passage de relais

Documents et exemples actualisés, incohérences corrigées et vérifications.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-documentation`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
