# Arbitrages issus de `_rules/`

Source : `_rules/` à `64591f8444339e14a695d1710effd0c687079f9f`, inchangée.
Le travail précédent fondé sur `references/` a été annulé par `db0d9e8`.
Les références existantes servent de supports de distribution, pas de source
remplaçant `_rules/`.

Les huit fichiers de `_rules/` et les 48 skills ont été examinés. `adefinir.md`
est vide. Les puces vides, exemples de chemins et répétitions typographiques
sont traités avec la règle à laquelle ils se rapportent. Les paragraphes non
listés et le README sont couverts séparément ci-dessous.

Précisions de l’utilisateur conservées : les briefs projet et technique fixent
le besoin et l’architecture ; Arclith est une bibliothèque Python privilégiée
seulement dans les projets qui la retiennent, et publie ses propres skills.
Pydantic est une dépendance assumée des développements Python. La source en
précise la portée : classes de données structurées, internes et techniques
incluses, sans transformer tout objet de comportement en modèle.

**P** : instruction de production ; **R** : contrôle ciblé de revue ; **C** :
détail accessible seulement dans le cas pertinent ; **A** : prescription retirée
ou reformulée parce qu’implicite, rigide ou propre à un projet. Les lignes A
peuvent conserver la préférence utile, sans son interdiction universelle.
Les destinations sont des propriétaires de la décision ; les contrôles déjà
présents ne sont pas dupliqués partout. Ce journal n’est pas à charger à chaque
invocation d’un skill et l’archive n’est pas un prompt à exécuter en bloc.


## dev.md

