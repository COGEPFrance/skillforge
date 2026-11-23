# Documentation

- Définir le public, la tâche et le résultat attendu du document.
- Documenter le comportement, les contrats, la configuration et les procédures utiles en distinguant clairement comportement vérifié et contrat ou conception à réaliser.
- Préserver une source de vérité pour chaque information ; préférer les renvois à la duplication.
- Produire ou actualiser la documentation uniquement dans sa phase dédiée, à la place choisie dans le [parcours](../workflows/production-sequences.md). Elle peut précéder code ou tests : identifier alors les propositions et réserver la vérification contre l’implémentation finale. Ne pas modifier code ou tests pendant cette phase ; une divergence déclenche une reprise explicite.
- Vérifier liens, exemples et commandes dans leur contexte ; distinguer procédures exécutées et exemples non vérifiés.

## Preuves attendues

Relier les affirmations à l’implémentation ou à une source propriétaire, vérifier la cohérence des exemples et signaler les limites de vérification. Un document ne doit pas présenter une proposition comme déjà implémentée.

## Configuration et architecture

Pour une option ajoutée, retirée ou remplacée, confronter déclaration, alias,
validation, défaut, injection et usage effectif aux exemples d’environnement,
variables documentées, descriptions d’activation et tests de chargement/défaut.
Suivre les chemins du projet plutôt qu’imposer un fichier de settings donné.
Pour le comportement livré, ne documenter une variable que si elle est déclarée
et utilisée, avec le même défaut que le code et sans secrets. Dans une phase
documentaire antérieure au code, identifier séparément les variables et défauts
proposés ; réserver la vérification de leur déclaration et de leur usage à la
confrontation finale, sans les présenter comme actifs.

Après une évolution d’architecture ou un retrait de composant, rechercher les
noms supprimés dans le dépôt et examiner chaque occurrence. Une conception
intermédiaire ne décrit pas automatiquement l’implémentation finale ; les notes
historiques explicitement identifiées peuvent rester. Éviter la paraphrase du
code et les docstrings imposées à tout module : documenter une décision, un
invariant, une contrainte ou un comportement non évident à son endroit utile.
