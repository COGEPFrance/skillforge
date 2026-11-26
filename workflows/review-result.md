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

## Gravité des commentaires

Utiliser un libellé textuel avec le pictogramme ; ne pas dépendre de la couleur
seule ni ajouter de HTML ou CSS.

| Niveau | Sens |
| --- | --- |
| 🔴 **Bloquant** | Bug, régression, vulnérabilité, perte de données, invariant ou contrat rompu exigeant une correction avant validation. |
| 🟠 **Important** | Défaut significatif de conception, performance, maintenabilité, typage ou tests, avec un impact concret à expliquer. |
| 🔵 **Suggestion** | Amélioration utile non bloquante ; à utiliser avec parcimonie, sans préférence de style personnelle. |
| 🟣 **Question** | Clarification réellement nécessaire pour établir l’intention ou déterminer un risque concret. |

La gravité décrit l’impact ; le verdict décrit la validation du périmètre.
Un défaut démontré empêchant un critère applicable donne `FAIL`. Une question
donne `BLOCKED` seulement si la décision ou preuve manquante est indispensable ;
sinon, conserver l’incertitude dans les limites sans la transformer en défaut.

## Commentaires prêts à publier

Présenter chaque constat dans un bloc Markdown distinct, sans réunir des
problèmes indépendants. Trier par gravité, puis fichier et ligne. Pour une PR,
ancrer le commentaire sur la plus petite plage utile de lignes modifiées ; pour
un artefact sans diff, donner l’emplacement précis dans l’état examiné.

```md
**Fichier :** `chemin/du/fichier.py`
**Lignes :** 42-48

🟠 **Important — Titre court décrivant le défaut**

Scénario déclencheur, problème démontré et impact concret ou invariant violé.

Correction attendue ou piste de résolution actionnable.
```

Un titre nomme le défaut observable plutôt qu’une règle abstraite. Une question
ne remplace pas l’explication d’un défaut déjà établi. Présenter les commentaires
à l’utilisateur ; leur préparation n’autorise pas leur publication sur GitHub.

Si aucun défaut actionnable n’est trouvé, le dire explicitement et conserver le
verdict justifié par les preuves et limites. Terminer par un bref rappel du
périmètre, de la révision et des incertitudes matérielles, sans reproduire les
rapports CI.
