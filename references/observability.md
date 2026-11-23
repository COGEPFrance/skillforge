# Signaux exploitables

Les instructions opérationnelles sont dans [`instrument-service`](../skills/dev/instrument-service/SKILL.md), [`review-observability`](../skills/review/review-observability/SKILL.md).

Lire si instrumentation, corrélation ou exploitation d’un traitement change.

Choisir les signaux qui répondent aux questions d’exploitation. Selon le traitement, suivre corrélation entre appels, messages, différé et tentatives ; rendre visibles les échecs et blocages, sans succès apparent.

Pour la revue, suivre un succès et un échec avec les signaux effectivement émis et consultables ; examiner secrets, données sensibles, cardinalité et coût. Un exporteur déclaré ou un collecteur indisponible ne valide pas la chaîne complète. Décrire la partie vérifiée et celle encore requise.
