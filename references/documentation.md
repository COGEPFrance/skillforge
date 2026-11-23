# Documentation

- Définir le public, la tâche et le résultat attendu du document.
- Documenter le comportement validé, les contrats, la configuration et les procédures utiles sans inventer les garanties non vérifiées.
- Préserver une source de vérité pour chaque information ; préférer les renvois à la duplication.
- Produire ou actualiser la documentation après validation du code et des tests selon le parcours retenu.
- Vérifier liens, exemples et commandes dans leur contexte ; distinguer procédures exécutées et exemples non vérifiés.

## Preuves attendues

Relier les affirmations à l’implémentation ou à une source propriétaire, vérifier la cohérence des exemples et signaler les limites de vérification. Un document ne doit pas présenter une proposition comme déjà implémentée.

## Configuration et architecture

Pour une option ajoutée, retirée ou remplacée, confronter déclaration, alias,
validation, défaut, injection et usage effectif aux exemples d’environnement,
variables documentées, descriptions d’activation et tests de chargement/défaut.
Suivre les chemins du projet plutôt qu’imposer un fichier de settings donné.
Ne documenter une variable que si elle est déclarée et utilisée ; documenter les
variables d’environnement actives avec le même défaut que le code, sans secrets.

Après une évolution d’architecture ou un retrait de composant, rechercher les
noms supprimés dans le dépôt et examiner chaque occurrence. Une conception
intermédiaire ne décrit pas automatiquement l’implémentation finale ; les notes
historiques explicitement identifiées peuvent rester. Éviter la paraphrase du
code et les docstrings imposées à tout module : documenter une décision, un
invariant, une contrainte ou un comportement non évident à son endroit utile.
