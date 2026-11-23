# Parcours de production

Une invocation isolée s’arrête au résultat et au relais de son skill. Une demande
de tâche complète autorise la poursuite des phases applicables dans le périmètre
demandé. Un relais ou un verdict n’autorise pas une publication supplémentaire.

## Une seule phase active

Avant production, consigner les phases utiles, leur ordre, leur périmètre,
leurs livrables et leurs critères de validation. L’ordre est libre : code,
tests ou documentation peuvent venir en premier. Ne pas imposer un ordre
par défaut à une demande qui en a choisi un autre.

Une seule phase est active à la fois. Terminer sa production, exécuter ses
contrôles et obtenir `PASS` sur les critères applicables avant d’entamer la
suivante. Ne pas écrire ou modifier code, tests et documentation dans une même
opération, ni distribuer ces phases à des agents en parallèle. Une phase peut
couvrir plusieurs composants d’un sujet cohérent ; elle n’est pas limitée à un
use case. Les dépendances entre composants suivent
[feature-implementation.md](feature-implementation.md).

Exécuter des tests déjà présents pour vérifier la phase courante ne constitue
pas une phase de rédaction de tests. En revanche, écrire ou adapter des tests
exige une phase de tests distincte, même pour un correctif. Les revues ne
modifient pas les artefacts. `FAIL` ou `BLOCKED` interdit toute phase suivante.

## Validation adaptée à la phase

| Phase | Livrables et validation avant passage |
| --- | --- |
| Code | Implémentation du périmètre, revues de code et de risques applicables, contrôles statiques et tests existants pertinents. Réserver les garanties comportementales qui exigent de nouveaux tests. |
| Tests | Scénarios, assertions, isolation et résultats, puis `review-tests`. Si le code manque, vérifier que l’échec attendu vient du comportement absent, pas d’un test invalide ou d’un environnement défectueux. |
| Documentation | Document et sources, puis `review-documentation`. Si elle précède l’implémentation, identifier explicitement ce qui est prévu, sans le présenter comme un comportement déjà livré. |

Les critères d’une phase portent sur les preuves disponibles à ce stade. Une
validation préliminaire ne vaut pas preuve comportementale finale et ne doit
pas exiger la production anticipée des livrables d’une autre phase.

Par exemple : tests et revue préliminaire → code et revue → documentation et
revue ; ou documentation du contrat et revue → code et revue → tests et revue.
Ces exemples ne fixent pas l’ordre des autres demandes.

## Reprise et clôture

Si une phase révèle qu’un autre artefact doit changer, interrompre la phase
courante et enregistrer le retour à la phase concernée. Ne pas corriger cet
artefact en passant : appliquer [correction-loop.md](correction-loop.md),
rejouer les validations affectées, puis reprendre le parcours enregistré.
L’ordre peut être révisé explicitement pour cette reprise, sans chevauchement.

Avant livraison, vérifier l’accord entre code, tests et documentation finaux,
obtenir les preuves comportementales encore réservées et rejouer uniquement les
revues invalidées selon [review-sequences.md](review-sequences.md). Préparer
ensuite les artefacts de livraison, puis `review-delivery`, avant publication
autorisée. Découper PR et livraisons et tenir le changelog selon
[delivery](../references/delivery.md).

Pour un nouveau service Arclith, insérer les opérations propriétaires nécessaires
selon [service-initialization.md](service-initialization.md). La délégation ne
permet pas de mélanger les phases.