| Source | Traitement | Destination et justification |
| --- | --- | --- |
| [L5–6](../_rules/dev.md) — Créer une branche dédiée depuis la dernière… | A | [`delivery`](../references/delivery.md) — Ne pas forcer une nouvelle branche depuis origin/main à chaque invocation ; respecter le checkout et la stratégie autorisés. |
| [L7–8](../_rules/dev.md) — Examiner l'architecture, les dépendances et les implémentations… | P | [`quality-criteria`](../references/quality-criteria.md) — Lire les briefs et l’existant oriente le changement sans inventer de choix techniques. |
| [L9–14](../_rules/dev.md) — Les règles de ce document priment sur… | P | [`quality-criteria`](../references/quality-criteria.md) — Ne pas reproduire une dette par simple imitation ; limiter sa correction à la tâche et préserver la compatibilité. |
| [L15–17](../_rules/dev.md) — En cas d'ambiguïté ayant un impact architectural,… | P | [`quality-criteria`](../references/quality-criteria.md) — Faire arbitrer une vraie ambiguïté structurante ; ne pas fabriquer une nouvelle règle universelle pour toute réponse locale. |
| [L18–20](../_rules/dev.md) — Limiter chaque changement aux modifications et refactorings… | P | [`refactor`](../skills/dev/refactor/SKILL.md) — Conserver le périmètre demandé et distinguer dette indépendante. |
| [L21–26](../_rules/dev.md) — Lorsqu'une amélioration importante mais hors périmètre est… | P | [`refactoring-scope`](../workflows/refactoring-scope.md) — Utiliser le suivi existant, sinon upgrade.md ; note dédupliquée et exploitable pour une issue sans publication automatique. |
| [L27–28](../_rules/dev.md) — Après un commentaire de review, rechercher le… | P | [`fix-bug`](../skills/dev/fix-bug/SKILL.md) — Rechercher les occurrences de la même cause dans le périmètre évite une correction de façade. |
| [L29–30](../_rules/dev.md) — Si une suggestion dégrade le typage, l'architecture… | P | [`fix-bug`](../skills/dev/fix-bug/SKILL.md) — Challenger la solution proposée plutôt que l’appliquer si elle dégrade un contrat. |
| [L34–37](../_rules/dev.md) — Respecter les décisions architecturales du projet. Si… | P | [`quality-criteria`](../references/quality-criteria.md) — Le brief technique gouverne l’architecture ; valider une divergence structurante avant exécution. |
| [L38–39](../_rules/dev.md) — Définir clairement la responsabilité de chaque composant… | P | [`implement-usecase`](../skills/dev/implement-usecase/SKILL.md) — Séparer orchestration et processus technique, sans imposer un service pour chaque bloc. |
| [L40–41](../_rules/dev.md) — Respecter la direction des dépendances : le… | P | [`implement-port`](../skills/dev/implement-port/SKILL.md) — Les contrats évitent que le métier dépende d’un client technique. |
| [L42–44](../_rules/dev.md) — Préférer la composition pour réutiliser ou combiner… | P | [`implement-lib`](../skills/dev/implement-lib/SKILL.md) — Composition ou héritage selon une véritable spécialisation, pas une interdiction d’héritage. |
| [L45](../_rules/dev.md) — Concevoir la solution la plus simple qui… | A | [`code-quality`](../references/code-quality.md) — KISS seul n’ajoute pas une décision ; conserver des critères concrets de responsabilité et d’effet. |
| [L46–48](../_rules/dev.md) — Avant de créer une classe, identifier sa… | P | [`implement-entity`](../skills/dev/implement-entity/SKILL.md) — Placer selon le rôle du modèle et le projet, pas selon son premier appelant. |
| [L49–50](../_rules/dev.md) — Une fonction ou méthode possède une responsabilité… | A | [`review-code`](../skills/review/review-code/SKILL.md) — Ne pas dupliquer le slogan SRP ; demander un défaut concret de responsabilité ou de complexité. |
| [L51–55](../_rules/dev.md) — Avant de créer un contrat, un modèle… | P | [`implement-lib`](../skills/dev/implement-lib/SKILL.md) — Même sémantique et vrais consommateurs justifient la réutilisation, pas la seule ressemblance. |
| [L56–60](../_rules/dev.md) — Avant de créer une solution spécifique, privilégier… | P | [`implement-lib`](../skills/dev/implement-lib/SKILL.md) — Examiner bibliothèque standard et versions avant une solution spécifique ; pas de modernisation sans bénéfice. |
| [L64–65](../_rules/dev.md) — En Python, utiliser une `ABC` pour une… | C | [`architecture`](../references/architecture.md) — ABC pour un contrat nominal interne ; ne pas transformer toute famille fermée en hiérarchie. |
| [L66–68](../_rules/dev.md) — Utiliser un `Protocol` lorsqu'un besoin réel de… | C | [`architecture`](../references/architecture.md) — Protocol seulement pour le typage structurel ou la surface étroite réellement requise. |
| [L69–77](../_rules/dev.md) — Conserver une seule chaîne d'héritage Pydantic, y… | P | [`implement-entity`](../skills/dev/implement-entity/SKILL.md) — Conserver la chaîne Pydantic unique ; le détail interdit la recombinaison de bases via mixins. |
| [L78–80](../_rules/dev.md) — Lorsqu'un mixin non-Pydantic répond à un besoin… | C | [`architecture`](../references/architecture.md) — Typer l’hôte d’un mixin non-Pydantic sans Any, faux modèle ou cast large. |
| [L84–85](../_rules/dev.md) — Toute classe qui transporte des données structurées… | P | [`implement-entity`](../skills/dev/implement-entity/SKILL.md) — Choix d’équipe Pydantic conservé pour les classes de données structurées Python, internes et techniques incluses. |
| [L86–87](../_rules/dev.md) — Une entité représente un concept métier doté… | C | [`domain-models`](../references/domain-models.md) — Conserver identité/cycle/invariants ; emplacement entity/ conditionné aux conventions du projet. |
| [L88–92](../_rules/dev.md) — Lorsqu'une mise à jour touche des champs… | P | [`implement-entity`](../skills/dev/implement-entity/SKILL.md) — Valider l’état final avant remplacement et préserver l’existant sur échec ; copie/instance validée ne prouvent rien seules. |
| [L93–94](../_rules/dev.md) — Un DTO transporte des données entre composants… | C | [`domain-models`](../references/domain-models.md) — Conserver le rôle du DTO ; chemin et suffixe sont des conventions du projet, pas une migration générale. |
| [L95–97](../_rules/dev.md) — Choisir selon le besoin entre entité, agrégat,… | P | [`implement-entity`](../skills/dev/implement-entity/SKILL.md) — Distinguer contexte, commande, DTO et entité empêche d’inventer une identité métier. |
| [L98–103](../_rules/dev.md) — Séparer les agrégats métier des contrats Pydantic… | P | [`implement-adapter`](../skills/dev/implement-adapter/SKILL.md) — Séparer les contrats et projeter les seules données nécessaires, sans exposer l’agrégat complet. |
| [L104–105](../_rules/dev.md) — Lorsqu'au moins quatre paramètres représentent un même… | R | [`review-code`](../skills/review/review-code/SKILL.md) — Quatre paramètres est un signal arbitraire ; examiner s’ils portent réellement un concept commun. |
| [L106](../_rules/dev.md) — Remplacer les valeurs métier répétées par un… | R | [`review-code`](../skills/review/review-code/SKILL.md) — Nommer une valeur métier réutilisée quand sa signification le justifie, pas toute constante répétée. |
| [L107–108](../_rules/dev.md) — Éviter les paramètres booléens qui modifient le… | R | [`review-code`](../skills/review/review-code/SKILL.md) — Un booléen n’est pas interdit ; examiner les fonctions qui mélangent plusieurs intentions. |
| [L112–113](../_rules/dev.md) — Un use case représente une intention métier… | P | [`implement-usecase`](../skills/dev/implement-usecase/SKILL.md) — Une intention autonome et des contrats Pydantic typés évitent des entrées/sorties opaques. |
| [L114–116](../_rules/dev.md) — Un use case orchestre des dépendances au… | P | [`implement-usecase`](../skills/dev/implement-usecase/SKILL.md) — Conserver l’orchestration par ports et la frontière avec un processus technique réutilisable. |
| [L117–119](../_rules/dev.md) — Déléguer les boucles de traitement, la pagination,… | P | [`implement-usecase`](../skills/dev/implement-usecase/SKILL.md) — Déléguer pagination/protocole/processus technique ; ne pas externaliser une boucle métier simple ni les autorisations métier. |
| [L120–123](../_rules/dev.md) — Un use case ne déclare pas de… | P | [`implement-usecase`](../skills/dev/implement-usecase/SKILL.md) — Contrats et helpers techniques dans les composants appropriés ; pas de partage forcé d’un helper à usage unique. |
| [L124–127](../_rules/dev.md) — Remettre en question toute méthode privée de… | R | [`review-usecases`](../skills/review/review-usecases/SKILL.md) — Plusieurs dépendances ne prouvent pas un nouveau service ; exiger une responsabilité autonome démontrable. |
| [L128–130](../_rules/dev.md) — Un use case ne lit pas directement… | P | [`implement-usecase`](../skills/dev/implement-usecase/SKILL.md) — Fichiers et formats externes appartiennent à l’adapter, sans interdiction textuelle aveugle d’un nom importé. |
| [L131](../_rules/dev.md) — Un use case ne parse, ne sélectionne… | P | [`implement-usecase`](../skills/dev/implement-usecase/SKILL.md) — La sélection et sérialisation de protocole ne sont pas une décision métier. |
| [L132–133](../_rules/dev.md) — Une variante technique ou un sous-processus devient… | P | [`implement-usecase`](../skills/dev/implement-usecase/SKILL.md) — Une variante technique n’ajoute pas une intention métier autonome. |
| [L137–138](../_rules/dev.md) — Pour une famille fermée, petite et stable,… | C | [`architecture`](../references/architecture.md) — Un petit ensemble fermé peut garder un dispatch exhaustif sans registre. |
| [L139–141](../_rules/dev.md) — Utiliser un registre typé lorsque les stratégies… | C | [`architecture`](../references/architecture.md) — Registre selon l’extensibilité ; clé classe seulement si l’identité de type correspond réellement au contrat. |
| [L142–145](../_rules/dev.md) — Ne pas faire dépendre l'enregistrement de composants… | P | [`integrate-service-components`](../skills/dev/integrate-service-components/SKILL.md) — L’initialisation explicite évite les handlers absents selon l’ordre des imports. |
| [L146–147](../_rules/dev.md) — Typer précisément les configurations, stratégies et retours,… | P | [`integrate-service-components`](../skills/dev/integrate-service-components/SKILL.md) — Typer les stratégies et refuser un choix inconnu plutôt qu’un comportement de repli silencieux. |
| [L148–149](../_rules/dev.md) — Tester que chaque configuration supportée possède un… | P | [`integrate-service-components`](../skills/dev/integrate-service-components/SKILL.md) — La couverture configurations/handlers vérifie une garantie concrète du registre. |
| [L153–155](../_rules/dev.md) — Le core manipule des agrégats, value objects,… | P | [`implement-persistence`](../skills/dev/implement-persistence/SKILL.md) — Garder les objets métier typés ; les documents bruts et formes historiques restent à la frontière. |
| [L156–159](../_rules/dev.md) — Un port de repository retourne un agrégat,… | P | [`implement-port`](../skills/dev/implement-port/SKILL.md) — Interdire dict/Any pour un objet métier ou persistant connu, pas les mappings vraiment dynamiques. |
| [L160–161](../_rules/dev.md) — Seul un adapter de persistance convertit un… | P | [`implement-persistence`](../skills/dev/implement-persistence/SKILL.md) — Les conversions document/modèle appartiennent au composant de persistance. |
| [L162–164](../_rules/dev.md) — Les mappers Mongo vivent dans `adapters/output/` et… | C | [`implement-persistence`](../skills/dev/implement-persistence/SKILL.md) — Cas Mongo gardé conditionnel ; BSON/_id/index restent dans les mappers sans chemin universel. |
| [L165–167](../_rules/dev.md) — Un use case n'appelle jamais `to_document()` ou… | P | [`implement-usecase`](../skills/dev/implement-usecase/SKILL.md) — Le use case demande et sauvegarde l’objet typé, sans appeler la conversion du document. |
| [L168–174](../_rules/dev.md) — Dans les règles métier, ne pas modifier… | P | [`implement-entity`](../skills/dev/implement-entity/SKILL.md) — La mise à jour métier nommée contrôle les champs et valide atomiquement les invariants. |
| [L175–178](../_rules/dev.md) — Autoriser `model_dump()` uniquement à une frontière d'adapter,… | C | [`domain-models`](../references/domain-models.md) — Pas de dump comme mutation ; projection validée entre contrats, et logs limités aux champs non sensibles. |
| [L182–183](../_rules/dev.md) — Préserver un typage précis : éviter les… | P | [`implement-port`](../skills/dev/implement-port/SKILL.md) — Contrats précis ; détail Python interdit les contournements artificiels du type checker. |
| [L184–186](../_rules/dev.md) — Interdire `# mypy: ignore-errors` et toute désactivation… | C | [`code-quality`](../references/code-quality.md) — Conserver l’interdiction des suppressions globales Mypy et les exceptions locales codées/justifiées. |
| [L187–188](../_rules/dev.md) — Produire des erreurs explicites, précises et actionnables.… | C | [`code-quality`](../references/code-quality.md) — Capturer les erreurs attendues sans masquer la cause ; ne pas interdire tout catch large de frontière si réémission/erreur explicite. |
| [L189–191](../_rules/dev.md) — Une erreur du traitement principal ne doit… | P | [`implement-usecase`](../skills/dev/implement-usecase/SKILL.md) — L’échec principal conserve une erreur explicite et la réponse standard existante. |
| [L192–195](../_rules/dev.md) — Un effet secondaire explicitement qualifié de `best… | C | [`code-quality`](../references/code-quality.md) — Best effort seulement si le contrat rend l’effet optionnel après succès ; éligibilité unique, visibilité et tests. |
| [L199–200](../_rules/dev.md) — Utiliser des noms précis qui expriment l'intention… | A | [`review-code`](../skills/review/review-code/SKILL.md) — Verbe pour toute méthode et règles lexicales systématiques sont implicites ; garder le vocabulaire métier et signaler une ambiguïté concrète. |
| [L201–202](../_rules/dev.md) — Employer le même vocabulaire dans le code,… | P | [`write-documentation`](../skills/documentation/write-documentation/SKILL.md) — Un vocabulaire commun code/tests/doc évite des contrats perçus différemment. |
| [L203–204](../_rules/dev.md) — Préférer un nom explicite, même plus long.… | A | [`review-code`](../skills/review/review-code/SKILL.md) — La longueur d’un nom ne prouve pas une responsabilité ; ne pas en faire un contrôle mécanique. |
| [L205–207](../_rules/dev.md) — Documenter uniquement une décision, un invariant, un… | P | [`write-documentation`](../skills/documentation/write-documentation/SKILL.md) — Documenter les décisions et contraintes non évidentes plutôt que paraphraser et dupliquer. |
| [L208](../_rules/dev.md) — Une docstring de module résume sa responsabilité… | A | [`documentation`](../references/documentation.md) — Pas de docstring obligatoire à chaque module ; documenter quand l’information aide. |
| [L212–213](../_rules/dev.md) — Évaluer la complexité de chaque fonction, pas… | R | [`review-code`](../skills/review/review-code/SKILL.md) — Complexité par fonction conservée ; 10 devient un repère, seuil bloquant uniquement si configuré par le projet. |
| [L214–215](../_rules/dev.md) — Réduire aussi la complexité cognitive et limiter… | R | [`review-code`](../skills/review/review-code/SKILL.md) — Deux niveaux est un repère de lecture, pas une obligation de fragmenter la logique. |
| [L216–217](../_rules/dev.md) — Refactorer selon les responsabilités, jamais pour tromper… | P | [`refactor`](../skills/dev/refactor/SKILL.md) — Extraire selon la responsabilité, sans micro-fonctions destinées à tromper une métrique. |
| [L218–219](../_rules/dev.md) — Évaluer la complexité algorithmique selon le volume… | R | [`review-performance`](../skills/review/review-performance/SKILL.md) — Examiner volumes et chemins critiques ; pas de benchmark systématique. |
| [L223](../_rules/dev.md) — L'arborescence des tests unitaires reflète celle des… | C | [`testing`](../references/testing.md) — Respecter l’organisation de tests du projet, sans migration universelle vers une arborescence donnée. |
| [L224–226](../_rules/dev.md) — Protéger par un test d'architecture toute frontière… | C | [`testing`](../references/testing.md) — Automatiser les frontières critiques quand un contrôle stable apporte une preuve utile. |
| [L227–228](../_rules/dev.md) — Dans `core/use_cases/`, interdire notamment les dépendances directes… | R | [`review-usecases`](../skills/review/review-usecases/SKILL.md) — Vérifier les accès et responsabilités interdits ; pas de liste noire d’imports indépendante de leur usage. |
| [L229–230](../_rules/dev.md) — Interdire les dataclasses dans `core/` et `adapters/`… | C | [`testing`](../references/testing.md) — Conserver Pydantic pour les classes de données ; vérifier les frontières utiles sans imposer Ruff/AST partout. |

## review.md

| Source | Traitement | Destination et justification |
| --- | --- | --- |
| [L1](../_rules/review.md) — Comparer les pratiques existantes aux règles.… | R | [`review-code`](../skills/review/review-code/SKILL.md) — Comparer aux choix applicables et au besoin, pas à toute l’archive brute. |
| [L2](../_rules/review.md) — Ne pas propager une mauvaise architecture dans… | R | [`review-architecture`](../skills/review/review-architecture/SKILL.md) — Ne pas imiter une dette ; limiter la correction au changement. |
| [L3](../_rules/review.md) — Vérifier les responsabilités et la direction des… | R | [`review-architecture`](../skills/review/review-architecture/SKILL.md) — Direction des dépendances et responsabilités déjà couvertes, sans copie dans toutes les revues. |
| [L4](../_rules/review.md) — Rechercher les noms ambigus.… | R | [`review-code`](../skills/review/review-code/SKILL.md) — Relever une ambiguïté qui affecte la compréhension d’un contrat, pas une préférence de nom. |
| [L5](../_rules/review.md) — Rechercher duplication, couplage et abstractions inutiles.… | R | [`review-lib`](../skills/review/review-lib/SKILL.md) — Examiner concept partagé, couplage et nécessité de l’abstraction. |
| [L6](../_rules/review.md) — Vérifier le typage et la gestion des… | R | [`review-code`](../skills/review/review-code/SKILL.md) — Contrôler types et erreurs avec les outils du projet. |
| [L7](../_rules/review.md) — Examiner la complexité fonction par fonction.… | R | [`review-code`](../skills/review/review-code/SKILL.md) — Examiner chaque fonction touchée, pas une moyenne de module. |
| [L8](../_rules/review.md) — Vérifier les cas limites et les risques… | R | [`review-performance`](../skills/review/review-performance/SKILL.md) — Cas limites et risques de charge dans la revue concernée, sans benchmark obligatoire pour toute PR. |
| [L9–10](../_rules/review.md) — Exécuter les outils existants du projet :… | R | [`review-delivery`](../skills/review/review-delivery/SKILL.md) — Vérifier les contrôles applicables réellement exécutés ; pas toute la batterie dans chaque agent spécialisé. |
| [L11](../_rules/review.md) — Vérifier le résultat réel, pas seulement le… | R | [`review-tests`](../skills/review/review-tests/SKILL.md) — Les résultats doivent prouver le comportement visé, pas seulement un code de sortie nul. |
| [L12–13](../_rules/review.md) — Vérifier que chaque nouveau contrat, abstraction ou… | R | [`review-architecture`](../skills/review/review-architecture/SKILL.md) — La conformité concerne les décisions applicables du brief, pas une architecture imposée à tous. |
| [L14–15](../_rules/review.md) — Vérifier qu’aucun use case ne contient un… | R | [`review-usecases`](../skills/review/review-usecases/SKILL.md) — Vérifier le placement des contrats et détails techniques sans extraction artificielle de toute méthode privée. |
| [L16–18](../_rules/review.md) — Toute contrainte portant sur un seul champ… | P | [`implement-entity`](../skills/dev/implement-entity/SKILL.md) — Les contraintes locales déclaratives sont traitées dès la production, puis revues. |
| [L19–20](../_rules/review.md) — Réserver `field_validator` aux transformations qui ne peuvent… | C | [`domain-models`](../references/domain-models.md) — field_validator pour le cas local non déclaratif ; éviter d’y dupliquer Field. |
| [L21–22](../_rules/review.md) — Réserver `model_validator` aux invariants qui portent réellement… | C | [`domain-models`](../references/domain-models.md) — model_validator pour un véritable invariant croisé. |
| [L23–24](../_rules/review.md) — Ne pas recopier dans un `model_validator` une… | C | [`domain-models`](../references/domain-models.md) — La même validation locale ne se répète pas au niveau du modèle. |
| [L25–27](../_rules/review.md) — Ne jamais remplacer mécaniquement `dataclasses.replace()` par… | C | [`domain-models`](../references/domain-models.md) — Une copie avec update ne suffit pas à garantir les invariants ; vérifier le chemin réel. |
| [L28](../_rules/review.md) — Interdire `# mypy: ignore-errors` au niveau d'un… | C | [`code-quality`](../references/code-quality.md) — Interdiction locale déjà portée par le détail typage, sans doublon normatif. |
| [L29](../_rules/review.md) — Interdire les suppressions de typage globales destinées… | C | [`code-quality`](../references/code-quality.md) — Pas de suppression globale de typage pour rendre Mypy silencieux. |
| [L30–34](../_rules/review.md) — Les fichiers ajoutés ou modifiés par une… | R | [`review-code`](../skills/review/review-code/SKILL.md) — Contrôler le format touché avec l’outil/version du projet ; Ruff si retenu. |
| [L35–36](../_rules/review.md) — La CI ou la cible `make lint`… | R | [`review-delivery`](../skills/review/review-delivery/SKILL.md) — Signaler une CI omettant le format pertinent, sans modifier une pipeline hors périmètre. |
| [L37–41](../_rules/review.md) — Une classe de champs Pydantic partagée est… | C | [`domain-models`](../references/domain-models.md) — Contrat partagé et chaîne unique conservés ; suffixe Fields et compte exact ne deviennent pas des critères universels. |
| [L42–43](../_rules/review.md) — Ne pas nommer `*Mixin` une base de… | C | [`domain-models`](../references/domain-models.md) — Nommer le rôle pour éviter un faux mixin ; suffixe selon les conventions du projet. |
| [L44–49](../_rules/review.md) — Avant de créer un `Mixin`, l’agent doit… | C | [`architecture`](../references/architecture.md) — Conserver justification et alternatives du mixin, sans formulaire obligatoire dans toutes les tâches. |

