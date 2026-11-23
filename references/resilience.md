# Défaillances et interruption brutale

Les instructions opérationnelles sont dans [`implement-resilience`](../skills/dev/implement-resilience/SKILL.md), [`test-crash-recovery`](../skills/test/test-crash-recovery/SKILL.md), [`review-resilience`](../skills/review/review-resilience/SKILL.md).

Lire si une dépendance peut bloquer, un traitement est relancé ou des effets survivent au processus.

Distinguer erreurs temporaires et définitives ; les retries ne conviennent qu’aux opérations rejouables. Pour des effets durables, identifier état partiel, point de reprise et conditions d’abandon. Pour les messages, maîtriser acquittements et remise en traitement.

La revue examine les coupures avant et après les effets pertinents, publications et acquittements. Un crash de test vérifie reprise, pertes silencieuses, duplications métier et opérations bloquées. L’arrêt propre est utile mais ne prouve pas la résistance à une interruption brutale ; une opération pure sans effet durable n’impose pas un checkpoint.
