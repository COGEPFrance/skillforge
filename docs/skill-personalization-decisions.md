# Arbitrages de personnalisation des skills

Base examinée : `64591f8444339e14a695d1710effd0c687079f9f` (23 novembre 2026).
Périmètre : les 17 fichiers de `references/`, les 48 skills et leurs relais.
`_rules/` n’a pas servi de source et reste inchangé.

Ce journal justifie la répartition ; il n’est pas une nouvelle liste de règles à
charger dans les agents. Les références conservées fournissent des détails
conditionnels et des preuves ; les skills portent les décisions de leur tâche.
Les contrôles déjà utiles ne sont pas ajoutés une seconde fois.

Décision précisée par l’utilisateur : le brief du projet et le brief technique
font autorité pour le besoin et le socle. Arclith rationalise la plupart des
projets Python qui le retiennent, sans s’imposer partout ; il publie ses propres
skills. Les instructions Arclith sont donc conditionnelles. Pydantic reste le choix commun des projets Python et une dépendance assumée
du domaine, avec ou sans Arclith, conformément à la précision de l’utilisateur.
YAML devient une préférence de format laissée au projet.

Légende : **P** instruction de production conservée ou reformulée ; **R** contrôle
ciblé de revue ; **C** détail conditionnel accessible ; **A** prescription retirée
ou slogan remplacé par un critère observable. Une ligne A peut conserver la
partie utile de la règle initiale ; son motif précise ce qui est retiré.
Les numéros sont ceux des puces du fichier à la révision de base ; les extraits
servent au repérage et ne sont pas un second référentiel normatif.


## architecture

| Source initiale | Arbitrage | Destination et valeur ajoutée / portée |
| --- | --- | --- |
| 1. Respecter les frontières domaine, cas d’usage, ports et adapters… | C | [`architecture`](../references/architecture.md) — Frontières utiles dans un profil hexagonal, sans imposer cette architecture aux autres projets. |
| 2. Le domaine ne dépend ni du transport ni du… | P | [`implement-entity`](../skills/dev/implement-entity/SKILL.md) — Évite de coupler le métier aux formats techniques ; Pydantic reste assumé pour les entités des projets Python. |
| 3. Assembler et injecter les dépendances à un point identifié,… | P | [`integrate-service-components`](../skills/dev/integrate-service-components/SKILL.md) — L’assemblage hors métier permet de vérifier les dépendances réellement injectées. |
| 4. Arclith est le socle : examiner ses capacités et… | P | [`implement-lib`](../skills/dev/implement-lib/SKILL.md) — Préserve la réutilisation ; le socle choisi remplace l’obligation universelle Arclith. |
| 5. Donner à chaque microservice une responsabilité métier, des données… | R | [`review-architecture`](../skills/review/review-architecture/SKILL.md) — Pertinent lors d’une frontière de service, pas une obligation de découper tous les projets. |
| 6. Ne pas multiplier les couches, interfaces ou services sans… | P | [`implement-port`](../skills/dev/implement-port/SKILL.md) — Évite interfaces et composants créés uniquement pour satisfaire une séquence. |
| § Preuves attendues | R | [`review-architecture`](../skills/review/review-architecture/SKILL.md) — Conserver la portée des preuves dans le détail conditionnel de ce thème ; ne pas convertir une lecture structurelle ou une vérification partielle en garantie globale. |

## code-quality

| Source initiale | Arbitrage | Destination et valeur ajoutée / portée |
| --- | --- | --- |
| 1. SRP : chaque composant a une responsabilité et une… | A | [`review-code`](../skills/review/review-code/SKILL.md) — Le slogan SRP seul ne tranche rien ; conserver uniquement le constat de responsabilités incompatibles. |
| 2. KISS : choisir la solution la plus simple qui… | A | [`review-code`](../skills/review/review-code/SKILL.md) — KISS seul est subjectif ; examiner la complexité et son effet concret sur le besoin. |
| 3. DRY : mutualiser un concept réellement partagé ; ne… | P | [`implement-lib`](../skills/dev/implement-lib/SKILL.md) — La distinction concept partagé/ressemblance évite une mauvaise mutualisation. |
| 4. SOTA signifie pratiques maintenues, éprouvées et adaptées au besoin,… | A | [`review-code`](../skills/review/review-code/SKILL.md) — Supprimer SOTA comme prescription ; aucune migration ne découle de la nouveauté d’une pratique. |
| 5. Définir des entrées, sorties et erreurs explicitement typées ;… | P | [`implement-port`](../skills/dev/implement-port/SKILL.md) — Types, erreurs et formats aux frontières fixent un contrat vérifiable. |
| 6. Produire des erreurs actionnables, sans masquer un échec en… | P | [`implement-usecase`](../skills/dev/implement-usecase/SKILL.md) — Un faux succès masque les effets partiels ; abstraction et dépendance restent justifiées par le besoin. |
| 7. Limiter le changement au besoin traité. Le refactoring nécessaire… | P | [`refactor`](../skills/dev/refactor/SKILL.md) — Borne les changements nécessaires et oriente la dette indépendante vers le workflow existant. |
| § Vérification | R | [`review-code`](../skills/review/review-code/SKILL.md) — Conserver la portée des preuves dans le détail conditionnel de ce thème ; ne pas convertir une lecture structurelle ou une vérification partielle en garantie globale. |