## refacto.md

| Source | Traitement | Destination et justification |
| --- | --- | --- |
| [L1–5](../_rules/refacto.md) — Lorsqu’un comportement est utilisé par plusieurs agrégats… | P | [`refactor`](../skills/dev/refactor/SKILL.md) — Fonction stateless ou service selon collaborateurs ; ABC seulement si contrat nominal réel. |
| [L6–10](../_rules/refacto.md) — Conserver une sous-classe sans ajout de comportement… | P | [`refactor`](../skills/dev/refactor/SKILL.md) — Une sous-classe vide peut préserver identité publique, métier ou schéma ; vérifier avant suppression. |
| [L11–14](../_rules/refacto.md) — Ne pas fusionner des modèles sur la… | P | [`implement-entity`](../skills/dev/implement-entity/SKILL.md) — Ne pas fusionner des modèles aux champs semblables et cycles/contraintes différents. |
| [L15–19](../_rules/refacto.md) — Conserver dans l'agrégat les comportements qui relèvent… | P | [`refactor`](../skills/dev/refactor/SKILL.md) — Garder invariants dans l’agrégat et détails privés ; pas de mixin de convenance pour la taille. |

## sdd.md

| Source | Traitement | Destination et justification |
| --- | --- | --- |
| [L1](../_rules/sdd.md) — Comprendre le besoin, les critères d’acceptation et… | P | [`quality-criteria`](../references/quality-criteria.md) — Lire les critères du brief existant ; ne pas créer de thème conception ou SDD hors catalogue. |
| [L2](../_rules/sdd.md) — Identifier les invariants, cas limites et comportements… | P | [`define-test-strategy`](../skills/test/define-test-strategy/SKILL.md) — Relier invariants, erreurs et limites aux scénarios utiles. |
| [L3–4](../_rules/sdd.md) — Ne pas appliquer mécaniquement une suggestion :… | P | [`fix-bug`](../skills/dev/fix-bug/SKILL.md) — Challenger une suggestion et choisir une correction adaptée plutôt qu’obéir mécaniquement. |

