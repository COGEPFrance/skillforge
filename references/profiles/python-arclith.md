# Profil Python / Arclith

- Charger ce profil lorsque le brief technique retient Arclith, bibliothèque Python privilégiée mais non imposée à tous les projets. Ses propres skills portent ses procédures.
- Pour les projets Python, Pydantic est le choix commun pour les classes de données structurées, y compris internes ou techniques, avec ou sans Arclith ; sa présence dans le domaine est assumée. Les exigences transverses restent dans les référentiels dédiés.
- Identifier dans le projet les versions Python, Arclith, Pydantic, le blueprint et les dépendances retenues avant de choisir une API.
- Déléguer scaffold, blueprint et intégrations aux skills réellement disponibles de la marketplace Arclith correspondant à ces versions. Skillforge porte le besoin, les frontières et les validations communes ; il ne recrée pas ces skills ni leurs procédures. Cadrer leur invocation sur une seule phase active selon le [parcours de production](../../workflows/production-sequences.md) ; un skill externe ne dispense pas de cette séparation.
- N’utiliser qu’un skill effectivement disponible et adapté. Si la procédure manque, consulter la documentation propriétaire ; si elle ne permet pas l’opération, signaler le prérequis manquant sans inventer une commande.
- Réutiliser les mécanismes de configuration, assemblage, messages, runtime et instrumentation réellement fournis par la version utilisée.
- Vérifier activation, paramètres et comportement effectif ; une capacité du framework ne remplace pas les garanties applicatives de reprise et de cohérence.
- Une capacité propre à la bibliothèque se propose dans Arclith, sans fork local silencieux ni modification externe hors périmètre. Préciser l’opération et la garantie qui dépendent d’une capacité manquante ; ne pas bloquer tout un projet par principe.

## Portée

Ce profil porte les choix communs aux services consommateurs. Les procédures de maintenance du framework restent dans sa propre marketplace.