## compatibility

| Source initiale | Arbitrage | Destination et valeur ajoutée / portée |
| --- | --- | --- |
| 1. Identifier les consommateurs des API, événements, configurations et schémas… | P | [`implement-port`](../skills/dev/implement-port/SKILL.md) — Identifier un consommateur avant de modifier son contrat empêche une rupture silencieuse. |
| 2. Examiner les transitions entre versions, y compris coexistence de… | C | [`compatibility`](../references/compatibility.md) — La coexistence s’examine selon les combinaisons réellement déployées, sans matrice historique infinie. |
| 3. Préserver les contrats requis ou expliciter la rupture, sa… | R | [`review-compatibility`](../skills/review/review-compatibility/SKILL.md) — Une rupture volontaire est acceptable avec migration et coordination explicites. |
| 4. Maîtriser les versions des dépendances ; vérifier la compatibilité… | R | [`review-compatibility`](../skills/review/review-compatibility/SKILL.md) — Vérifier les dépendances concernées avec le socle retenu, sans imposer Arclith. |
| 5. Considérer reprise, rejeu d’anciens messages et retour à une… | C | [`compatibility`](../references/compatibility.md) — Rejeu et retour arrière ne concernent que les garanties promises par le système. |
| § Preuves attendues | R | [`review-compatibility`](../skills/review/review-compatibility/SKILL.md) — Conserver la portée des preuves dans le détail conditionnel de ce thème ; ne pas convertir une lecture structurelle ou une vérification partielle en garantie globale. |

## configuration

| Source initiale | Arbitrage | Destination et valeur ajoutée / portée |
| --- | --- | --- |
| 1. Centraliser les variations utiles et identifiées dans des fichiers… | A | [`implement-configuration`](../skills/dev/implement-configuration/SKILL.md) — Retirer la préférence YAML ; conserver centralisation et format déjà retenu par le projet. |
| 2. Configurer les variations d’environnement et de déploiement ainsi que… | P | [`implement-configuration`](../skills/dev/implement-configuration/SKILL.md) — Ne configurer que les variations opérationnelles identifiées limite les options sans utilisateur. |
| 3. Typer et valider la configuration au démarrage, définir les… | P | [`implement-configuration`](../skills/dev/implement-configuration/SKILL.md) — Type, défaut, validation et priorité évitent les valeurs effectives ambiguës. |
| 4. Éviter les lectures dispersées de fichiers ou de variables… | P | [`implement-configuration`](../skills/dev/implement-configuration/SKILL.md) — L’injection des valeurs validées évite des sources concurrentes dans le métier. |
| 5. Fournir les secrets séparément des fichiers partagés ; ne… | P | [`implement-configuration`](../skills/dev/implement-configuration/SKILL.md) — La séparation des secrets protège fichiers partagés et exemples dès leur production. |
| 6. Ne pas transformer les invariants métier en options désactivables.… | P | [`implement-configuration`](../skills/dev/implement-configuration/SKILL.md) — Une option ne doit pas rendre invalide une règle métier obligatoire. |
| § Preuves attendues | R | [`review-configuration`](../skills/review/review-configuration/SKILL.md) — Conserver la portée des preuves dans le détail conditionnel de ce thème ; ne pas convertir une lecture structurelle ou une vérification partielle en garantie globale. |

## data-consistency