## doc.md

| Source | Traitement | Destination et justification |
| --- | --- | --- |
| [L1–9](../_rules/doc.md) — Lorsqu’une fonctionnalité ajoute, supprime ou remplace une… | P | [`implement-configuration`](../skills/dev/implement-configuration/SKILL.md) — Contrôle de la chaîne option→consommateur→exemples→doc→tests ; chemin settings spécifique retiré, répétition ligne 7 dédupliquée. |

## test.md

| Source | Traitement | Destination et justification |
| --- | --- | --- |
| [L7–8](../_rules/test.md) — Utilise `unittest.mock` : `Mock`, `MagicMock`, `AsyncMock`,… | C | [`testing`](../references/testing.md) — unittest.mock pour les TU Python, sans l’imposer aux tests d’intégration. |
| [L9–11](../_rules/test.md) — Lorsque l'interface est disponible, privilégie… | C | [`testing`](../references/testing.md) — autospec contraint si l’interface le permet pour détecter les écarts de contrat. |
| [L12](../_rules/test.md) — Utilise `AsyncMock` pour les méthodes asynchrones.… | C | [`testing`](../references/testing.md) — AsyncMock pour les opérations asynchrones seulement. |
| [L13–14](../_rules/test.md) — Instancie réellement le composant testé et exécute… | P | [`write-unit-tests`](../skills/test/write-unit-tests/SKILL.md) — Ne pas simuler la logique dont le comportement doit être vérifié. |
| [L15–16](../_rules/test.md) — Utilise des objets réels pour les données,… | P | [`write-unit-tests`](../skills/test/write-unit-tests/SKILL.md) — Données et modèles réels conservent les contraintes de validation. |
| [L17–19](../_rules/test.md) — Configure uniquement les comportements nécessaires au scénario… | C | [`testing`](../references/testing.md) — Configurer seulement le scénario pour garder les tests lisibles et discriminants. |
| [L20–22](../_rules/test.md) — Privilégie l'injection des mocks dans le composant… | C | [`testing`](../references/testing.md) — Injection prioritaire et patch au point d’usage évitent de patcher le mauvais symbole. |
| [L23–24](../_rules/test.md) — N'utilise pas les fakes de `tests/test_helpers.py` pour… | A | [`testing`](../references/testing.md) — Retirer l’interdiction universelle des fakes et le chemin local ; mocks privilégiés pour les nouveaux TU. |
| [L34](../_rules/test.md) — Applique cette migration aux tests concernés par… | C | [`testing`](../references/testing.md) — Pas de migration déclenchée par la seule détection ; si nécessaire/demandée, rester dans les tests de la tâche. |
| [L35–36](../_rules/test.md) — Utilise `AsyncMock` uniquement pour les méthodes asynchrones… | C | [`testing`](../references/testing.md) — La méthode testée reste réelle, même asynchrone ; préciser les assertions d’attente. |
| [L37–39](../_rules/test.md) — Configure les comportements nécessaires avec `return_value`… | C | [`testing`](../references/testing.md) — Préserver scénarios/garanties lors d’une migration utile, pas transcrire mécaniquement les interactions. |
| [L40–41](../_rules/test.md) — Remplace les assertions propres au fake par… | P | [`write-unit-tests`](../skills/test/write-unit-tests/SKILL.md) — Résultats observables et interactions contractuelles, sans reproduire l’API interne du fake. |
| [L42–45](../_rules/test.md) — Adapte les fixtures concernées. Avant de modifier… | C | [`testing`](../references/testing.md) — Vérifier tous les usages d’une fixture partagée et isoler les réglages divergents. |
| [L46–47](../_rules/test.md) — Ne remplace pas les objets réels servant… | P | [`write-unit-tests`](../skills/test/write-unit-tests/SKILL.md) — Conserver les objets de données et le composant réels lors d’une migration. |
| [L48](../_rules/test.md) — Ne modifie pas le code de production… | P | [`write-unit-tests`](../skills/test/write-unit-tests/SKILL.md) — La migration de doubles ne doit pas modifier la production ; transmettre un défaut à son propriétaire. |
| [L58–59](../_rules/test.md) — Avant d'utiliser une fixture, vérifie sa définition… | C | [`testing`](../references/testing.md) — Lire le type et les garanties d’une fixture avant réemploi. |
| [L60–61](../_rules/test.md) — Réutilise les fixtures existantes lorsqu'elles fournissent des… | C | [`testing`](../references/testing.md) — Réutiliser un mock adapté sans copier une configuration partagée. |
| [L62–63](../_rules/test.md) — Les fixtures fournissant des fakes ne doivent… | A | [`testing`](../references/testing.md) — La préférence mocks ne justifie pas une interdiction globale de fixtures de fakes utiles. |
| [L64–65](../_rules/test.md) — Lorsqu'une fixture adaptée existe, injecte-la par paramètre… | C | [`testing`](../references/testing.md) — Les fixtures pytest sont injectées par paramètre, pas appelées directement. |
| [L66–67](../_rules/test.md) — Chaque test doit disposer de mocks indépendants.… | C | [`testing`](../references/testing.md) — État indépendant par test, function privilégié pour les mocks ; pas de scope imposé aux infrastructures. |
| [L68–73](../_rules/test.md) — Les variables d'environnement MDM sont automatiquement configurées… | A | [`testing`](../references/testing.md) — Variables MDM et setup_test_env_vars appartiennent à un projet particulier ; ne pas les supposer ailleurs. |
| [L79–80](../_rules/test.md) — Avant de créer une nouvelle fixture dans… | C | [`testing`](../references/testing.md) — Rechercher une fixture adaptée avant de créer un nouvel équivalent. |
| [L81–83](../_rules/test.md) — Pour une configuration propre à un scénario,… | C | [`testing`](../references/testing.md) — Les réglages spécifiques au scénario restent dans le test. |
| [L84–85](../_rules/test.md) — Si aucune fixture adaptée n'existe et que… | C | [`testing`](../references/testing.md) — Mock local si le besoin est local ; pas de fixture partagée artificielle. |
| [L86–87](../_rules/test.md) — Ne modifie jamais la définition d'une fixture… | C | [`testing`](../references/testing.md) — Garder une fixture commune générique pour ne pas casser d’autres usages. |
| [L88–96](../_rules/test.md) — Ne transforme pas les fixtures de fakes… | C | [`testing`](../references/testing.md) — Toute évolution de fixture partagée nécessite l’examen de ses usages. |
| [L97](../_rules/test.md) — La fixture contient uniquement la configuration commune.… | C | [`testing`](../references/testing.md) — Conserver uniquement la configuration commune dans une fixture. |
| [L98](../_rules/test.md) — Un mock utilisé uniquement dans un fichier… | C | [`testing`](../references/testing.md) — Un usage local ne nécessite pas de conftest global. |
| [L99–103](../_rules/test.md) — Tout mock d'une même dépendance nécessaire dans… | A | [`testing`](../references/testing.md) — Retirer le seuil mécanique de deux fichiers et la racine imposée ; partager un vrai réglage commun. |
| [L120–125](../_rules/test.md) — Nommage : `test_<ce_qui_est_testé>_<contexte>`.… | C | [`testing`](../references/testing.md) — Nom comportement/contexte conservé ; commentaires utiles, sans police universelle des séparateurs. |
| [L126–127](../_rules/test.md) — Pour les tests asynchrones, utilise `@pytest.mark.asyncio`… | C | [`testing`](../references/testing.md) — Utiliser le mode async du projet, pas imposer pytest-asyncio à tous les projets Python. |
| [L128–129](../_rules/test.md) — Pour vérifier les appels asynchrones, utilise les… | C | [`testing`](../references/testing.md) — Vérifier l’attente effective quand elle fait partie du contrat. |
| [L130–131](../_rules/test.md) — Objectif de couverture : 80 % minimum,… | A | [`testing`](../references/testing.md) — 80/90 % ne sont pas universels ; suivre la quality gate réelle et les comportements à risque. |
| [L137](../_rules/test.md) — `dependency_container.py`… | A | [`testing`](../references/testing.md) — Ne pas exclure automatiquement un conteneur dont l’assemblage peut avoir un comportement important. |
| [L138](../_rules/test.md) — Les entités… | A | [`testing`](../references/testing.md) — Ne pas exclure automatiquement les entités ; leurs invariants doivent être testés. |
| [L139–143](../_rules/test.md) — Les DTO… | A | [`testing`](../references/testing.md) — Ne pas exclure automatiquement les DTO porteurs de validation significative. |
| [L149–151](../_rules/test.md) — Avant d'écrire les tests d'un fichier, analyse… | P | [`write-unit-tests`](../skills/test/write-unit-tests/SKILL.md) — Consulter les tests existants pour éviter doublons et incohérences utiles au contexte. |
| [L152–154](../_rules/test.md) — Ne génère pas de tests triviaux ou… | P | [`write-unit-tests`](../skills/test/write-unit-tests/SKILL.md) — Pas de test nominal trivial sans comportement à prouver. |
| [L155–157](../_rules/test.md) — Chaque test doit vérifier les résultats, erreurs… | P | [`write-unit-tests`](../skills/test/write-unit-tests/SKILL.md) — Assertions sur le comportement public et ses effets. |
| [L158–160](../_rules/test.md) — Vérifie les interactions uniquement lorsqu'elles font partie… | P | [`write-unit-tests`](../skills/test/write-unit-tests/SKILL.md) — Interactions seulement lorsqu’elles participent au contrat attendu. |
| [L161–163](../_rules/test.md) — Évite les assertions sur les détails internes,… | P | [`write-unit-tests`](../skills/test/write-unit-tests/SKILL.md) — Pas de couplage aux méthodes privées ni à l’ordre sans exigence métier. |
| [L164–165](../_rules/test.md) — Un test ne doit pas seulement vérifier… | P | [`write-unit-tests`](../skills/test/write-unit-tests/SKILL.md) — Un mock qui renvoie sa valeur configurée ne prouve pas la logique du composant. |
| [L166–167](../_rules/test.md) — Ne duplique pas les tests existants. Si… | P | [`write-unit-tests`](../skills/test/write-unit-tests/SKILL.md) — Compléter une couverture existante plutôt que recopier le même scénario. |
| [L168](../_rules/test.md) — Priorise les use cases et leurs règles… | A | [`define-test-strategy`](../skills/test/define-test-strategy/SKILL.md) — Prioriser les risques, pas les use cases avant tous les adapters quels que soient leurs enjeux. |
| [L169](../_rules/test.md) — Couvre les cas nominaux, les erreurs et… | P | [`define-test-strategy`](../skills/test/define-test-strategy/SKILL.md) — Nominal, erreurs et limites selon le comportement réellement modifié. |
| [L170–171](../_rules/test.md) — Pour les entités, cible uniquement les règles… | P | [`write-unit-tests`](../skills/test/write-unit-tests/SKILL.md) — Pour les entités, cibler les validations et règles significatives plutôt que des tests de champs triviaux. |
| [L172–173](../_rules/test.md) — Les TU ne doivent effectuer aucun appel… | P | [`write-unit-tests`](../skills/test/write-unit-tests/SKILL.md) — TU isolés de réseau/infrastructure/délais réels ; les garanties de systèmes réels vont en intégration. |
| [L174–178](../_rules/test.md) — Tester explicitement les invariants métier. Pour chaque… | P | [`implement-entity`](../skills/dev/implement-entity/SKILL.md) — Vérifier création, transitions, limites et état inchangé après refus de mise à jour. |
| [L179](../_rules/test.md) — Ajouter un test de non-régression pour chaque… | P | [`fix-bug`](../skills/dev/fix-bug/SKILL.md) — Conserver un scénario de non-régression qui détecte la cause ; expliciter si sa réalisation relève de la phase suivante. |
| [L180–181](../_rules/test.md) — Privilégie des mocks simples, configurés uniquement pour… | C | [`testing`](../references/testing.md) — Mocks simples et réglages limités au scénario, dédupliqués avec le début du fichier. |
| [L182](../_rules/test.md) — Préserver les comportements existants sauf changement explicitement… | P | [`refactor`](../skills/dev/refactor/SKILL.md) — Préserver les comportements sauf changement demandé, y compris lors d’une migration de tests. |
| [L188–194](../_rules/test.md) — Définir explicitement le périmètre des sources et… | C | [`testing`](../references/testing.md) — Périmètre de sources reproductible, nouvelles sources incluses, résidus locaux exclus. |
| [L200](../_rules/test.md) — N'écris que des fichiers de test Python.… | A | [`write-unit-tests`](../skills/test/write-unit-tests/SKILL.md) — Limiter ce skill aux tests et supports requis ; les autres langages et artefacts de preuve ne sont pas interdits au catalogue. |
| [L201](../_rules/test.md) — Ne modifie pas le code de production.… | P | [`write-unit-tests`](../skills/test/write-unit-tests/SKILL.md) — Le producteur de tests ne corrige pas silencieusement la production. |
| [L202](../_rules/test.md) — N'écris aucun rapport ou explication.… | A | [`write-unit-tests`](../skills/test/write-unit-tests/SKILL.md) — Un bref relais de résultats est nécessaire aux agents autonomes ; pas d’interdiction de rapport. |
| [L203](../_rules/test.md) — N'exécute aucune commande terminal.… | A | [`write-unit-tests`](../skills/test/write-unit-tests/SKILL.md) — L’interdiction terminal contredit la preuve exécutée ; autoriser les contrôles isolés pertinents. |

