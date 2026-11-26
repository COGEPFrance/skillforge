# Méthode commune de revue

Appliquer cette méthode avant les critères spécialisés, y compris lorsqu’un
skill de revue est invoqué seul. Elle cadre l’analyse sans élargir son périmètre
ni remplacer le [parcours de sélection des revues](../workflows/review-sequences.md).

## Dépôt, sources et comparaison

- Résoudre le dépôt visé depuis la demande ou l’URL de PR et vérifier son remote ;
  le répertoire courant n’est pas nécessairement la cible. Rechercher d’abord
  les clones dans les emplacements déclarés par l’environnement, puis dans les
  racines de travail disponibles. Ne pas modifier un checkout pour le localiser.
- Lire les instructions du dépôt, les briefs projet et technique, les critères
  d’acceptation et les contrats applicables. Identifier la source et la version
  des règles utilisées ; signaler une source indisponible sans présenter une
  copie locale comme nécessairement à jour.
- Pour une PR ou une branche, identifier les révisions source et cible depuis
  la demande ou les métadonnées de PR. Examiner tout le diff depuis leur
  merge-base jusqu’à la révision source, pas seulement le dernier commit. Si la
  base reste ambiguë et peut changer les conclusions, la faire préciser.
- Pour une revue d’artefact ou de fichiers locaux sans PR, enregistrer l’état
  effectivement examiné et les changements inclus ; ne pas inventer une base
  Git. Dans tous les cas, distinguer les changements des éléments préexistants.

## Établir un constat

- Partir du comportement attendu, des invariants et des erreurs prévues. Lire
  le diff et assez de contexte, d’appels, de contrats et de tests pour suivre le
  chemin qui déclenche le problème, dans le dépôt et le périmètre retenus.
- Relier chaque défaut au changement : introduit par lui ou rendu directement
  pertinent par lui. Ne pas transformer la revue en inventaire de dette ancienne.
- Établir un scénario déclencheur, l’effet observable ou l’invariant violé et une
  correction actionnable. Distinguer défaut démontré, hypothèse à confirmer et
  préférence de style ; une préférence seule ne justifie pas un constat.
- Lire les entrées et assertions des tests pertinents pour déterminer ce qu’ils
  prouvent réellement. Une CI verte ou un pourcentage de couverture ne démontre
  pas à lui seul la correction du comportement.
- Examiner les configurations et chemins supportés concernés, au-delà des seules
  valeurs par défaut et des exemples. Ne pas écarter un défaut démontré parce que
  sa condition est rare, ni limiter artificiellement le nombre de constats utiles.
- Lorsqu’une même cause semble répétée, rechercher ses autres occurrences dans
  le périmètre revu et regrouper uniquement celles qui constituent le même défaut.

## Contrôles et restitution

Utiliser les contrôles pertinents autorisés par la tâche et les critères du
skill. Distinguer lecture du code, résultats d’exécution observés et preuves CI
de la révision examinée. Une limite d’exécution explicite reste applicable ; une
preuve indispensable absente suit le verdict `BLOCKED`, sans résultat inventé.

La revue ne corrige pas les fichiers. Elle ne vaut pas autorisation de commit,
push ou publication de commentaires : restituer les constats à l’utilisateur
selon le [format commun](../workflows/review-result.md), sauf demande explicite
autorisant l’action externe concernée.