| Source initiale | Arbitrage | Destination et valeur ajoutée / portée |
| --- | --- | --- |
| 1. Identifier les données possédées par le service, les invariants… | P | [`implement-persistence`](../skills/dev/implement-persistence/SKILL.md) — Propriété et transaction fixent où les invariants peuvent être garantis. |
| 2. Garder les représentations de stockage et les conversions dans… | P | [`implement-persistence`](../skills/dev/implement-persistence/SKILL.md) — Le schéma du stockage reste dans l’adapter pour préserver le contrat métier. |
| 3. Définir le comportement en cas de concurrence, mise à… | P | [`implement-persistence`](../skills/dev/implement-persistence/SKILL.md) — Sans politique de conflit, concurrence et mises à jour partielles peuvent perdre des données. |
| 4. Expliciter la cohérence entre écriture durable et publication d’un… | P | [`implement-messaging`](../skills/dev/implement-messaging/SKILL.md) — La fenêtre écriture/publication exige une garantie explicite, pas un pattern obligatoire. |
| 5. Prévoir les migrations et reprises nécessaires ; considérer le… | C | [`data-consistency`](../references/data-consistency.md) — La migration dépend des versions qui lisent et écrivent réellement les données. |
| 6. Distinguer retour arrière du code, réversibilité des données et… | P | [`prepare-deployment`](../skills/delivery/prepare-deployment/SKILL.md) — Un rollback de code ne répare pas implicitement les données ni les effets externes. |
| § Preuves attendues | R | [`review-data-consistency`](../skills/review/review-data-consistency/SKILL.md) — Conserver la portée des preuves dans le détail conditionnel de ce thème ; ne pas convertir une lecture structurelle ou une vérification partielle en garantie globale. |

## delivery

| Source initiale | Arbitrage | Destination et valeur ajoutée / portée |
| --- | --- | --- |
| 1. Organiser des changements cohérents, limités au besoin et revus… | P | [`prepare-commits`](../skills/delivery/prepare-commits/SKILL.md) — Les ensembles cohérents et leurs validations rendent le contenu livrable révisable. |
| 2. Vérifier le contenu exact à committer et publier ;… | P | [`prepare-commits`](../skills/delivery/prepare-commits/SKILL.md) — L’inspection du diff exact évite d’emporter les modifications d’autrui. |
| 3. Utiliser les conventions et outils de versionnement du dépôt… | P | [`prepare-release`](../skills/delivery/prepare-release/SKILL.md) — Suivre le dépôt évite d’inventer une politique de version ou de branches. |
| 4. Préparer les versions, notes de release, migrations, prérequis de… | P | [`prepare-deployment`](../skills/delivery/prepare-deployment/SKILL.md) — Versions, migrations et reprise s’ajoutent selon l’artefact, pas à chaque changement. |
| 5. Distinguer préparation d’un artefact et publication effective. Exécuter commit,… | P | [`prepare-pull-request`](../skills/delivery/prepare-pull-request/SKILL.md) — La publication reste distincte de la préparation et requiert son autorisation propre. |
| 6. Les contrôles applicables et revues sélectionnées doivent être validés… | P | [`prepare-commits`](../skills/delivery/prepare-commits/SKILL.md) — PASS sur les artefacts préparés précède leur livraison ; toute modification invalide les contrôles affectés. |
| § Preuves attendues | R | [`review-delivery`](../skills/review/review-delivery/SKILL.md) — Conserver la portée des preuves dans le détail conditionnel de ce thème ; ne pas convertir une lecture structurelle ou une vérification partielle en garantie globale. |

## documentation

| Source initiale | Arbitrage | Destination et valeur ajoutée / portée |
| --- | --- | --- |
| 1. Définir le public, la tâche et le résultat attendu… | P | [`write-documentation`](../skills/documentation/write-documentation/SKILL.md) — Public, tâche et résultat permettent de sélectionner le contenu utile. |
| 2. Documenter le comportement validé, les contrats, la configuration et… | P | [`write-documentation`](../skills/documentation/write-documentation/SKILL.md) — Relier les garanties aux preuves évite de documenter un comportement imaginaire. |
| 3. Préserver une source de vérité pour chaque information ;… | P | [`write-documentation`](../skills/documentation/write-documentation/SKILL.md) — Une source propriétaire et des renvois évitent les versions contradictoires. |
| 4. Produire ou actualiser la documentation après validation du code… | P | [`update-documentation`](../skills/documentation/update-documentation/SKILL.md) — Le document final suit le comportement validé ; la review attend son artefact. |
| 5. Vérifier liens, exemples et commandes dans leur contexte ;… | P | [`write-documentation`](../skills/documentation/write-documentation/SKILL.md) — Le statut d’exécution des commandes évite de confondre exemple et procédure vérifiée. |
| § Preuves attendues | R | [`review-documentation`](../skills/review/review-documentation/SKILL.md) — Conserver la portée des preuves dans le détail conditionnel de ce thème ; ne pas convertir une lecture structurelle ou une vérification partielle en garantie globale. |

