# Échanges asynchrones

- Utiliser les messages lorsqu’ils apportent un bénéfice identifié : découplage, traitement différé ou absorption de charge.
- Définir les contrats, producteurs, consommateurs et garanties nécessaires ; distinguer commande et événement selon leur intention.
- Préciser doublons, idempotence, ordre utile, concurrence, retries bornés et destination des messages en échec.
- Positionner les acquittements selon les effets réellement durables. Traiter explicitement la coupure entre persistance et publication, avec le référentiel de [cohérence des données](data-consistency.md).
- Propager le contexte de corrélation sans secrets ; rendre visibles le retard, l’accumulation et les tentatives.
- Réutiliser les mécanismes Arclith et du broker retenu ; leur présence ne démontre pas leur bonne configuration.

## Preuves attendues

Suivre un message du producteur à ses effets persistés, puis examiner doublon, panne, message invalide et traitement interrompu. Ne pas promettre une garantie de livraison ou d’unicité non démontrée.
