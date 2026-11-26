---
name: review-code
description: "Examiner correction locale, petites fonctions, responsabilités, entrées/sorties et absence de duplication inutile. Produire une revue du code sans corriger les fichiers."
---

# review-code

## Périmètre

Vérifier que l’implémentation est localement correcte, compréhensible, maintenable et testable. Privilégier les petites fonctions à responsabilité unique, les entrées/sorties limitées et la mutualisation d’un même traitement. Identifier le périmètre : changement ou projet ; pour un changement, distinguer ses défauts de la dette indépendante.

## Critères partagés

Appliquer d’abord la [méthode commune de revue](../../../references/review-method.md)
pour cadrer le dépôt, les sources et la comparaison, même en invocation seule.

- [code-quality](../../../references/code-quality.md)

## Examen

1. Identifier révision, phase, besoin et conventions applicables via la méthode commune. Pour un projet sans diff, examiner l’état fourni sans inventer de base Git.
2. Suivre les entrées jusqu’au résultat : conditions, branches, bornes, valeurs absentes, collections vides et erreurs. Confronter le comportement observé au contrat plutôt qu’au seul succès des outils.
3. Examiner chaque fonction : responsabilité, taille, niveau d’abstraction, paramètres et résultats. Repérer les blocs séparables, les intentions commandées par des booléens et les données sans rapport regroupées dans une même API. Une fonction correcte à l’exécution peut encore présenter un défaut démontré de maintenabilité ou de testabilité.
4. Rechercher les occurrences d’un même traitement dans le périmètre et ses consommateurs : mutualisation attendue ; pour les variantes, examiner spécialisation, héritage ou composition selon le contrat. Vérifier que l’extraction simplifie les responsabilités et ne déplace pas la complexité derrière un objet fourre-tout.
5. Suivre mutations, état partagé entre appels, effets répétés et durée de vie des ressources. Pour le code asynchrone concerné, vérifier attente, propagation des erreurs et nettoyage utiles au chemin examiné.
6. Examiner typage, gestion d’erreurs et contrôles configurés ; utiliser les vérifications pertinentes dans un environnement isolé et autorisé. Distinguer défaut du code, non-conformité explicite et outil indisponible ; ne pas annoncer de résultat non obtenu.

## Contrôles ciblés

Appliquer les [critères de découpage et mutualisation](../../../references/code-quality.md#fonctions-responsabilités-et-mutualisation), puis les [contrôles de typage et erreurs](../../../references/code-quality.md#typage-python-et-contrôles). Les métriques aident à localiser les problèmes ; expliciter responsabilités mélangées, charge de compréhension ou modification répétée plutôt que se contenter d’un slogan. Respecter un seuil bloquant configuré par le projet, sans inventer une limite universelle de lignes ou de paramètres.

Les reviewers de composants approfondissent leurs contrats et les reviewers spécialisés leurs risques. Signaler tout défaut directement démontré dans le périmètre, même s’il relève aussi d’un autre reviewer, sans certifier ses garanties spécialisées.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Relier chaque correction à un emplacement, un scénario ou une difficulté de maintenance démontrée, son effet et un principe de résolution. Distinguer défaut, suggestion et incertitude. Une preuve ou décision indispensable manquante peut donner `BLOCKED` ; la seule absence d’un outil non requis ne suffit pas.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
