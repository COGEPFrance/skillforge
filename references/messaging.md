# Contrats et garanties asynchrones

Les instructions opérationnelles sont dans [`implement-messaging`](../skills/dev/implement-messaging/SKILL.md), [`review-messaging`](../skills/review/review-messaging/SKILL.md).

Lire lorsqu’un échange asynchrone ou son consommateur change.

Pour la revue, suivre un message du producteur aux effets durables : contrat, acquittement, doublon, message invalide, tentatives et échec définitif. Examiner l’ordre seulement lorsqu’il porte une garantie métier. Lire [cohérence](data-consistency.md) si une écriture et une publication sont séparées.

Vérifier les mécanismes réellement activés dans le socle et le broker retenus. Leur existence ne prouve pas leur configuration. Ne pas promettre une unicité des effets ou une garantie de livraison non démontrée ; transmettre les fenêtres de coupure aux tests concernés.
