# Délégation de l’initialisation d’un service Arclith

Ce parcours concerne les projets dont le brief technique retient Arclith.
Skillforge définit le périmètre et les passages de validation ; les skills
publiés par Arclith possèdent les procédures de génération et d’intégration.
Ne pas les réimplémenter dans ce catalogue.

1. Identifier destination, versions, état existant et résultat attendu. Retrouver
   le skill propriétaire réellement disponible et compatible dans la marketplace
   Arclith ; ne pas inventer son nom ou recopier ses commandes ici.
2. Enregistrer les opérations nécessaires et les phases qu’elles produisent
   selon [production-sequences.md](production-sequences.md). Déléguer uniquement
   la phase active. Si un générateur produit aussi des tests ou de la
   documentation, vérifier qu’il permet de les différer ou les séparer. Sinon,
   signaler le blocage avant mutation ; ne pas considérer la génération comme
   une exception implicite à la séparation des phases.
3. Faire exécuter chaque opération par le skill Arclith approprié, recueillir
   les artefacts et preuves, puis obtenir la validation de phase avant la suite.
   La revue commune `review-service-foundation` examine les preuves du socle ;
   les contrôles propres au framework restent délégués à Arclith.
4. Transmettre le socle vérifié au [parcours de fonctionnalité](feature-implementation.md).
   Un échec suit la [boucle de correction](correction-loop.md).

Sur un service existant, préserver les fichiers et appliquer uniquement les
écarts nécessaires. Une procédure ou un blueprint requis manquant bloque les
opérations qui en dépendent ; ne pas fabriquer de remplacement local.
