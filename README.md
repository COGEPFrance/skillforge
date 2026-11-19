# Skillforge

Skillforge a vocation à être la marketplace de skills partagés par toutes nos
équipes : un catalogue commun de méthodes et de pratiques réutilisables d’un
projet à l’autre.

## Le principe

Les skills sont **génériques dans leur portée, spécialisés dans leur objectif** :
chacun décrit comment accomplir une tâche précise, sans dépendre d’un projet
particulier. Par exemple : réaliser une revue de code, préparer une PR, définir
une stratégie de tests ou rédiger une documentation technique.

Les thèmes retenus sont **dev**, **test**, **review**, **documentation** et
**delivery**. Le thème **diagnostic** reste envisagé. Le cadrage et la conception
sont laissés de côté pour le moment.

Arclith est le socle du code des services visés par ce catalogue. Avant la
première fonctionnalité, un parcours dédié initialise le service : scaffold
Arclith, application d’un blueprint identifié, puis validation du socle obtenu.

## Production et revue

Les skills de production ont des skills de revue correspondants, spécialisés
par résultat ou par risque. Il n’y a pas de skill unique chargé de « tout revoir ».
Plusieurs skills de production peuvent partager un même skill de revue.

Les [principes de qualité retenus](references/quality-criteria.md) constituent
le référentiel commun à la production et aux revues. Ils seront déclinés
progressivement en critères vérifiables dans les skills.

La sécurité, la performance et la compatibilité sont conservées comme axes de
revue distincts et prioritaires. Leurs exigences restent prises en compte dès
la production. Les critères de qualité communs servent de référence aux deux.

## Utilisation future par des agents

Les skills décrivent les méthodes ; les agents les exécutent. À terme, un parcours
définira les agents de revue nécessaires à un besoin et leur ordre de passage.
Tous les agents sélectionnés devront valider leur étape.

- Une étape validée autorise le passage à la suivante.
- Une étape en échec interrompt le parcours et demande une correction.
- Après correction, l’étape doit être validée à nouveau. Les revues déjà passées
  dont les conclusions sont affectées par la correction doivent aussi être rejouées.
- Une revue impossible à exécuter ne vaut pas validation : le parcours reste bloqué.

Les workflows définissent un ordre de référence, les verdicts et les règles de
reprise. Chaque besoin sélectionne ses agents et enregistre leur ordre avant
exécution. Les définitions exécutables d’agents et leur moteur d’orchestration
restent à implémenter.

## Arborescence du catalogue

Le catalogue contient une première version de 48 skills, 17 référentiels et
7 workflows documentaires, fondée uniquement sur les décisions de cette proposition.
Les anciens fichiers de règles restent inchangés et ne sont pas incorporés.
Les deux skills de diagnostic figurant ci-dessous restent prévus, non créés.

Le format de distribution et d’installation sera défini séparément. Pour le
moment, les skills et leurs références forment un ensemble à conserver dans
cette arborescence : copier un seul dossier de skill ne suffit pas à embarquer
ses références communes. Aucun enregistrement de marketplace ni moteur d’agents
n’est activé par ces fichiers.

Les skills de `dev/` combinent l’initialisation du socle et des tâches
d’implémentation spécialisées : lib, entités, ports, use cases, adapters et
assemblage. Configuration, échanges, persistance, résilience et instrumentation
ont également leurs tâches dédiées. Il n’est pas nécessaire de tous les exécuter
pour chaque modification. La réalisation complète d’une fonctionnalité relève
d’un workflow, sans skill global `implement-feature`.

Les revues sont séparées par responsabilité. La revue d’architecture vérifie
l’implémentation hexagonale et les frontières des microservices ; elle n’ajoute
pas un thème de conception. Chaque revue examine aussi les tests et les preuves
qui concernent son périmètre, lorsqu’ils sont disponibles. Une revue préliminaire
ne vaut pas validation finale du comportement.