## Paragraphes, exemples et éléments non listés

| Source | Arbitrage |
| --- | --- |
| `test.md` L3–5 | Préférence mocks pour les dépendances internes et externes des nouveaux TU conservée ; la logique et les données testées restent réelles. |
| `test.md` L29–32 | Migration automatique au simple constat d’un fake retirée : risque de hors-périmètre et perte d’un double utile. Migration ciblée si nécessaire ou explicitement demandée. |
| `test.md` L53–56 | Injection des fixtures conservée dans le détail Python ; noms dossier/MDM restent des exemples locaux, pas des dépendances requises. |
| `test.md` L71–73 | Interdiction des conftest imbriqués retirée : pytest permet une portée locale utile ; organisation du projet et partage réel priment. |
| `test.md` L91–103 | Exemples return_value/side_effect conservés sous forme de consigne courte, sans exemples métier imposés ; partage selon configuration réellement commune. |
| `test.md` L109–114 et `dev.md` L223 | Arborescence miroir utilisable si retenue par le projet ; pas de déplacement automatique vers tests/units. |
| `test.md` L141–143 | Tester les validations significatives même si un projet exclut leur code du pourcentage de couverture. |
| `doc.md` L7 | Doublon de la sous-condition de tests dédupliqué, sans perte de la vérification. |
| `doc.md` L8 | Conserver la cohérence variable déclarée/utilisée/documentée et défauts identiques, dans implement-configuration, update-documentation et leurs revues. |
| `doc.md` L9 | Recherche des noms supprimés conservée comme contrôle de fin de changement ; vérifier les occurrences plutôt que supprimer toute mention historique. |
| Puces vides finales de dev/doc/review/sdd | Aucun contenu normatif à intégrer. |
| `adefinir.md` | Fichier vide, aucune règle inventée. |

