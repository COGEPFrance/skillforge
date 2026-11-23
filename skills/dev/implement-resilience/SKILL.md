---
name: implement-resilience
description: "Implémenter les protections et la reprise d’un traitement face aux défaillances et aux crashes."
---

# implement-resilience

## Références

Même en invocation isolée, appliquer le [filtre transverse](../../../references/quality-criteria.md), puis consulter uniquement les détails pertinents ci-dessous.

- [resilience](../../../references/resilience.md)
- [data-consistency](../../../references/data-consistency.md)
- [observability](../../../references/observability.md)

## Exécution

1. Identifier les défaillances atteignables, effets partiels et garanties requises du traitement ; une opération sans état durable ne nécessite pas un mécanisme de checkpoint.
2. Pour les appels ou traitements concernés, définir timeouts, concurrence bornée, erreurs temporaires ou définitives, tentatives et abandon ; vérifier les protections fournies par le socle avant d’en ajouter.
3. Lorsque des effets survivent au processus, définir état durable, point de reprise et rejouabilité. Aligner acquittements sur les effets enregistrés et maîtriser les duplications métier.
4. Prévoir échec définitif et remise en traitement sans boucle infinie. Gérer l’arrêt propre et transmettre aussi les scénarios où il ne se produit pas.

## Résultat et passage de relais

Garanties applicatives et scénarios de crash avec observations attendues.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-resilience`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Suivre le [parcours de production](../../../workflows/production-sequences.md). Exécuter les vérifications existantes pertinentes ; ne pas enchaîner automatiquement création des tests, documentation ou livraison hors de cette étape.
