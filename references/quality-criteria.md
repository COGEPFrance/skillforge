# Principes de qualité retenus

Ce référentiel synthétise les décisions prises pour Skillforge. Il servira de
base aux skills de production et aux revues spécialisées. Il ne constitue pas
encore une liste exhaustive de contrôles bloquants.

Les autres fichiers Markdown déjà présents dans le dépôt ne sont pas intégrés
à cette synthèse. Leur contenu sera examiné et incorporé progressivement aux
skills. Le cadrage et la conception ne sont pas des thèmes du catalogue à ce stade.

## Architecture et réutilisation

- Adopter une architecture hexagonale stricte, aux responsabilités et frontières
  explicites : domaine, cas d’usage, ports et adapters.
- Garder le domaine indépendant des transports, du stockage et des adapters
  concrets. Isoler les conversions de formats externes aux frontières.
- Injecter les dépendances et centraliser leur assemblage.
- Utiliser Arclith comme socle pour les services Python concernés. Vérifier et
  réutiliser ses capacités avant de créer un mécanisme équivalent.
- Distinguer la disponibilité d’un mécanisme dans Arclith de son intégration
  correcte dans le service : configuration, instrumentation, comportement et
  garanties doivent être vérifiés pour le cas d’usage réel.
- Respecter SRP, KISS et DRY sans multiplier artificiellement couches,
  interfaces ou abstractions. Une mutualisation répond à un besoin réel.
- Retenir des pratiques maintenues, éprouvées et adaptées au besoin : c’est le
  sens donné ici à SOTA, sans recherche systématique de nouveauté.

## Modèles, typage et contrats

- Utiliser Pydantic pour les entités ; cette dépendance du domaine est assumée.
- Distinguer entités, objets valeur, DTO, commandes et modèles de configuration.
  Ne pas partager automatiquement un même modèle entre toutes les frontières.
- Définir des entrées, sorties et erreurs explicites et précisément typées.
- Préciser les contraintes de champs, invariants entre champs, conversions
  autorisées, champs supplémentaires et règles de mutabilité.
- Préserver les invariants pendant tout le cycle de vie, y compris lors des
  mises à jour. Ne pas contourner la validation sans justification explicite.

## Configuration

- Centraliser les variations utiles et identifiées dans une configuration
  lisible, de préférence YAML ou un format équivalent adapté.
- Rendre configurables les variations d’environnement, de déploiement et de
  fonctionnement pertinentes, sans transformer chaque détail en option.
- Typer et valider la configuration au démarrage ; définir les valeurs par
  défaut et la priorité des différentes sources.
- Éviter les paramètres dispersés et les lectures d’environnement dans le code
  métier. Fournir les secrets séparément des fichiers de configuration partagés.
- Ne pas transformer automatiquement les invariants métier en options désactivables.

## Microservices et échanges

- Travailler en microservices avec une responsabilité métier claire, une
  propriété explicite des données et une capacité de déploiement indépendante.
- Limiter le couplage et la portée des changements. Ne pas accéder directement
  aux données internes d’un autre service.
- Privilégier les messages lorsque le traitement différé, le découplage ou
  l’absorption de charge apporte un bénéfice identifié ; ne pas imposer
  l’asynchronisme sans ce bénéfice.
- Expliciter les contrats d’API et d’événements ainsi que leur évolution.
- Définir les garanties de cohérence entre persistance et publication de messages,
  les frontières transactionnelles et les moyens de reprise adaptés.

## Résilience et reprise après crash

- Prendre en compte les défaillances dans le code applicatif, au-delà des
  mécanismes fournis par le framework, le broker ou l’infrastructure.
- Définir les timeouts, retries bornés, limites de concurrence et conditions
  d’abandon. Distinguer erreurs temporaires et erreurs définitives.
- Prévoir l’idempotence, les doublons, les traitements partiels et l’ordre des
  messages lorsque celui-ci importe.
- Pour chaque traitement concerné, préciser ce qui est durable, ce qui peut
  être rejoué et comment retrouver les opérations interrompues après un crash.
- Positionner les acquittements et points de reprise en cohérence avec les
  effets réellement enregistrés. Prévenir les pertes silencieuses et les
  effets métier dupliqués lors d’un redémarrage.
- Prévoir le traitement des messages en échec et leur remise en traitement
  maîtrisée ; ne pas créer de boucle de retry infinie.
- Prévoir un arrêt propre, sans supposer qu’il aura lieu lors de chaque panne.
- Vérifier les scénarios de crash, de redémarrage et de reprise pertinents.

## Observabilité et performance

- Instrumenter les services avec des logs structurés, des métriques et des traces
  permettant de comprendre et de mesurer leur comportement.
- Propager le contexte de corrélation et de trace entre appels et messages,
  y compris pour les traitements asynchrones et leurs tentatives successives.
- Rendre observables les erreurs, retries, abandons, reprises et traitements
  bloqués. Ne pas masquer un échec derrière un faux succès.
- Mesurer, selon le traitement, les latences, débits, erreurs, ressources,
  accumulations de messages et délais de traitement.
- Définir les volumes et objectifs attendus ; mesurer les chemins critiques
  avant de conclure qu’une optimisation ou une architecture est performante.
- Maîtriser le coût de l’instrumentation et la cardinalité des métriques.
- Protéger secrets et données sensibles dans les logs, métriques et traces.
- Réutiliser l’instrumentation d’Arclith lorsqu’elle convient et vérifier que
  les signaux nécessaires sont effectivement produits et exploitables.

## Sécurité, compatibilité et maîtrise des changements

- Intégrer validation aux frontières, autorisations explicites et moindre
  privilège dès la production ; approfondir ces contrôles en revue de sécurité.
- Maîtriser l’évolution des API, événements, configurations et schémas persistés,
  y compris pendant une transition entre versions de services.
- Prévoir les migrations, reprises de données et possibilités de retour arrière
  ou de correction lorsque le changement le nécessite.
- Maîtriser les versions des dépendances et éviter les ajouts sans besoin réel.
- Limiter chaque changement au besoin traité, sans refonte opportuniste.

## Production et validation par étapes

- Séparer les étapes pour ne pas investir dans les suivantes tant que leur base
  n’a pas reçu une première validation adaptée.
- Parcours de référence : code → revue structurelle et contrôles statiques →
  tests et revue des tests → validation du comportement et des risques →
  documentation et revue documentaire → livraison.
- Autoriser les tests en premier lorsqu’ils permettent de préciser ou reproduire
  le comportement attendu ; faire adapter le parcours à ce choix.
- Continuer à exécuter les tests existants pendant le développement. Une première
  revue du code ne remplace pas la validation du comportement par les tests.
- Tout défaut découvert ultérieurement peut imposer un retour au code et la
  répétition des validations affectées.
- Maintenir des revues spécialisées, notamment pour la sécurité, la performance
  et la compatibilité, plutôt qu’une revue unique chargée de tout contrôler.
- Définir progressivement pour chaque règle son résultat attendu, ses preuves
  de vérification et son caractère bloquant. Un contrôle impossible à réaliser
  ne constitue pas une validation.