```text
skillforge/
├── README.md
├── skills/
│   ├── dev/
│   │   ├── scaffold-arclith-service/SKILL.md
│   │   ├── apply-arclith-blueprint/SKILL.md
│   │   ├── implement-lib/SKILL.md
│   │   ├── implement-entity/SKILL.md
│   │   ├── implement-port/SKILL.md
│   │   ├── implement-usecase/SKILL.md
│   │   ├── implement-adapter/SKILL.md
│   │   ├── integrate-service-components/SKILL.md
│   │   ├── fix-bug/SKILL.md
│   │   ├── refactor/SKILL.md
│   │   ├── implement-configuration/SKILL.md
│   │   ├── implement-messaging/SKILL.md
│   │   ├── implement-persistence/SKILL.md
│   │   ├── implement-resilience/SKILL.md
│   │   └── instrument-service/SKILL.md
│   ├── test/
│   │   ├── define-test-strategy/SKILL.md
│   │   ├── write-unit-tests/SKILL.md
│   │   ├── write-integration-tests/SKILL.md
│   │   ├── write-contract-tests/SKILL.md
│   │   ├── test-crash-recovery/SKILL.md
│   │   └── measure-performance/SKILL.md
│   ├── documentation/
│   │   ├── write-documentation/SKILL.md
│   │   └── update-documentation/SKILL.md
│   ├── delivery/
│   │   ├── prepare-commits/SKILL.md
│   │   ├── prepare-pull-request/SKILL.md
│   │   ├── resolve-conflicts/SKILL.md
│   │   ├── prepare-release/SKILL.md
│   │   └── prepare-deployment/SKILL.md
│   ├── review/
│   │   ├── review-service-foundation/SKILL.md
│   │   ├── review-architecture/SKILL.md
│   │   ├── review-code/SKILL.md
│   │   ├── review-lib/SKILL.md
│   │   ├── review-domain-models/SKILL.md
│   │   ├── review-ports/SKILL.md
│   │   ├── review-usecases/SKILL.md
│   │   ├── review-adapters/SKILL.md
│   │   ├── review-service-integration/SKILL.md
│   │   ├── review-configuration/SKILL.md
│   │   ├── review-messaging/SKILL.md
│   │   ├── review-data-consistency/SKILL.md
│   │   ├── review-resilience/SKILL.md
│   │   ├── review-observability/SKILL.md
│   │   ├── review-tests/SKILL.md
│   │   ├── review-security/SKILL.md
│   │   ├── review-performance/SKILL.md
│   │   ├── review-compatibility/SKILL.md
│   │   ├── review-documentation/SKILL.md
│   │   ├── review-delivery/SKILL.md
│   │   └── review-diagnostic/SKILL.md # prévu, non créé
│   └── diagnostic/                  # prévu, non créé
│       └── diagnose-failure/SKILL.md
├── references/
│   ├── quality-criteria.md          # index des référentiels partagés
│   ├── architecture.md             # hexagonal, microservices, réutilisation
│   ├── service-foundation.md        # scaffold, blueprint, critères de passage
│   ├── code-quality.md             # SRP, KISS, DRY, typage, erreurs, périmètre
│   ├── domain-models.md             # entités, invariants, mutations
│   ├── configuration.md            # sources, validation, secrets
│   ├── messaging.md                # contrats, livraison, ordre, doublons
│   ├── data-consistency.md         # transactions, publication, migrations
│   ├── resilience.md               # timeouts, retries, crash, reprise
│   ├── observability.md            # logs, métriques, traces, corrélation
│   ├── performance.md              # objectifs, charge, mesures
│   ├── security.md
│   ├── compatibility.md
│   ├── testing.md
│   ├── documentation.md
│   ├── delivery.md
│   └── profiles/
│       └── python-arclith.md        # Pydantic, socle Arclith, délégation
└── workflows/
    ├── service-initialization.md   # scaffold → blueprint → revue du socle
    ├── feature-implementation.md   # lib → entités → ports → use cases → adapters
    ├── refactoring-scope.md        # changement nécessaire ou issue avec impact
    ├── production-sequences.md     # code d’abord ou tests d’abord, puis doc
    ├── review-sequences.md         # agents sélectionnés, ordre et dépendances
    ├── review-result.md            # verdict, preuves, constats, corrections
    └── correction-loop.md          # blocage, correction, revues à rejouer
```

`quality-criteria.md` est le point d’entrée des référentiels détaillés. Les
skills de production et de revue utilisent les mêmes références. Le profil
Python/Arclith porte les choix technologiques communs aux projets consommateurs
et renvoie aux procédures Arclith effectivement disponibles dans l’environnement.
Les règles seront enrichies progressivement à partir des anciens documents,
après examen, sans duplication.

### Initialiser avant d’implémenter

Le parcours d’initialisation prépare une base exécutable pour le premier
développement métier. Il reste dans `dev/` et n’introduit pas un thème de
conception générale.

1. `scaffold-arclith-service` génère le squelette du service à partir des
   capacités et procédures Arclith disponibles, avec des versions identifiées.
2. `apply-arclith-blueprint` applique un blueprint existant, identifié et
   compatible : structure, composants techniques, assemblage des dépendances,
   configuration et instrumentation nécessaires au service. Il ne crée pas un
   blueprint inédit ni la première fonctionnalité métier. Si aucun blueprint
   adapté n’est disponible, il signale le blocage.
3. `review-service-foundation` vérifie la conformité au blueprint, la structure
   attendue, l’assemblage, la configuration, le démarrage et la production des
   signaux d’observabilité de base, avec des preuves adaptées. Cette revue ne
   remplace pas les futures revues du comportement métier, de sécurité, de
   performance ou de résilience.
4. La première implémentation est autorisée une fois le socle validé. Un échec
   bloque ce passage et suit la boucle de correction commune.

