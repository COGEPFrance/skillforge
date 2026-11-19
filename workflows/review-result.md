# Résultat d’une revue

Chaque revue identifie le skill, son périmètre, la révision ou l’état des fichiers examinés et la phase : préliminaire ou finale.

## Verdict

- `PASS` : critères applicables du périmètre vérifiés, avec preuves suffisantes pour la phase annoncée.
- `FAIL` : un défaut démontré empêche la validation ; préciser effet, emplacement et correction attendue.
- `BLOCKED` : une preuve, une dépendance ou une décision indispensable manque ; préciser ce qui permettrait de reprendre.

Séparer constats bloquants, suggestions et hypothèses. Pour chaque contrôle, indiquer les preuves, commandes exécutées et limites. Ne pas inventer un résultat ni modifier le code pendant la revue.

Une revue sélectionnée ne peut être omise silencieusement. Si son périmètre semble absent, faire réviser explicitement la sélection du parcours avant de continuer. Une revue préliminaire peut valider la structure sans certifier le comportement ; sa portée doit être explicite.

## Sortie attendue

Révision et phase ; verdict ; constats avec gravité, emplacement et effet ; preuves ; limites ; corrections ou prérequis de reprise. Les suggestions non bloquantes n’empêchent pas `PASS`. Les constats non démontrés restent des hypothèses et ne deviennent pas automatiquement des défauts.
