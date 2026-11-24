# Livraison

- Limiter chaque PR à un sujet cohérent, de taille adaptée au besoin. Préférer
  les plus petites livraisons autonomes et vérifiables possibles pour suivre
  l’avancement et faciliter un rollback ; ne pas imposer une PR par use case.
  Séparer les sujets indépendants et expliciter les dépendances entre PR.
- Préserver un état livrable cohérent : ne pas publier du code incomplet ou un
  découpage artificiel qui exige plusieurs déploiements simultanés pour fonctionner.
  Pour une migration irréversible, expliciter la limite et le moyen de reprise.
- Tenir un changelog précis selon le format du projet, avant livraison : effet
  concret de chaque changement, corrections, migrations et incompatibilités,
  avec liens vers les PR et version livrée. Avant release, garder les changements
  dans une section non publiée plutôt qu’inventer une version ou annoncer une
  livraison effectuée. Distinguer avancement intégré et travail encore prévu.
- Vérifier le contenu exact à committer et publier ; préserver les modifications qui ne font pas partie de la tâche.
- Utiliser les conventions et outils de versionnement du dépôt ; ne pas inventer une stratégie de branches ou de release. Réutiliser une branche de tâche adaptée lorsqu’elle existe ; pour une nouvelle branche, vérifier la base pertinente plutôt qu’imposer origin/main à chaque invocation.
- Préparer les versions, notes de release, migrations, prérequis de déploiement et moyens de reprise nécessaires.
- Distinguer préparation d’un artefact et publication effective. Exécuter commit, push, ouverture de PR, release ou déploiement uniquement dans le périmètre autorisé par la demande.
- Les contrôles applicables et revues sélectionnées doivent être validés avant la livraison correspondante.

## Preuves attendues

Identifier la révision et le contenu livrés, les validations, les dépendances de déploiement et les risques connus. Vérifier l’état distant avant une action qui en dépend.