## domain-models

| Source initiale | Arbitrage | Destination et valeur ajoutée / portée |
| --- | --- | --- |
| 1. Utiliser Pydantic pour les entités et distinguer identité métier,… | P | [`implement-entity`](../skills/dev/implement-entity/SKILL.md) — Conserver Pydantic pour les projets Python, ainsi que les distinctions identité/valeur/DTO ; ne pas l’imposer aux autres langages. |
| 2. Définir identité, invariants, transitions autorisées et règles de mutabilité… | P | [`implement-entity`](../skills/dev/implement-entity/SKILL.md) — Identité, mutabilité et transitions définissent ce qu’une modification doit préserver. |
| 3. Exprimer les contraintes locales par les types et contraintes… | P | [`implement-entity`](../skills/dev/implement-entity/SKILL.md) — Contraintes locales et règles croisées n’ont pas les mêmes responsabilités. |
| 4. Préciser conversions acceptées, champs supplémentaires et comportement des mises… | P | [`implement-entity`](../skills/dev/implement-entity/SKILL.md) — Conversions et mises à jour peuvent invalider un modèle pourtant valide à sa création. |
| 5. Ne pas réutiliser automatiquement une entité comme contrat HTTP,… | C | [`domain-models`](../references/domain-models.md) — Le partage d’un modèle externe reste conditionné à la compatibilité réelle des contrats. |
| 6. Justifier toute construction contournant la validation. Pour Pydantic, vérifier… | C | [`domain-models`](../references/domain-models.md) — Le piège des copies et constructions sans validation est utile aux seuls projets/API concernés. |
| § Preuves attendues | R | [`review-domain-models`](../skills/review/review-domain-models/SKILL.md) — Conserver la portée des preuves dans le détail conditionnel de ce thème ; ne pas convertir une lecture structurelle ou une vérification partielle en garantie globale. |

## messaging

| Source initiale | Arbitrage | Destination et valeur ajoutée / portée |
| --- | --- | --- |
| 1. Utiliser les messages lorsqu’ils apportent un bénéfice identifié :… | P | [`implement-messaging`](../skills/dev/implement-messaging/SKILL.md) — Justifier le message évite d’ajouter un système distribué sans bénéfice. |
| 2. Définir les contrats, producteurs, consommateurs et garanties nécessaires ;… | P | [`implement-messaging`](../skills/dev/implement-messaging/SKILL.md) — L’intention commande/événement et les consommateurs fixent le contrat attendu. |
| 3. Préciser doublons, idempotence, ordre utile, concurrence, retries bornés et… | P | [`implement-messaging`](../skills/dev/implement-messaging/SKILL.md) — Doublons, concurrence et fin des tentatives affectent directement les effets métier ; ordre seulement si utile. |
| 4. Positionner les acquittements selon les effets réellement durables. Traiter… | P | [`implement-messaging`](../skills/dev/implement-messaging/SKILL.md) — Un acquittement prématuré peut perdre le traitement ; persistance/publication nécessite une décision explicite. |
| 5. Propager le contexte de corrélation sans secrets ; rendre… | P | [`implement-messaging`](../skills/dev/implement-messaging/SKILL.md) — Corrélation et retard rendent les flux différés exploitables sans exposer de secrets. |
| 6. Réutiliser les mécanismes Arclith et du broker retenu ;… | C | [`messaging`](../references/messaging.md) — Réutiliser le socle retenu ; seule son activation vérifiée établit les garanties, pas son nom. |
| § Preuves attendues | R | [`review-messaging`](../skills/review/review-messaging/SKILL.md) — Conserver la portée des preuves dans le détail conditionnel de ce thème ; ne pas convertir une lecture structurelle ou une vérification partielle en garantie globale. |

## observability

