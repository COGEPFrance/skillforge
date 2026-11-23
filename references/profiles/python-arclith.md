# Profil Python / Arclith

- Arclith est le socle des services visés ; Pydantic est utilisé pour les entités. Les exigences transverses restent dans les référentiels dédiés.
- Identifier dans le projet les versions Python, Arclith, Pydantic, le blueprint et les dépendances retenues avant de choisir une API.
- Consulter les skills disponibles de la marketplace Arclith et sa documentation correspondant à ces versions pour scaffold, blueprint et intégrations.
- N’utiliser qu’un skill effectivement disponible et adapté. Si la procédure manque, consulter la documentation propriétaire ; si elle ne permet pas l’opération, signaler le prérequis manquant sans inventer une commande.
- Réutiliser les mécanismes de configuration, assemblage, messages, runtime et instrumentation réellement fournis par la version utilisée.
- Vérifier activation, paramètres et comportement effectif ; une capacité du framework ne remplace pas les garanties applicatives de reprise et de cohérence.
- Une capacité générique propre au framework se traite dans le projet Arclith, sans fork local silencieux ni modification externe hors périmètre.

## Portée

Ce profil porte les choix communs aux services consommateurs. Les procédures de maintenance du framework restent dans sa propre marketplace.
