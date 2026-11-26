---
name: review-configuration
description: "Vérifier qu’une configuration est chargée, validée et effectivement utilisée avec les valeurs, unités et modes attendus. Produire une revue sans corriger les fichiers."
---

# review-configuration

## Périmètre

Suivre les options de leurs sources à leurs effets réels, selon le contrat et les modes supportés du projet. Distinguer review de changement et review de projet ; pour un changement, séparer la dette indépendante de ses défauts et conséquences. Ne pas imposer de format de fichier ou de mécanisme de rechargement absent du besoin.

## Critères partagés

Appliquer d’abord la [méthode commune de revue](../../../references/review-method.md)
pour cadrer le dépôt, les sources et la comparaison, même en invocation seule.

- [configuration](../../../references/configuration.md)

## Examen

1. Identifier révision, phase, périmètre et sources des règles via la méthode commune. Relever les sources de configuration autorisées, leurs priorités, valeurs par défaut, alias et moment d’application.
2. Suivre le chargeur réel, la validation, les conversions, l’injection et le consommateur. Confronter valeurs effectives et unités attendues ; une option déclarée mais inutilisée ne satisfait pas le besoin.
3. Examiner les contraintes croisées et les modes supportés : options absentes ou explicites, surcharges, capacité activée ou désactivée. Vérifier les paramètres indispensables à chaque mode sans les exiger dans les modes où ils ne servent pas. Choisir les combinaisons pertinentes selon leurs dépendances, sans produit cartésien systématique.
4. Vérifier refus et moment du refus d’une configuration invalide. Repérer défaut de secours silencieux, succès apparent, opérations déjà engagées avant validation et changements non appliqués au moment promis. Ne pas exiger de rechargement à chaud si la configuration est fixée au démarrage.
5. Examiner secrets, exemples et absence d’invariants métier désactivables. Utiliser les contrôles disponibles en environnement isolé et autorisé, sans exposer les secrets ni contacter un service externe sans autorisation.

## Cohérence du changement

Suivre déclaration, alias, chargement, défauts, injection et consommateur jusqu’aux exemples et à la documentation. Pour une suppression ou un remplacement, rechercher les anciens noms et vérifier les occurrences encore valides ; ne pas se limiter au fichier de settings.

Le sens de l’option et la valeur transmise relèvent de cette revue ; la construction des bonnes instances et leur parcours réel relèvent de `review-service-integration`. Signaler tout défaut directement démontré, sans certifier les garanties de cette autre revue. Une priorité ou une règle croisée indispensable indécise donne `BLOCKED` ; la seule absence de documentation ne suffit pas.

Comparer aussi les [valeurs acceptées avant et après](../../../references/compatibility.md#valeurs-acceptées-et-validations),
notamment frontières, sentinelles et formes normalisées. Suivre une valeur
auparavant valide dans le chargeur réel jusqu’au démarrage ou au traitement.

## Restitution

Appliquer le [format de résultat](../../../workflows/review-result.md) : `PASS`, `FAIL` ou `BLOCKED`, preuves, limites et corrections attendues. Une preuve indispensable manquante ne vaut pas validation. Préciser les garanties reportées lors d’une revue préliminaire.

Pour chaque défaut, préciser option et mode, sources en conflit ou valeur déclenchante, valeur effectivement utilisée, consommateur, effet et principe de correction. Distinguer une valeur observée d’une règle confirmée et les observations par mock d’une garantie de fournisseur réel.

Ne pas corriger le code ni lancer le prochain agent. Le workflow décide du passage suivant et applique la [boucle de correction](../../../workflows/correction-loop.md).
