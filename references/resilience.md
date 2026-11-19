# Résilience et reprise après crash

- Définir timeouts, retries bornés, limites de concurrence et conditions d’abandon ; distinguer erreurs temporaires et définitives.
- Prendre en compte les défaillances dans le code, au-delà des garanties du framework, du broker et de l’infrastructure.
- Pour chaque traitement concerné, identifier état durable, traitements partiels, point de reprise et opérations rejouables.
- Préserver l’idempotence des effets lors des doublons et redémarrages ; aligner les acquittements sur les effets enregistrés.
- Prévoir messages en échec, remise en traitement maîtrisée et absence de boucle infinie.
- Prévoir l’arrêt propre sans supposer qu’il se produira lors d’une panne.

## Preuves attendues

Examiner un crash avant et après les principales écritures, publications et acquittements. Vérifier reprise, absence de perte silencieuse, maîtrise des effets dupliqués et visibilité des opérations bloquées. L’arrêt propre seul n’est pas une preuve de résistance au crash.