| Source initiale | Arbitrage | Destination et valeur ajoutée / portée |
| --- | --- | --- |
| 1. Utiliser logs structurés, métriques et traces pour expliquer et… | P | [`instrument-service`](../skills/dev/instrument-service/SKILL.md) — Choisir les signaux utiles, sans rendre logs+métriques+traces obligatoires partout. |
| 2. Propager la corrélation et le contexte de trace entre… | P | [`instrument-service`](../skills/dev/instrument-service/SKILL.md) — La corrélation doit survivre aux frontières et reprises réellement concernées. |
| 3. Rendre observables erreurs, retries, abandons, reprises et traitements bloqués… | P | [`instrument-service`](../skills/dev/instrument-service/SKILL.md) — Les erreurs et blocages doivent rester visibles plutôt que réussir en apparence. |
| 4. Observer selon le besoin latence, débit, erreurs, ressources, accumulation… | C | [`observability`](../references/observability.md) — Latence, débit et accumulation sont choisis selon les questions d’exploitation, sans liste imposée. |
| 5. Maîtriser le coût de l’instrumentation et la cardinalité des… | P | [`instrument-service`](../skills/dev/instrument-service/SKILL.md) — Cardinalité, secrets et coût évitent une instrumentation dangereuse ou inutilisable. |
| 6. Réutiliser l’instrumentation Arclith et vérifier les signaux effectivement produits,… | P | [`instrument-service`](../skills/dev/instrument-service/SKILL.md) — Réutiliser le socle retenu puis vérifier les signaux émis plutôt qu’imposer Arclith. |
| § Preuves attendues | R | [`review-observability`](../skills/review/review-observability/SKILL.md) — Conserver la portée des preuves dans le détail conditionnel de ce thème ; ne pas convertir une lecture structurelle ou une vérification partielle en garantie globale. |

## performance

| Source initiale | Arbitrage | Destination et valeur ajoutée / portée |
| --- | --- | --- |
| 1. Définir les volumes et objectifs attendus : latence, débit,… | P | [`measure-performance`](../skills/test/measure-performance/SKILL.md) — Les volumes et objectifs donnent un sens à la mesure ; une exploration sans objectif reste possible. |
| 2. Examiner complexité algorithmique, accès aux données, appels distants, tailles… | R | [`review-performance`](../skills/review/review-performance/SKILL.md) — Complexité, accès, lots et concurrence s’examinent sur les chemins et charges concernés. |
| 3. Mesurer les chemins critiques avant de conclure à un… | P | [`measure-performance`](../skills/test/measure-performance/SKILL.md) — Scénario, données, environnement et versions permettent une comparaison interprétable. |
| 4. Distinguer latence individuelle, débit global et accumulation de travail.… | P | [`measure-performance`](../skills/test/measure-performance/SKILL.md) — Séparer latence, débit et accumulation empêche de déclarer un gain sur le seul choix asynchrone. |
| 5. Examiner saturation, limites et coût d’observabilité ; éviter de… | R | [`review-performance`](../skills/review/review-performance/SKILL.md) — Une optimisation peut déplacer le goulot ou saturer une dépendance ; cibler les facteurs pertinents. |
| § Preuves attendues | R | [`review-performance`](../skills/review/review-performance/SKILL.md) — Conserver la portée des preuves dans le détail conditionnel de ce thème ; ne pas convertir une lecture structurelle ou une vérification partielle en garantie globale. |

## resilience

| Source initiale | Arbitrage | Destination et valeur ajoutée / portée |
| --- | --- | --- |
| 1. Définir timeouts, retries bornés, limites de concurrence et conditions… | P | [`implement-resilience`](../skills/dev/implement-resilience/SKILL.md) — Limites, erreurs temporaires/définitives et abandon s’appliquent aux appels ou traitements exposés. |
| 2. Prendre en compte les défaillances dans le code, au-delà… | P | [`implement-resilience`](../skills/dev/implement-resilience/SKILL.md) — Le framework ne connaît pas les effets partiels métier ; vérifier les garanties requises. |
| 3. Pour chaque traitement concerné, identifier état durable, traitements partiels,… | P | [`implement-resilience`](../skills/dev/implement-resilience/SKILL.md) — État durable et point de reprise sont nécessaires seulement si les effets survivent au processus. |
| 4. Préserver l’idempotence des effets lors des doublons et redémarrages… | P | [`implement-resilience`](../skills/dev/implement-resilience/SKILL.md) — Idempotence et acquittements doivent maîtriser les duplications métier promises par le contrat. |
| 5. Prévoir messages en échec, remise en traitement maîtrisée et… | P | [`implement-resilience`](../skills/dev/implement-resilience/SKILL.md) — Une fin des tentatives et un rejeu maîtrisé empêchent une boucle permanente. |
| 6. Prévoir l’arrêt propre sans supposer qu’il se produira lors… | P | [`implement-resilience`](../skills/dev/implement-resilience/SKILL.md) — Conserver l’arrêt propre, sans en faire une preuve de résistance à la panne brutale. |
| § Preuves attendues | R | [`review-resilience`](../skills/review/review-resilience/SKILL.md) — Conserver la portée des preuves dans le détail conditionnel de ce thème ; ne pas convertir une lecture structurelle ou une vérification partielle en garantie globale. |

