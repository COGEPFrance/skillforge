# Éprouver un skill de review

Les instructions et critères maintenus appartiennent à Skillforge. Les projets
synthétiques, requêtes, attentes et tests de comportement sont hébergés dans le
dépôt séparé [skillforge-tests](https://github.com/COGEPFrance/skillforge-tests).
Les contrôles de structure et de liens du
catalogue restent du ressort de Skillforge ; ils ne prouvent pas les décisions
d’un reviewer. Les tests de préparation et de bon fonctionnement des cas restent
avec le dépôt de tests. Aucun moteur d’agents ni CI n’est introduit ici.

## Boucle d’évaluation

1. Définir le contrat du skill : entrées, périmètre, critères, résultat et limites
   avec les autres reviewers. Modifier ses références partagées si nécessaire.
2. Dans le dépôt de tests, préparer un cas avec un défaut démontrable et un cas
   acceptable qui protège contre les faux positifs ; ajouter un prérequis manquant
   lorsque la distinction `BLOCKED` est pertinente. Définir les attentes avant
   l’essai et vérifier que le projet exerce bien le scénario annoncé.
3. Préparer les entrées avec `evaluate.py prepare` en ciblant le catalogue local.
   Conserver l’identité du skill, de ses références, du cas et du runner. Les
   empreintes identifient le contenu réel, même avec des changements non committés.
4. Donner uniquement le dossier `input/` et sa requête au reviewer dans un
   contexte neuf. Garder attentes et anciens rapports hors de son contexte ;
   pour un essai en aveugle, isoler aussi son accès au dépôt et à cet historique.
   Archiver le rapport brut, l’identité de l’essai et les informations du modèle.
5. Comparer le verdict avec `evaluate.py check-report`, puis évaluer les constats :
   défaut et effet démontrés, preuves et emplacements exacts, respect du périmètre,
   absence de défaut inventé ou omis. Un verdict identique avec un mauvais
   raisonnement ne valide pas le skill. Consigner chaque critère d’acceptation.
6. Corriger le skill seulement sur la base d’un écart expliqué. Préparer un nouvel
   essai et rejouer les cas affectés, y compris ceux qui doivent rester acceptés.
   Distinguer erreur du reviewer, ambiguïté du contrat, cas invalide et panne du
   dispositif d’essai avant de conclure.

Le parcours d’évaluation des skills est distinct du parcours de review d’un
projet. Commencer par `review-architecture`, puis élargir aux autres reviewers
selon les dépendances de validation. Un premier lot synthétique ne démontre pas
la fiabilité sur tous les projets ; compléter ensuite avec des changements réels
et des répétitions indépendantes selon les écarts observés.

## Premier lot : architecture

Sept cas couvrent l’hexagonal valide et sa violation, un monolithe modulaire
valide, une documentation absente, des décisions contradictoires et une même
dette examinée en périmètre changement puis projet. Le README du dépôt de tests
porte les commandes d’exécution et les critères restent à côté des cas.