## README de `_rules/` : décisions du catalogue

| Section source | Traitement |
| --- | --- |
| Le principe, Commun à l’équipe/spécifique au projet | Conserver les tâches spécialisées génériques et les procédures de projet dans leurs propres skills. Les briefs précisent le contexte ; les métiers locaux ne deviennent pas des règles globales. |
| Arclith socle de tous les services | Corriger selon la précision utilisateur : seulement si choisi par le brief technique, avec ses propres skills. Le choix Pydantic pour Python est conservé. |
| Production et revue | Garder les revues par résultat/risque et les exigences dès production, sans imposer tous les contrôles à chaque tâche. |
| Utilisation future par des agents | Conserver séquence, PASS, blocage FAIL/BLOCKED et reprise des validations affectées ; une revue impossible n’est pas un succès. |
| Catalogue, schéma des 48 skills | Garder les 48 compétences existantes. Diagnostic et conception restent hors catalogue ; ne pas créer un moteur d’agents ni un installateur. |
| Références communes et anciennes règles non incorporées | Mettre à jour le README courant et le routage pour cette incorporation sélective ; garder l’archive intacte et les détails conditionnels accessibles. |
| Initialiser avant implémentation | Conserver scaffold → blueprint compatible → revue du socle avant fonctionnalité dans le parcours Arclith. Blueprint manquant bloque ce parcours, pas tous les projets. |
| Implémentation par composants | Garder l’ordre des dépendances et les revues séquentielles sélectionnées ; réutiliser les composants existants sans créer une couche pour remplir l’étape. |
| Capacité générique manquante d’Arclith | Examiner/réutiliser le socle choisi ; évolution propre à Arclith à son propriétaire. Seules les garanties qui en dépendent bloquent, sans modification externe implicite. |
| Refactoring indépendant avec issue | Réconcilier avec dev.md : suivi existant, sinon note upgrade.md préparant une issue ; publication seulement si autorisée. |
| Exemple code/tests/risques/doc/delivery | Préserver préparation avant revue documentaire/delivery, puis publication après PASS et autorisation. Invocation isolée distincte du parcours complet. |
| Faire évoluer le catalogue | Maintenir des méthodes versionnées communes, promouvoir un cas local seulement s’il devient réutilisable. |

