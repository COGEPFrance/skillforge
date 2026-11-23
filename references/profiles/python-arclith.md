# Profil conditionnel Python / Arclith

Les instructions opérationnelles sont dans [`scaffold-arclith-service`](../../skills/dev/scaffold-arclith-service/SKILL.md), [`apply-arclith-blueprint`](../../skills/dev/apply-arclith-blueprint/SKILL.md), [`review-service-foundation`](../../skills/review/review-service-foundation/SKILL.md).

Charger ce profil lorsque le brief d’architecture technique retient Arclith. Arclith est une bibliothèque Python destinée à rationaliser une grande partie des développements Python ; elle n’est pas imposée à tous les projets. Ses propres skills portent ses procédures spécialisées.

Identifier versions Python, Arclith, dépendances et blueprint utile. Pour une opération propre à Arclith, consulter un skill Arclith réellement disponible et adapté à ces versions ; sinon utiliser sa documentation propriétaire. Ne pas inventer une API, une commande ou une option manquante.

Examiner configuration, assemblage, messages, runtime et instrumentation fournis avant de développer un équivalent. Vérifier activation et comportement : la bibliothèque ne garantit pas les propriétés applicatives de cohérence ou de reprise.

Si une procédure ou capacité indispensable manque, préciser la garantie ou l’opération bloquée et proposer la suite appropriée ; ne pas déclarer tout le projet bloqué par principe. Une évolution de la bibliothèque se propose dans Arclith, sans fork silencieux ni modification externe non autorisée. Pour l’application d’un blueprint, son absence ou incompatibilité bloque cette étape explicitement demandée.

Pour les projets Python, Pydantic est le choix commun pour les entités et une dépendance assumée du domaine ; Arclith l’intègre dans son core. Ce choix vaut aussi sans Arclith. Ses contrôles de validation sont dans [modèles métier](../domain-models.md).
