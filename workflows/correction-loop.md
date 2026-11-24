# Correction et reprise des validations

1. Exécuter les agents sélectionnés séquentiellement dans l’ordre enregistré.
2. Sur `FAIL` ou `BLOCKED`, arrêter les étapes suivantes et transmettre les constats à l’agent responsable du composant ou au responsable du prérequis.
3. Identifier la phase propriétaire de l’artefact à corriger. Si elle diffère de la phase active, suspendre celle-ci et enregistrer le retour ; une seule phase reste active. Corriger dans le périmètre autorisé, en conservant les preuves du défaut et de la correction. Une revue n’effectue pas elle-même la correction.
4. Comparer les modifications à l’état précédemment revu. Invalider les validations dont le code, les contrats, la configuration ou les hypothèses ont changé, y compris celles d’étapes antérieures.
5. Repartir de la première étape invalidée ; rejouer les revues affectées dans leur ordre avant de reprendre la suite.
6. Ne pas répéter sans fin une correction identique : si le même blocage subsiste après deux tentatives sans preuve nouvelle, restituer le blocage et la décision nécessaire au responsable du parcours.

Un changement hors périmètre suit le [parcours de refactoring](refactoring-scope.md). Toute nouvelle action externe reste soumise à l’autorisation de la tâche. Les verdicts sont définis dans [review-result.md](review-result.md).
