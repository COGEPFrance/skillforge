---
name: review-architecture
description: "Évaluer la cohérence globale de l’architecture avec le besoin et les décisions du projet, pour un changement ou une revue du projet. Produire une revue sans corriger les fichiers."
---

# review-architecture

## Périmètre

Évaluer la répartition des responsabilités, les frontières et les dépendances au regard du besoin et des choix du projet. L’architecture hexagonale et les microservices sont conditionnels, jamais présupposés.

Identifier le périmètre demandé :

- **Changement** : comprendre l’architecture globale, puis examiner le changement et ses conséquences. Signaler séparément la dette indépendante, sans en faire un motif de refus du changement.
- **Projet** : examiner l’ensemble du périmètre annoncé, y compris les défauts existants, et prioriser les constats. Ne pas présenter une revue partielle comme un audit exhaustif.

Une demande portant sur une PR ou un diff relève du premier périmètre, sauf instruction contraire. Distinguer ce périmètre de la phase de validation, préliminaire ou finale.

## Critères partagés

- [architecture](../../../references/architecture.md)

## Examen

1. Identifier révision, périmètre, phase et besoin attendu. Pour un changement, identifier aussi la base et les fichiers modifiés.
2. Rechercher les décisions applicables dans les instructions du dépôt, le brief technique, la documentation d’architecture, les ADR et les conventions des modules concernés. Relever sources, portée, statut et éventuelles décisions remplacées ; distinguer décisions confirmées, pratiques observées et hypothèses.
3. Construire une vue synthétique des composants, responsabilités, données possédées, contrats et dépendances. Lire au-delà du diff pour comprendre les conséquences, sans élargir les corrections autorisées.
4. Suivre les scénarios représentatifs du besoin : entrées, décisions métier, dépendances, effets durables et sorties. Examiner les dépendances effectives, y compris configuration, appels distants, accès aux données et initialisation ; les imports seuls ne suffisent pas.
5. Appliquer les critères du référentiel : cohésion, couplage, cycles, frontières, assemblage, proportion des abstractions et coût des évolutions concrètes. Approfondir les contraintes hexagonales ou de microservices seulement si le projet les retient.
6. Utiliser les contrôles pertinents disponibles dans un environnement de test isolé et autorisé. Séparer architecture annoncée et observée ; relier chaque défaut à une preuve, une conséquence et un principe de correction.

## Choix du projet

L’absence de documentation n’est pas un blocage automatique : examiner les faits observables, expliciter les hypothèses et limiter le verdict aux garanties démontrées. Si une décision indispensable reste contradictoire ou inconnue, produire `BLOCKED` sur cette décision et préciser ce qui permettrait de reprendre. Ne pas choisir silencieusement une architecture à la place du projet.

Une divergence à une contrainte explicite applicable ou un défaut aux conséquences démontrées peut justifier `FAIL` ; une préférence de style ne suffit pas. Ne pas reproduire une dette uniquement parce qu’elle est fréquente. Pour Python, Pydantic est une dépendance assumée du domaine. Les [tests d’architecture](../../../references/testing.md#contrôles-darchitecture-et-couverture) peuvent protéger les frontières critiques sans imposer un outil particulier.

Cette revue porte sur la place des responsabilités et leurs dépendances. Confier la qualité locale à `review-code`, le détail des composants à leurs revues et l’assemblage en exécution à `review-service-integration`. Signaler les risques nécessitant une revue spécialisée sans en certifier les garanties ni les examiner systématiquement en détail.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Commencer par l’architecture comprise, les sources des règles applicables et les scénarios suivis. Pour chaque défaut, préciser responsabilité ou frontière, emplacement, preuve, effet et principe de correction ; distinguer dette indépendante et suggestions. Pour une revue de projet, hiérarchiser les constats selon leurs conséquences. Ne pas exiger une abstraction sur la seule possibilité d’un besoin futur.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