## security

| Source initiale | Arbitrage | Destination et valeur ajoutée / portée |
| --- | --- | --- |
| 1. Valider les données aux frontières et appliquer des autorisations… | P | [`implement-usecase`](../skills/dev/implement-usecase/SKILL.md) — Valider les entrées aux frontières et autoriser au bon périmètre métier dès l’implémentation. |
| 2. Limiter les privilèges des composants et des intégrations ;… | P | [`implement-adapter`](../skills/dev/implement-adapter/SKILL.md) — Les privilèges minimaux et la protection des secrets concernent les intégrations effectives. |
| 3. Examiner les entrées non fiables, opérations sensibles et dépendances… | C | [`security`](../references/security.md) — Le filtre des chemins atteignables évite de déclencher un audit général à chaque tâche. |
| 4. Réutiliser les mécanismes Arclith lorsqu’ils répondent au besoin, en… | C | [`security`](../references/security.md) — Réutiliser et vérifier les mécanismes du socle retenu ; Arclith n’est pas universel. |
| 5. Intégrer ces exigences dès la production et les approfondir… | P | [`quality-criteria`](../references/quality-criteria.md) — Maintenir le filtre sécurité en invocation isolée et la revue spécialisée selon le risque. |
| § Preuves attendues | R | [`review-security`](../skills/review/review-security/SKILL.md) — Conserver la portée des preuves dans le détail conditionnel de ce thème ; ne pas convertir une lecture structurelle ou une vérification partielle en garantie globale. |

## service-foundation

| Source initiale | Arbitrage | Destination et valeur ajoutée / portée |
| --- | --- | --- |
| 1. Identifier la destination, la version du socle Arclith et… | P | [`scaffold-arclith-service`](../skills/dev/scaffold-arclith-service/SKILL.md) — Destination et versions évitent une génération dans le mauvais projet ; parcours conditionné au brief. |
| 2. Utiliser les procédures disponibles de la marketplace ou de… | P | [`scaffold-arclith-service`](../skills/dev/scaffold-arclith-service/SKILL.md) — Les skills Arclith possèdent les procédures ; ne pas inventer commandes et options. |
| 3. Scaffold puis application du blueprint sont deux tâches distinctes.… | P | [`apply-arclith-blueprint`](../skills/dev/apply-arclith-blueprint/SKILL.md) — Conserver scaffold puis blueprint ; seul ce parcours demandé bloque si le blueprint est absent/incompatible. |
| 4. Ne pas écraser un service existant : comparer le… | P | [`scaffold-arclith-service`](../skills/dev/scaffold-arclith-service/SKILL.md) — La comparaison d’un existant empêche l’écrasement par une régénération. |
| 5. Vérifier structure, assemblage des dépendances, configuration, démarrage et signaux… | P | [`apply-arclith-blueprint`](../skills/dev/apply-arclith-blueprint/SKILL.md) — La revue de socle vérifie assemblage et démarrage avant fonctionnalité dans ce parcours. |
| 6. Enregistrer versions, blueprint appliqué, fichiers produits et commandes réellement… | P | [`apply-arclith-blueprint`](../skills/dev/apply-arclith-blueprint/SKILL.md) — Versions, fichiers et commandes rendent la génération vérifiable et bornent son périmètre. |
| § Limite de validation | R | [`review-service-foundation`](../skills/review/review-service-foundation/SKILL.md) — Conserver la portée des preuves dans le détail conditionnel de ce thème ; ne pas convertir une lecture structurelle ou une vérification partielle en garantie globale. |

## profiles/python-arclith

