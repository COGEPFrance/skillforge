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

Le choix des agents, les critères bloquants et l’ordre exact des revues restent
à préciser. L’orchestration n’est pas encore implémentée.

## Arborescence proposée — à valider

Cette structure représente l’organisation logique du catalogue. Les noms et le
découpage des skills sont proposés ; les dossiers de skills et de workflows ne
sont pas encore créés. Le référentiel `references/quality-criteria.md` existe.
Le format de distribution et d’installation sera défini séparément.

Les skills de `dev/` combinent des tâches de changement (implémenter, corriger,
refactorer) et des tâches spécialisées mobilisables selon le besoin : modèles,
configuration, échanges, persistance, résilience et instrumentation. Il n’est
pas nécessaire de tous les exécuter pour chaque modification.

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
│   │   ├── implement-feature/SKILL.md
│   │   ├── fix-bug/SKILL.md
│   │   ├── refactor/SKILL.md
│   │   ├── implement-domain-models/SKILL.md
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
│   │   ├── review-architecture/SKILL.md
│   │   ├── review-code/SKILL.md
│   │   ├── review-domain-models/SKILL.md
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
│   │   └── review-diagnostic/SKILL.md # optionnel, à confirmer
│   └── diagnostic/                  # optionnel, à confirmer
│       └── diagnose-failure/SKILL.md
├── references/
│   ├── quality-criteria.md          # synthèse retenue, déjà présente
│   ├── architecture.md             # hexagonal, microservices, réutilisation
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
    ├── production-sequences.md     # code d’abord ou tests d’abord, puis doc
    ├── review-sequences.md         # agents sélectionnés, ordre et dépendances
    ├── review-result.md            # verdict, preuves, constats, corrections
    └── correction-loop.md          # blocage, correction, revues à rejouer
```

Les référentiels détaillés seront extraits progressivement de la synthèse
`quality-criteria.md`, qui en deviendra le point d’entrée, sans dupliquer les
règles. Les skills de production et de revue utiliseront les mêmes références.
Le profil Python/Arclith précisera les choix technologiques communs aux projets
consommateurs et renverra aux skills Arclith pour ses procédures spécifiques.

Les frontières des revues devront être explicites : `review-code` porte sur
la qualité locale du code ; `review-tests` sur la pertinence des tests ;
`review-data-consistency` sur les transactions et les effets persistés ;
`review-resilience` sur les défaillances et la reprise ; `review-observability`
sur les signaux effectivement exploitables. Sécurité, performance et compatibilité
restent des revues dédiées.

Exemple de parcours à préciser pour une modification de code :

1. Production du code et revues préliminaires de structure : architecture, code,
   modèles et configuration selon le périmètre.
2. Production et revue des tests ; revues spécialisées applicables : échanges,
   cohérence des données, résilience, observabilité, sécurité, compatibilité et
   performance, avec leurs preuves d’exécution.
3. Production puis revue de la documentation.
4. Préparation de la livraison puis revue de delivery.

Chaque groupe sera décliné en une liste ordonnée d’agents. Tous les agents
sélectionnés doivent valider leur étape avant la suivante ; les groupes ne sont
pas des exécutions parallèles. Le parcours tests d’abord aura sa propre séquence.
Les workflows préciseront aussi les blocages, corrections et validations à
rejouer. Ils décriront l’orchestration attendue, sans présumer de son moteur ni
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