## Répartition sur les skills existants

Les ajouts vont aux producteurs de modèles, ports, use cases, libs, adapters,
persistance, configuration, assemblage, corrections, refactoring, tests unitaires,
stratégie de tests et documentation, avec leurs revues spécialisées. Les détails
ABC/Protocol/dispatch, Pydantic, best effort et mocks/fixtures restent accessibles
seulement lorsqu’ils s’appliquent.

Les compétences de messagerie, résilience, instrumentation, intégration,
contrats, crash, mesures et livraison conservent leurs instructions déjà utiles.
Les exigences transverses, la délégation Arclith conditionnelle et les relais
sont vérifiés sans remplir chaque skill du texte de l’archive.

Les seuils de complexité 10, d’imbrication 2 et de couverture 80/90 % ne deviennent
pas des quality gates universelles. Les suffixes Fields/Dto et les chemins
historiques restent des conventions contextuelles. Les nouvelles classes de
données Python restent Pydantic ; cela ne déclenche pas la migration de tout
l’existant. Les clauses historiques « aucun rapport » et « aucune commande
terminal » ne sont pas reprises : elles empêcheraient la preuve et le relais.


## Validation de la répartition

Les 48 skills passent `quick_validate.py` du skill système `skill-creator`.
Les liens locaux et ancres, le diff et la correspondance des 156 puces avec leurs
fichiers/lignes sources sont contrôlés ; les paragraphes et le README ont une
traçabilité séparée. `_rules/` reste identique à la source de départ.
Ces contrôles structurels ne prouvent pas le comportement d’un agent.