| Source initiale | Arbitrage | Destination et valeur ajoutée / portée |
| --- | --- | --- |
| 1. Arclith est le socle des services visés ; Pydantic… | A | [`profiles/python-arclith`](../references/profiles/python-arclith.md) — Conditionner Arclith au brief technique ; conserver Pydantic comme choix commun pour les entités Python, y compris hors Arclith. |
| 2. Identifier dans le projet les versions Python, Arclith, Pydantic,… | C | [`profiles/python-arclith`](../references/profiles/python-arclith.md) — Les API ne se choisissent qu’après identification des versions du projet concerné. |
| 3. Consulter les skills disponibles de la marketplace Arclith et… | C | [`profiles/python-arclith`](../references/profiles/python-arclith.md) — Les skills propres à Arclith portent ses procédures, sans les recopier dans Skillforge. |
| 4. N’utiliser qu’un skill effectivement disponible et adapté. Si la… | C | [`profiles/python-arclith`](../references/profiles/python-arclith.md) — Documentation propriétaire en recours ; seul un prérequis indispensable bloque l’opération dépendante. |
| 5. Réutiliser les mécanismes de configuration, assemblage, messages, runtime et… | C | [`profiles/python-arclith`](../references/profiles/python-arclith.md) — Réutiliser les capacités disponibles répond à l’objectif explicite de ne pas réinventer la roue. |
| 6. Vérifier activation, paramètres et comportement effectif ; une capacité… | C | [`profiles/python-arclith`](../references/profiles/python-arclith.md) — Activation et comportement réel restent à vérifier au niveau de l’application. |
| 7. Une capacité générique propre au framework se traite dans… | C | [`profiles/python-arclith`](../references/profiles/python-arclith.md) — Proposer une évolution au bon propriétaire sans fork silencieux ; pas de blocage universel du projet. |
| § Portée | C | [`profiles/python-arclith`](../references/profiles/python-arclith.md) — Conserver la portée des preuves dans le détail conditionnel de ce thème ; ne pas convertir une lecture structurelle ou une vérification partielle en garantie globale. |

## testing

| Source initiale | Arbitrage | Destination et valeur ajoutée / portée |
| --- | --- | --- |
| 1. Choisir des tests qui vérifient les comportements et risques… | P | [`define-test-strategy`](../skills/test/define-test-strategy/SKILL.md) — Le comportement et le risque sélectionnent les tests plutôt que la structure de l’implémentation. |
| 2. Distinguer tests unitaires, intégration entre composants réels, contrats entre… | P | [`define-test-strategy`](../skills/test/define-test-strategy/SKILL.md) — Chaque niveau prouve une frontière différente ; aucun besoin d’exécuter toutes les catégories. |
| 3. Isoler les dépendances des tests unitaires ; utiliser une… | P | [`write-integration-tests`](../skills/test/write-integration-tests/SKILL.md) — Les garanties de stockage/broker demandent le système réel ; l’unité garde des dépendances isolées. |
| 4. Cibler cas nominaux, erreurs et limites pertinentes, avec des… | P | [`write-unit-tests`](../skills/test/write-unit-tests/SKILL.md) — Les assertions doivent différencier le défaut ; éviter un catalogue de cas sans effet observable. |
| 5. Exécuter les tests existants dès le développement ; ne… | P | [`fix-bug`](../skills/dev/fix-bug/SKILL.md) — Les tests existants restent exécutés pendant le développement, sans attendre une nouvelle suite. |
| 6. Conserver commandes, environnement et résultats observés ; un test… | P | [`write-integration-tests`](../skills/test/write-integration-tests/SKILL.md) — Une dépendance absente et un test non exécuté ne prouvent pas la garantie. |
| 7. Les tests peuvent précéder le code. Dans ce cas,… | P | [`define-test-strategy`](../skills/test/define-test-strategy/SKILL.md) — Tests d’abord : distinguer comportement absent, test invalide et panne d’environnement. |
| § Preuves attendues | R | [`review-tests`](../skills/review/review-tests/SKILL.md) — Conserver la portée des preuves dans le détail conditionnel de ce thème ; ne pas convertir une lecture structurelle ou une vérification partielle en garantie globale. |

## quality-criteria : routage et protocole commun

| Élément initial | Arbitrage et justification |
| --- | --- |
| Référentiel de règles central + tableau des 16 thèmes | Remplacer par un filtre à déclencheurs : les instructions appartiennent aux skills ; un agent ne charge que les détails liés au changement. |
| `_rules/` exclu, cadrage hors catalogue | Conserver l’exclusion de l’historique. Lire les briefs fournis ne crée pas un nouveau parcours de conception. |
| Sécurité obligatoire en invocation dev isolée | Conserver un filtre court pour les entrées, autorisations, privilèges et secrets ; sa revue finale ne remplace pas l’implémentation. |
| Parcourir tout le tableau et consigner les exclusions | Réduire aux risques plausibles ; transmettre décisions, preuves et limites utiles sans matrice exhaustive pour chaque tâche. |
| Arclith base de tous les services et initialisation préalable | Conditionner au brief technique ; garder scaffold → blueprint → revue pour le parcours Arclith. |
| Ordre lib, entités, ports, use cases, adapters, assemblage | Conserver pour le parcours hexagonal, sans composants artificiels ni dépendance imposée aux projets d’une autre architecture. |
| Code/tests, risques, documentation, livraison | Conserver l’ordre des artefacts et de leurs revues ; les tests existants continuent pendant le développement. |
| Sécurité, performance, compatibilité dès production | Conserver selon les effets du changement ; charge et scénarios coûteux ne sont pas exigés systématiquement. |
| Framework insuffisant pour reprise/observabilité | Conserver les preuves applicatives quand ces garanties sont requises, quel que soit le socle choisi. |
| Verdicts, blocage et reprise après correction | Conserver le blocage des étapes dépendantes ; rejouer les validations affectées. Aucune publication autorisée par le seul verdict. |

