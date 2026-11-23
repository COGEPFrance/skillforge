---
name: test-crash-recovery
description: "Vérifier la reprise après interruption brutale d’un traitement dans un environnement isolé."
---

# test-crash-recovery

## Références

Lire les sections pertinentes de ces références pour le changement ; elles portent les critères communs à la production et à la revue.

- [testing](../../../references/testing.md)
- [resilience](../../../references/resilience.md)
- [data-consistency](../../../references/data-consistency.md)

## Exécution

1. Pour les effets durables concernés, identifier les coupures avant et après écritures, publications et acquittements ainsi que la reprise attendue.
2. Injecter des interruptions brutales uniquement dans un environnement de test autorisé, puis redémarrer et rejouer les traitements concernés.
3. Observer état durable, pertes silencieuses, duplications métier, opérations bloquées et signaux de reprise. Conserver protocole et résultats ; un arrêt propre ne remplace pas cette preuve.

## Résultat et passage de relais

Preuves reproductibles des scénarios de crash et des garanties ou défauts observés.

Transmettre les fichiers concernés, vérifications réellement exécutées, limites et prérequis manquants à `review-resilience`. Un prérequis indispensable manquant bloque la tâche ; ne pas annoncer une réussite partielle comme validation complète.

Respecter la phase et le périmètre du [parcours de production](../../../workflows/production-sequences.md). Ne pas enchaîner une publication ou une modification externe non autorisée.