Une évaluation indépendante, sans lecture de ce journal ni de l’historique, a
appliqué les instructions à neuf demandes :

| Demande | Décision retrouvée |
| --- | --- |
| TU async, fake et fixture session partagés | Mock local adapté et données réelles ; pas de migration générale ni fixture MDM inventée. |
| Mise à jour de deux champs liés | Valider l’état final ; vérifier refus et état initial inchangé. |
| Héritage de deux bases Pydantic | Ne pas recombiner les branches ; proposer une chaîne unique préservant le contrat. |
| Deux ports et courte boucle métier | Conserver l’orchestration simple ; pas de nouveau service sans responsabilité distincte. |
| Port Mongo retournant dict et _id | Contrat typé, conversion et détails Mongo dans l’adapter ; examiner les consommateurs affectés. |
| DTO technique Python sans Arclith | Pydantic sans imposer Arclith ni inventer une identité métier. |
| Retrait d’option dans un autre module de settings | Suivre le module réel ; mettre à jour le guide courant, conserver le changelog historique légitime. |
| Complexité 11, troisième niveau, Ruff lint seul | Examiner les métriques sans FAIL automatique ; formatage non vérifié = preuve manquante, pas défaut de format inventé. |
| Publication obligatoire proposée en best effort | Refuser de masquer l’échec sans changement explicite du contrat ; traiter cohérence et reprise. |

Aucune contradiction interne n’a été démontrée sur ces cas. Le routage du skill
`implement-entity` a été précisé pour couvrir aussi les contrats de données sans
attribuer une identité ou un cycle de vie à un DTO. Cette passe est une simulation
documentaire, pas une exécution d’application.

### Exercice exécuté dans un projet temporaire

Un autre agent, sans historique ni journal, a reçu un petit projet Python brut
sans Arclith, avec une réservation Pydantic, un repository asynchrone, un test
existant et un fake partagé. La demande portait sur une révision conjointe de
`seats` et `capacity`, la préservation des contraintes et de l’objet initial en
cas de refus, puis un TU d’échec du repository. Il a utilisé `implement-entity`
puis `write-unit-tests` et leurs références ; les artefacts ont ensuite été
inspectés. Aucune installation ni action externe, aucun artefact d’application
ajouté au dépôt Skillforge.

Sous Pydantic 2.13.0 et pytest 9.0.2, dans
`/tmp/skillforge-forward-validation` :

| Contrôle exécuté | Résultat observé |
| --- | --- |
| `python -m pytest -q` initial | 1 test existant passe, malgré le défaut sur les mises à jour invalides. |
| Correction et nouveaux TU | Reconstruction d’un état validé ; transitions conjointes, limites, refus et état initial inchangé ; erreur de sauvegarde propagée ; sauvegarde non appelée après refus. |
| `python -m pytest -q` final | 17 tests passent. |
| Réintroduction en mémoire du `revise` initial | 6 cas ciblés échouent comme attendu ; le défaut est détecté. |
| Réexécution après restauration de la correction | 17 tests passent. |
| `python -m ruff check .` | Succès. |
| `python -m ruff format --check .` | 3 fichiers conformes. |
| `python -m mypy app.py tests` | Succès sur les 3 fichiers. |

Le fake et la fixture existants sont conservés. Les nouveaux tests utilisent un
mock local autospec du repository, les entités réelles et les assertions
asynchrones contractuelles. Le modèle conserve sa responsabilité métier ; aucun
service, mixin ou dépendance Arclith n’a été ajouté.

Les relais de revue de l’exercice ont été réalisés localement par son agent,
pas par des reviewers indépendants. La preuve porte sur le chemin `revise` de ce
petit projet, pas sur les affectations directes ni tous les usages de Pydantic.
Elle ne valide pas l’autodécouverte, l’installation des skills ou un moteur
d’agents, et ne remplace pas une validation future dans les projets consommateurs.