## Couverture du catalogue

Les 48 skills ont été lus. Les compétences déjà suffisamment précises ne sont
pas réécrites pour augmenter le nombre de fichiers modifiés. `review-adapters`,
`review-configuration`, `review-documentation`, `review-messaging`,
`review-observability`, `review-ports`, `review-resilience`,
`review-service-integration`, `review-tests` et
`prepare-pull-request` conservent leurs contrôles ciblés et relais, avec les
références désormais allégées et une précision commune sur l’environnement de test.
`review-usecases` explicite aussi les autorisations et refus pour éviter un trou
dans le relais de sécurité. Les autres changements rapprochent les décisions
de leur producteur et limitent les prescriptions au profil applicable.

Le parcours PR conserve `review-delivery` après préparation, avant publication
autorisée. Le même principe a été rendu explicite pour les commits et releases.
La documentation et la livraison sont revues sur leurs artefacts préparés.


## Validation des instructions

Les validations structurelles utilisent `quick_validate.py` du skill
`skill-creator` sur les 48 skills, plus un contrôle des liens locaux et de leurs
ancres et `git diff --check`. Elles vérifient le format et la navigation, pas la
qualité des décisions d’un agent.

Une évaluation indépendante a appliqué les instructions à six demandes sans
modifier de projet ni appeler de système externe. C’est une simulation
documentaire, pas un test de service exécuté. L’évaluateur a ouvert ce journal
pendant sa découverte : la première passe ne constitue donc pas un test aveugle.

| Demande simulée | Décision observée |
| --- | --- |
| Conflit concurrent dans un projet FastAPI/SQLAlchemy sans Arclith | Conserver le socle et corriger la concurrence dans l’existant ; demander une preuve sur le stockage concerné. |
| Lecture de dossier limitée à l’organisation, use case invoqué seul | Appliquer l’autorisation pendant l’implémentation, vérifier les refus, transmettre aux revues utiles sans publier de PR. |
| Scaffold Arclith prêt mais blueprint demandé absent | BLOCKED sur le parcours Arclith ; conserver le scaffold, sans inventer de blueprint ni poursuivre la fonctionnalité. |
| Paiement durable puis événement, broker acceptant les doublons | Identifier perte et duplication possibles ; proposer une garantie adaptée sans outbox ni ordre global imposés. |
| PR autorisée mais review-delivery BLOCKED | Conserver les artefacts préparés ; aucune publication avant preuve et PASS ; l’autorisation acquise reste valable à la reprise. |
| Revue finale Pydantic avec copie/update et seuls tests nominaux | BLOCKED sur la preuve des invariants après mise à jour ; FAIL uniquement si un état interdit atteignable est démontré. |

Cette passe a révélé des formulations à corriger : port semblant obligatoire en
persistance, autorisations absentes du relais explicite vers `review-usecases`,
« environnement réel » ambigu pour les tests isolés, portée d’une invocation
isolée et arrêt du parcours séquentiel. Les instructions ont été précisées sur
ces points, puis soumises à une vérification ciblée.

La validation future sur un vrai service devra observer les artefacts produits,
les contrôles réellement exécutés et les relais effectifs. Aucun moteur d’agents
ni mécanisme d’installation n’a été créé dans cette personnalisation.

La vérification ciblée a confirmé les cinq corrections. Deux scénarios
supplémentaires ont été examinés :

| Demande simulée | Décision observée |
| --- | --- |
| Entité Python sans Arclith, brief silencieux sur la validation | Utiliser Pydantic selon le choix commun, sans imposer Arclith ni demander de choisir une bibliothèque. |
| Mesure exploratoire sans objectif chiffré | Accepter la mesure et ses limites, sans certifier de scalabilité ; la comparaison à un objectif est conditionnelle. |

Les deux dernières réserves ont conduit à préciser la description et la
comparaison conditionnelle de `measure-performance`, ainsi que l’arbitrage à
demander si un brief contredit explicitement le choix commun Pydantic. Cette
clarification ne donne aucune autorisation de migrer un projet existant.