Chaque skill pourra être exécuté par un agent spécialisé distinct. Le workflow
porte leur enchaînement ; les skills délèguent aux procédures de la marketplace
Arclith les opérations propres au framework, sans les recopier.
Sur un service existant, on vérifie le socle et les écarts utiles sans relancer
une génération qui écraserait le code en place.

### Implémenter par composants

Après validation du socle, le workflow de fonctionnalité suit les dépendances :
lib si nécessaire → entités → ports → use cases → adapters → assemblage.
Chaque étape applicable peut être confiée à un agent spécialisé, reçoit une
première revue avant la suivante et suit les mêmes règles de blocage et de correction.
Les tests et validations complémentaires suivent le parcours choisi ; la revue
intermédiaire d’un composant ne garantit pas le fonctionnement de l’ensemble.

| Skill de production | Résultat attendu | Revue spécialisée |
| --- | --- | --- |
| `implement-lib` | Composant autonome réutilisable réellement nécessaire, absent d’Arclith et des dépendances retenues | `review-lib` |
| `implement-entity` | Entités Pydantic, identité, invariants et opérations métier | `review-domain-models` |
| `implement-port` | Contrats des dépendances nécessaires aux use cases, sans adapter concret | `review-ports` |
| `implement-usecase` | Intention applicative implémentée au travers des entités et des ports | `review-usecases` |
| `implement-adapter` | Implémentation d’un port et conversions aux frontières techniques | `review-adapters` |
| `integrate-service-components` | Assemblage des composants dans le service existant et vérification de leur intégration | `review-service-integration` |

L’étape lib ne crée pas systématiquement une bibliothèque ou un paquet. Elle
réutilise l’existant en priorité ; une capacité générique propre à Arclith doit
être traitée dans son projet, sans réimplémentation locale concurrente. Le
workflow vérifie ses prérequis avant de poursuivre.

Les tâches de configuration, messages, persistance, résilience et instrumentation
interviennent au niveau du composant concerné, sous leur responsabilité propre,
sans dupliquer sa logique. Le workflow précise l’ordre effectif selon les
dépendances ; un composant existant conforme n’est pas recréé.

Un refactoring nécessaire à la fonctionnalité reste dans son périmètre et suit
les revues applicables. Un refactoring indépendant donne lieu à une issue dédiée
avec une analyse d’impact : problème, composants et consommateurs affectés,
risques de compatibilité ou de migration, périmètre et validations attendues.
Il n’est pas implémenté dans le changement courant.

Les frontières des revues sont explicites : `review-code` porte sur
la qualité locale du code ; `review-tests` sur la pertinence des tests ;
`review-data-consistency` sur les transactions et les effets persistés ;
`review-resilience` sur les défaillances et la reprise ; `review-observability`
sur les signaux effectivement exploitables. Sécurité, performance et compatibilité
restent des revues dédiées.

Exemple de parcours à préciser pour une modification de code, après validation
du socle lors de l’initialisation du service :

1. Production du code par composants, avec les revues spécialisées intermédiaires,
   puis revues de structure transverses : architecture, code et configuration
   selon le périmètre.
2. Production et revue des tests ; revues spécialisées applicables : échanges,
   cohérence des données, résilience, observabilité, sécurité, compatibilité et
   performance, avec leurs preuves d’exécution.
3. Production puis revue de la documentation.
4. Préparation de la livraison puis revue de delivery.

Chaque groupe est décliné dans le workflow en une liste ordonnée d’agents. Tous les agents
sélectionnés doivent valider leur étape avant la suivante ; les groupes ne sont
pas des exécutions parallèles. Le parcours tests d’abord aura sa propre séquence.
Les workflows précisent aussi les blocages, corrections et validations à
rejouer. Ils décrivent l’orchestration attendue, sans présumer de son moteur ni
du format technique des futures définitions d’agents.

## Commun à l’équipe, spécifique au projet

- **Skillforge** porte les skills transverses, destinés à être partagés entre
  toutes les équipes.
- **Chaque projet** porte ses propres skills : son architecture, ses outils,
  ses règles métier et ses procédures particulières.

Par exemple, [Arclith](https://github.com/karned-agency/arclith) possède sa propre
marketplace pour ses skills spécifiques. Dataflow a également vocation à porter
les siens. Une équipe travaillant sur ces projets combine le socle Skillforge
avec les skills du projet concerné.

## Faire évoluer le catalogue

L’objectif est de maintenir une référence commune, versionnée et revue
collectivement, pour que les équipes utilisent les mêmes pratiques et des
versions identifiées des skills.

Un nouveau skill rejoint Skillforge lorsqu’il répond à un besoin partagé entre
projets. S’il dépend d’un projet particulier, il reste dans ce projet. Un skill
local peut ensuite être généralisé lorsqu’un usage commun se confirme.
