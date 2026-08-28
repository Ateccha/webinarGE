# Gemini Enterprise — Prérequis techniques, Quotas & Dépassements

*Document de référence interne ATECNA — recherche menée le 28/08/2026 sur la documentation officielle Google Cloud (arborescence `docs.cloud.google.com/gemini/enterprise/docs/`) et sources complémentaires. Gemini Enterprise est le nom actuel de la plateforme précédemment commercialisée sous le nom « Google Agentspace » ; Google a annoncé ce changement de marque le 9 octobre 2025, et a poursuivi la consolidation lors de Google Cloud Next 2026 en renommant également Vertex AI en « Gemini Enterprise Agent Platform » (Source : https://cloudfresh.com/en/blog/google-agentspace-evolves-into-gemini-enterprise/ — ⚠️ source secondaire, non officielle Google).*

---

## 1. Qu'est-ce que Gemini Enterprise

Gemini Enterprise est décrit par Google comme une plateforme combinant recherche d'entreprise (intranet search), assistant IA conversationnel et plateforme agentique (Source : https://docs.cloud.google.com/gemini/enterprise/docs). Ses composants principaux sont :

- **Recherche multimodale** avec prise en compte des permissions d'accès (« permissions-aware ») (Source : https://docs.cloud.google.com/gemini/enterprise/docs)
- **Assistant IA conversationnel** s'appuyant sur les sources de données connectées de l'organisation (Source : https://docs.cloud.google.com/gemini/enterprise/docs)
- **Agents** personnalisés ou pré-construits, accessibles via une « Agent Gallery » (Source : https://docs.cloud.google.com/gemini/enterprise/docs)
- **Connecteurs** prêts à l'emploi vers des outils tiers (Confluence, Jira, Microsoft SharePoint, ServiceNow, etc.) (Source : https://docs.cloud.google.com/gemini/enterprise/docs)
- Un accès inclus à **Gemini Code Assist Standard** pour les éditions Standard et Plus (Source : https://docs.cloud.google.com/gemini/enterprise/docs/licenses)

La documentation est organisée par rôle : administrateurs (déploiement, connexion des sources de données), utilisateurs applicatifs (web/mobile) et développeurs (intégration via API REST/RPC) (Source : https://docs.cloud.google.com/gemini/enterprise/docs).

---

## 2. Éditions disponibles

D'après la page officielle de comparaison des éditions, cinq éditions principales existent : **Business**, **Standard**, **Plus**, **Pay-as-you-go**, et **Frontline** (Source : https://docs.cloud.google.com/gemini/enterprise/docs/editions). La documentation quotas/tarification mentionne également des variantes **EDU**, **EDU Pro**, **Frontline Starter**, **Frontline Worker**, et une variante **Standard Emerging Market** (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages).

| Édition | Nombre de sièges | Particularités | Source |
|---|---|---|---|
| Business | 1 à 500 utilisateurs | Pas de configuration IT nécessaire ; ne nécessite pas de projet Google Cloud dédié géré par l'IT | https://docs.cloud.google.com/gemini/enterprise/docs/editions |
| Standard | 1 utilisateur ou plus | Contrôles IT/entreprise complets | https://docs.cloud.google.com/gemini/enterprise/docs/editions |
| Plus | 1 utilisateur ou plus | Quotas plus élevés que Standard | https://docs.cloud.google.com/gemini/enterprise/docs/editions |
| Pay-as-you-go | 1 siège minimum | Aucune limite de quota fonctionnel ; facturation à l'usage | https://docs.cloud.google.com/gemini/enterprise/docs/editions |
| Frontline | 150 utilisateurs Standard/Plus existants minimum requis | Add-on : accès uniquement aux agents déjà provisionnés par l'administrateur, pas de création de notebooks | https://docs.cloud.google.com/gemini/enterprise/docs/editions |

**Point de scoping important** : Frontline n'est pas une édition autonome — elle nécessite une base d'au moins 150 licences Standard ou Plus déjà existantes dans l'organisation (Source : https://docs.cloud.google.com/gemini/enterprise/docs/editions).

### 2.1 Business edition — parcours simplifié

L'édition Business est conçue pour des équipes jusqu'à 300 personnes sans nécessiter de configuration IT (Source : https://support.google.com/g/answer/17100048?hl=en — ⚠️ source secondaire Google Support, hors arborescence documentaire ciblée). Après attribution d'une licence, l'administrateur se connecte simplement sur `business.gemini.google`, sans création préalable d'un projet Google Cloud par l'IT (Source : https://support.google.com/g/answer/17100048?hl=en — ⚠️ Non vérifié directement sur `docs.cloud.google.com`). Un essai gratuit de 30 jours est proposé (Source : https://support.google.com/g/answer/17100048?hl=en — ⚠️ source secondaire).

### 2.2 Tarification par siège

⚠️ **Non vérifié directement** : la page officielle `cloud.google.com/gemini-enterprise#pricing` n'a pas pu être chargée intégralement (contenu tronqué lors de la récupération). Les éléments suivants proviennent d'extraits indexés par le moteur de recherche et de sites tiers, à confirmer avant tout chiffrage de projet client :

- Business : environ 21 $ US/siège/mois (Source : recherche web sur snippets `cloud.google.com/gemini-enterprise` — ⚠️ Non vérifié)
- Standard : à partir de 30 $ US/siège/mois avec engagement annuel (35 $ sans engagement selon des revendeurs) (Source : agrégation de blogs tiers, notamment https://coworker.ai/blog/gemini-enterprise-pricing — ⚠️ Non vérifié)
- Plus : environ 50 $ US/siège/mois avec engagement annuel (60 $ sans engagement) (Source : https://coworker.ai/blog/gemini-enterprise-pricing — ⚠️ Non vérifié)
- La consommation de calcul (Agent Platform) est facturée séparément au compte Google Cloud lié, en plus du prix par siège (Source : https://coworker.ai/blog/gemini-enterprise-pricing — ⚠️ Non vérifié)

**Recommandation pour le chiffrage** : valider ces montants avec un commercial Google Cloud ou via la console de facturation avant de les intégrer dans une proposition ATECNA.

---

## 3. Prérequis organisationnels avant provisioning

D'après la page officielle « Before you begin » et le guide de démarrage rapide :

- **Compte Google** : disposer d'un compte Google ; possibilité de créer un compte d'évaluation pour les nouveaux clients Google Cloud (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quickstart-gemini-enterprise)
- **Projet Google Cloud** : un projet Google Cloud est nécessaire pour héberger les apps, data stores et connecteurs (sauf édition Business en self-serve) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/before-you-begin)
- **Rôle requis pour créer le projet** : `roles/resourcemanager.projectCreator` si un nouveau projet doit être créé (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quickstart-gemini-enterprise)
- **Compte de facturation Cloud actif** : la facturation Cloud doit être activée sur le projet avant de poursuivre, pour supporter les paliers d'abonnement et le pay-as-you-go (Source : https://docs.cloud.google.com/gemini/enterprise/docs/before-you-begin ; https://docs.cloud.google.com/gemini/enterprise/docs/quickstart-gemini-enterprise)
- **Vérification de domaine Workspace** : non explicitement détaillée dans les pages consultées de la documentation Gemini Enterprise — ⚠️ Non vérifié spécifiquement pour ce produit (il s'agit toutefois d'un prérequis standard bien connu pour toute organisation Cloud Identity/Workspace en général, mais ce point n'a pas été confirmé sur les pages Gemini Enterprise elles-mêmes)

---

## 4. APIs Google Cloud à activer

Le guide de démarrage rapide indique un flux d'activation groupée de quatre API via la console (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quickstart-gemini-enterprise) :

| API | Identifiant service | Rôle |
|---|---|---|
| Gemini Enterprise / Discovery Engine API | `discoveryengine.googleapis.com` | Cœur du produit : data stores, moteurs de recherche, agents, assistant, événements utilisateurs, contrôle d'accès (Source : https://docs.cloud.google.com/gemini/enterprise/docs/apis) |
| Vertex AI / AI Platform API | `aiplatform.googleapis.com` | Modèles génératifs sous-jacents ; sert aussi de périmètre de facturation pour les plafonds de dépenses (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quickstart-gemini-enterprise ; https://docs.cloud.google.com/gemini/enterprise/docs/configure-overages) |
| Cloud Storage API | `storage.googleapis.com` | Connexion de données stockées sur Cloud Storage (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quickstart-gemini-enterprise) |
| Identity and Access Management (IAM) API | `iam.googleapis.com` | Gestion des rôles et permissions (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quickstart-gemini-enterprise) |

Le rôle/permission requis pour activer ces API est `serviceusage.services.enable`, généralement inclus dans le rôle « Service Usage Admin » ou « Owner » (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quickstart-gemini-enterprise). La page de sécurité confirme la même liste (Vertex AI, Discovery Engine, Cloud Storage, IAM) comme API requises (Source : https://docs.cloud.google.com/gemini/enterprise/docs/security-overview).

Pour la distribution de licences multi-projets, l'API Discovery Engine doit également être activée sur chaque projet cible (Source : https://docs.cloud.google.com/gemini/enterprise/docs/licenses-faqs).

---

## 5. Rôles IAM requis

Gemini Enterprise définit des rôles prédéfinis spécifiques, distincts des rôles Google Cloud génériques :

| Rôle | Identifiant | Usage | Source |
|---|---|---|---|
| Gemini Enterprise Admin | `roles/discoveryengine.agentspaceAdmin` | Administration complète : paramètres, data stores, contrôle d'accès fin par app (`getIamPolicy`/`setIamPolicy`) | https://docs.cloud.google.com/gemini/enterprise/docs/iam-policy-for-apps ; https://docs.cloud.google.com/gemini/enterprise/docs/access-control |
| Gemini Enterprise User | `roles/discoveryengine.agentspaceUser` | Accès direct à des apps spécifiques (attribution au niveau app) | https://docs.cloud.google.com/gemini/enterprise/docs/iam-policy-for-apps ; https://docs.cloud.google.com/gemini/enterprise/docs/configure-identity-provider |
| Gemini Enterprise Restricted User | `roles/discoveryengine.agentspaceRestrictedUser` | Rôle de base obligatoire pour tout utilisateur licencié | https://docs.cloud.google.com/gemini/enterprise/docs/iam-policy-for-apps |
| Discovery Engine Editor | `roles/discoveryengine.editor` | Lecture/écriture sur toutes les ressources Discovery Engine, sans fonctions d'administration | https://docs.cloud.google.com/gemini/enterprise/docs/access-control |
| Discovery Engine Viewer | `roles/discoveryengine.viewer` | Lecture seule sur toutes les ressources Discovery Engine | https://docs.cloud.google.com/gemini/enterprise/docs/access-control |

**Règle de précédence critique** : les permissions IAM au niveau projet priment sur les politiques au niveau app. Pour restreindre des utilisateurs à des apps spécifiques, il faut retirer les rôles au niveau projet et les attribuer uniquement au niveau app (Source : https://docs.cloud.google.com/gemini/enterprise/docs/iam-policy-for-apps).

**Prérequis cumulatif** : un utilisateur final doit posséder à la fois le rôle IAM approprié **et** une licence valide pour accéder à Gemini Enterprise — l'un sans l'autre ne suffit pas (Source : https://docs.cloud.google.com/gemini/enterprise/docs/access-control).

Rôles additionnels utiles selon la tâche :
- **Billing Account Administrator** : requis pour visualiser/modifier les souscriptions et distribuer des licences entre projets (Source : https://docs.cloud.google.com/gemini/enterprise/docs/licenses-faqs)
- **Billing Account Viewer/Administrator** + permissions `monitoring.timeSeries.list` et `serviceconsumermanagement.quota.get` : requis pour consulter les coûts (Source : https://docs.cloud.google.com/gemini/enterprise/docs/view-costs)
- Permissions de base `resourcemanager.projects.get/list`, `serviceusage.services.list/get` nécessaires en complément des rôles spécifiques (Source : https://docs.cloud.google.com/gemini/enterprise/docs/access-control)

Des rôles personnalisés (« custom roles ») peuvent être créés si les rôles prédéfinis ne conviennent pas (Source : https://docs.cloud.google.com/gemini/enterprise/docs/access-control).

---

## 6. Fournisseur d'identité (SSO) et Workspace

Gemini Enterprise supporte deux catégories de fournisseurs d'identité (Source : https://docs.cloud.google.com/gemini/enterprise/docs/configure-identity-provider) :

1. **Google Identity** (recommandé) : supporte nativement les sources de données Google Workspace de premier niveau, et les sources tierces via fédération OAuth ; compatible avec des fournisseurs tiers supportant OIDC ou SAML 2.0 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/configure-identity-provider)
2. **Fournisseurs d'identité tiers via Workforce Identity Federation** : Microsoft Entra ID, Okta, ou tout fournisseur OIDC/SAML 2.0 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/configure-identity-provider)

**Point important** : les sources de données Microsoft 365 connectées par ingestion nécessitent obligatoirement Microsoft Entra ID et Workforce Identity Federation (Source : https://docs.cloud.google.com/gemini/enterprise/docs/configure-identity-provider).

Prérequis de configuration :
- Attribution préalable des rôles IAM appropriés aux administrateurs avant la configuration (Source : https://docs.cloud.google.com/gemini/enterprise/docs/configure-identity-provider)
- Détermination d'un identifiant utilisateur unique (généralement l'email) ; en cas d'emails multiples, un alias doit être ajouté (Source : https://docs.cloud.google.com/gemini/enterprise/docs/configure-identity-provider)
- Mapping d'attributs recommandé : `google.subject` vers l'email en minuscules (Source : https://docs.cloud.google.com/gemini/enterprise/docs/configure-identity-provider)
- Configuration SCIM nécessaire pour Entra ID et Okta afin de gérer les groupes et l'autocomplétion (Source : https://docs.cloud.google.com/gemini/enterprise/docs/configure-identity-provider)
- **Un seul type de fournisseur d'identité par localisation** ; changer de fournisseur nécessite de supprimer et recréer les data stores existants (Source : https://docs.cloud.google.com/gemini/enterprise/docs/configure-identity-provider)

Étapes de configuration dans la console : **Gemini Enterprise > Settings > Authentication > Add identity provider**, sélection du type, puis sauvegarde (Source : https://docs.cloud.google.com/gemini/enterprise/docs/configure-identity-provider).

---

## 7. Flux de provisioning — étapes de haut niveau

D'après le guide de démarrage rapide (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quickstart-gemini-enterprise) :

1. Se connecter avec un compte Google (ou en créer un si nouveau client Google Cloud)
2. Sélectionner un projet Google Cloud existant ou en créer un nouveau (rôle `roles/resourcemanager.projectCreator` requis pour la création)
3. Vérifier que la facturation Cloud est activée sur le projet
4. Activer les quatre API requises (Discovery Engine, Vertex AI, Cloud Storage, IAM) via le lien d'activation groupée de la console
5. Attribuer le rôle **Gemini Enterprise Admin** à son propre compte via la page IAM
6. Créer une app dans la console Gemini Enterprise (localisation globale par défaut)
7. Créer un data store en connectant Cloud Storage ou une autre source de données
8. Attendre l'indexation/synchronisation avant de tester (plusieurs minutes)

Aucune commande `gcloud` en ligne de commande n'est documentée pour ce parcours ; le flux décrit passe entièrement par la console (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quickstart-gemini-enterprise).

### 7.1 Création d'une app en détail

- Un data store existant est requis en amont ; sinon, il faut connecter une source Google ou tierce (Source : https://docs.cloud.google.com/gemini/enterprise/docs/create-app)
- **CMEK** (clés de chiffrement gérées par le client) doit être enregistré **avant** la création de l'app — les apps créées avant cet enregistrement restent non protégées (Source : https://docs.cloud.google.com/gemini/enterprise/docs/create-app)
- Sélection d'une localisation multi-régionale ; Google recommande la localisation **globale** par défaut sauf contrainte géographique de résidence des données (Source : https://docs.cloud.google.com/gemini/enterprise/docs/create-app)
- Limitation notable : impossible de connecter des data stores de type « site web » aux apps de recherche/assistant Gemini Enterprise (Source : https://docs.cloud.google.com/gemini/enterprise/docs/create-app)
- Méthode API REST disponible via `engines.create` avec paramètres `displayName`, `dataStoreIds`, `solutionType` (`SOLUTION_TYPE_SEARCH`), `appType` (`APP_TYPE_INTRANET`) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/create-app)

### 7.2 Licences et attribution

- Souscription mensuelle ou annuelle, avec renouvellement automatique possible, achetée via la console Google Cloud pour Standard, Plus et Pay-as-you-go (Source : https://docs.cloud.google.com/gemini/enterprise/docs/licenses)
- **Limites de sièges en self-serve** : maximum 25 sièges pour un compte de facturation en libre-service/revendeur ; maximum 1 000 sièges pour un compte de facturation facturé (invoiced) ; au-delà, il faut passer par une commande hors ligne via un représentant commercial (Source : https://docs.cloud.google.com/gemini/enterprise/docs/licenses)
- Attribution manuelle par email, ou automatique à la première connexion (Source : https://docs.cloud.google.com/gemini/enterprise/docs/licenses)
- Une même souscription peut couvrir plusieurs projets au sein du même compte de facturation, y compris à travers plusieurs organisations si elles partagent ce compte de facturation (Source : https://docs.cloud.google.com/gemini/enterprise/docs/licenses-faqs)
- Le nom d'une souscription **ne peut pas être modifié** après création (Source : https://docs.cloud.google.com/gemini/enterprise/docs/licenses-faqs)
- Une réduction du nombre de licences en cours de terme **n'est pas autorisée** — les changements ne prennent effet qu'au renouvellement ou en fin de terme (Source : https://docs.cloud.google.com/gemini/enterprise/docs/licenses-faqs)

---

## 8. Quotas — ce qui est mesuré et les limites par édition

### 8.1 Structure de pooling

- Les quotas fonctionnels (hors stockage/indexation) sont **mutualisés par édition**, au sein d'un même projet et d'une même localisation (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages)
- Les quotas de **stockage et d'indexation de données** sont mutualisés **entre toutes les éditions** au niveau projet/localisation (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages)
- Il n'y a pas de plafond individuel par utilisateur sauf configuration manuelle spécifique (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages)
- **Réinitialisation** : la plupart des fonctionnalités se réinitialisent quotidiennement à minuit heure du Pacifique (PT) ; les outils de développement IA se réinitialisent sur un cycle glissant de 7 jours à partir de la première utilisation (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages ; https://docs.cloud.google.com/gemini/enterprise/docs/feature-usage)

### 8.2 Tableau des quotas par édition (page actuelle, vérifiée)

*(Source pour l'ensemble du tableau : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages)*

| Fonctionnalité | Standard | Plus | EDU | EDU Pro | Frontline Starter | Frontline Worker |
|---|---|---|---|---|---|---|
| Stockage + indexation | 30 GiB | 75 GiB | 5 GiB | 50 GiB | 2 GiB | 2 GiB |
| Requêtes Assistant / jour | 160 | 200 | 40 | 200 | 20 | 40 |
| Création d'agent no-code / jour | 1 | 10 | 1 | 10 | s.o. | s.o. |
| Génération vidéo / jour | 2 | 3 | 1 | 3 | s.o. | 1 |
| Génération image / jour | 5 | 10 | 2 | 10 | s.o. | 2 |
| Deep Research / jour | 3 | 10 | 1 | 10 | s.o. | 1 |
| Crédit outils développeur IA | 10 $/mois | 15 $/mois | inclus | s.o. | s.o. | s.o. |

**Éditions marchés émergents / gouvernement/éducation** :
- Standard Emerging Market : 10 GiB de stockage, 40 requêtes/jour, 1 agent/jour (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages)
- EDU & Gouvernements : 3 GiB de stockage, 5 requêtes/jour (usage individuel uniquement) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages)

### 8.3 Édition Pay-as-you-go

- Nécessite un compte de facturation Cloud **facturé (invoiced)** avec une facture mensuelle active (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages)
- Aucune limite de quota fonctionnel : facturation intégrale à l'usage (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages)
- Stockage + indexation : **5 $ par GiB/mois** (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages)
- Autres fonctionnalités : tarification renvoyée vers la grille « Agent Platform » (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages)
- Absence de certaines fonctionnalités premium (accès prioritaire aux modèles, Deep Research) par rapport à Standard/Plus (Source : https://docs.cloud.google.com/gemini/enterprise/docs/editions)

### 8.4 Quotas techniques / système (API)

*(Source : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages)*

| Quota | Valeur |
|---|---|
| Data stores par projet | 100 (maximum technique : 500) |
| Engines (moteurs) par projet | 150 (maximum technique : 500) |
| Data stores régionaux | 100 par localisation |
| Documents régionaux | 10 000 000 par localisation |
| Requêtes de recherche / minute | 300 par projet |
| Requêtes de recherche régionales / minute | 300 par localisation |

---

## 9. Dépassements (overages) — modèle de facturation

### 9.1 Qui peut activer les dépassements et à quelles conditions

- Seul un administrateur **Gemini Enterprise Administrator** peut activer les dépassements (Source : https://docs.cloud.google.com/gemini/enterprise/docs/configure-overages)
- **Éligibilité obligatoire** : le projet doit disposer d'un compte de facturation Cloud **facturé (invoiced, non prépayé)**, et d'au moins une souscription active, hors essai gratuit, pour les éditions Standard, Plus ou Standard Emerging Market (Source : https://docs.cloud.google.com/gemini/enterprise/docs/configure-overages)
- **L'édition Pay-as-you-go ne supporte pas les dépassements** — tout son usage est déjà facturé à la consommation (Source : https://docs.cloud.google.com/gemini/enterprise/docs/configure-overages)

**Conséquence de scoping critique** : si le client ATECNA ne dispose que d'un compte de facturation Cloud en libre-service (carte bancaire, non facturé), il **ne pourra pas activer les dépassements** — les quotas deviennent alors des plafonds durs (« hard cap ») pour ce type de compte, malgré ce qui est décrit plus bas au §9.3.

### 9.2 Comportement par défaut avant activation

Lorsque le projet atteint son quota mutualisé pour une fonctionnalité, **l'usage de cette fonctionnalité s'arrête** tant que les dépassements ne sont pas activés (Source : https://docs.cloud.google.com/gemini/enterprise/docs/configure-overages). Les utilisateurs voient un message d'erreur « Usage limit reached » (Source : https://docs.cloud.google.com/gemini/enterprise/docs/manage-costs-overview).

### 9.3 Étapes pour activer les dépassements

*(Source : https://docs.cloud.google.com/gemini/enterprise/docs/configure-overages)*

1. Naviguer vers **Google Cloud console > Gemini Enterprise > Usage & Spending**
2. Sélectionner l'onglet **Usage**
3. Dans la section **Feature usage > Overage**, activer le bouton **Enabled**
4. Cocher les cases pour les éditions concernées (Standard, Plus, Standard Emerging)
5. Cliquer sur **Save changes**
6. Confirmer dans la boîte de dialogue de confirmation

### 9.4 Nature des plafonds : soft cap vs hard cap

- **Stockage + indexation** : le dépassement est **automatique** — dès que le quota est dépassé, la facturation supplémentaire s'applique sans action requise (« soft cap » de fait) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages ; confirmé également sur https://docs.cloud.google.com/gemini/enterprise/docs/overages)
- **Toutes les autres fonctionnalités** (requêtes Assistant, Deep Research, génération d'image/vidéo, création d'agents no-code) : le dépassement du quota **restreint la fonctionnalité** (hard cap) tant que l'administrateur n'a pas explicitement activé les dépassements payants (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages ; https://docs.cloud.google.com/gemini/enterprise/docs/overages)
- Citation exacte de la documentation : *« When your project reaches its pooled quota for a feature in Gemini Enterprise, feature usage stops unless you enable overages »* (Source : https://docs.cloud.google.com/gemini/enterprise/docs/configure-overages)

### 9.5 Avertissement sur l'absence de plafond de dépense

*« If you enable overages without setting a monthly spend limit, feature usage continues without restriction after your project exceeds its pooled quota, and you pay for all excess usage at pay-as-you-go overage rates »* (Source : https://docs.cloud.google.com/gemini/enterprise/docs/configure-overages).

**Il est donc fortement recommandé de configurer un plafond de dépense mensuel** via Cloud Billing, en sélectionnant **Vertex AI (`aiplatform.googleapis.com`)** comme périmètre de service — ce plafond s'applique aux apps Gemini Enterprise, à l'Agent Platform et aux outils de développement IA (Source : https://docs.cloud.google.com/gemini/enterprise/docs/configure-overages ; https://docs.cloud.google.com/gemini/enterprise/docs/manage-costs-overview). Quand ce plafond est atteint, *« overage usage is automatically stopped »* (Source : https://docs.cloud.google.com/gemini/enterprise/docs/manage-costs-overview). Des alertes de budget peuvent être configurées à 50 %, 80 % et 100 % du budget (Source : https://docs.cloud.google.com/gemini/enterprise/docs/manage-costs-overview).

### 9.6 Taux de dépassement — ⚠️ point de vigilance temporelle

La page **actuelle** (`quotas-and-overages`) indique uniquement un tarif précis pour le stockage (5 $/GiB/mois), et renvoie toutes les autres fonctionnalités vers « Agent Platform pricing » sans donner de taux fixe par unité (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages).

Une page distincte marquée comme **« legacy »** (`/gemini/enterprise/docs/overages`) donne des taux précis par fonctionnalité, mais précise explicitement qu'elle s'adresse uniquement aux clients ayant reçu un email intitulé *« [Billing Update] New Gemini Enterprise overage billing controls launching August 17, 2026 »*, et que les autres clients doivent se référer à la page `quotas-and-overages` actuelle (Source : https://docs.cloud.google.com/gemini/enterprise/docs/overages). **Étant donné que la date du jour (28/08/2026) est postérieure à cette bascule du 17/08/2026, il n'est pas certain que ces taux ci-dessous soient encore d'actualité pour tous les clients** — à vérifier au cas par cas selon le compte de facturation du client. ⚠️ Non vérifié comme étant les taux en vigueur actuellement pour l'ensemble des clients.

| Fonctionnalité | Unité | Taux (page legacy) |
|---|---|---|
| Stockage + indexation | GiB/mois | 5,00 $ |
| Requêtes Assistant | requête/jour | 0,10 $ |
| Génération vidéo | seconde | 0,40 $ |
| Génération image | image/jour | 0,02 $ |
| Deep Research | requête/jour | 4,00 $ |
| Création d'agent no-code | agents/jour | non précisé |

*(Source pour ce tableau : https://docs.cloud.google.com/gemini/enterprise/docs/overages — ⚠️ page legacy, à confirmer)*

Pour la tarification « Agent Platform » (référencée pour les autres fonctionnalités), des sources tierces indiquent des tarifs par token pour les modèles Gemini 3.7/3.6 Flash (0,75 $ / 3,75 $ par million de tokens entrée/sortie en tarif introductif jusqu'au 31/12/2026, puis 1,5 $ / 7,5 $ à partir du 01/01/2027), ainsi que des coûts de stockage de session et de calcul par vCPU-heure (Source : agrégation de résultats de recherche web, notamment via des extraits indexés de `cloud.google.com/products/gemini-enterprise-agent-platform/pricing` — ⚠️ Non vérifié, la page officielle n'a pas pu être chargée intégralement lors de cette recherche).

### 9.7 Suivi et visualisation des coûts

- Navigation : **Gemini Enterprise > Usage & Spending > onglet Billing**, affichant les coûts de dépassement et pay-as-you-go des 30 derniers jours (Source : https://docs.cloud.google.com/gemini/enterprise/docs/view-costs)
- Rôles requis : **Gemini Enterprise Administrator** + **Billing Account Viewer/Administrator**, ainsi que les permissions `monitoring.timeSeries.list` et `serviceconsumermanagement.quota.get` (Source : https://docs.cloud.google.com/gemini/enterprise/docs/view-costs)
- Trois catégories de coûts affichées : « Gemini Enterprise app », « Gemini Enterprise Agent Platform », « AI developer tools » (Source : https://docs.cloud.google.com/gemini/enterprise/docs/view-costs)
- **Important** : cette page n'affiche que les dépassements et le pay-as-you-go — elle **exclut les charges d'abonnement basées sur les licences** (Source : https://docs.cloud.google.com/gemini/enterprise/docs/view-costs)
- Désactiver la facturation du projet désactive également toutes les ressources produit associées (Source : https://docs.cloud.google.com/gemini/enterprise/docs/billing-questions)

---

## 10. Sécurité, conformité et résidence des données (éléments pertinents pour le scoping)

- **Chiffrement** : support CMEK (Customer Managed Encryption Keys) par défaut ; support EKM/HSM (External Key Manager / Hardware Security Module) avec limitations documentées (Source : https://docs.cloud.google.com/gemini/enterprise/docs/security-overview)
- **CMEK et Access Transparency (AXT) ne sont pas supportés en localisation `global`**, ni lorsque le « Grounding with Google Search » est activé (Source : https://docs.cloud.google.com/gemini/enterprise/docs/compliance-security-controls)
- **VPC Service Controls** : intégré pour les services Google Cloud ; les connecteurs tiers utilisent des points de terminaison publics hors du réseau Google, nécessitant des règles de pare-feu VPC restreignant les connexions sortantes aux FQDN des services externes (Source : https://docs.cloud.google.com/gemini/enterprise/docs/security-overview). Appliquer un périmètre VPC-SC sur un projet ayant déjà des data stores existants **n'est pas supporté** — il faut les supprimer et les recréer (Source : https://docs.cloud.google.com/gemini/enterprise/docs/use-vpc-service-controls)
- **Certifications de conformité** disponibles pour Standard et Plus (et Gemini Notebook Enterprise) : HIPAA, FedRAMP, ISO 27001/27017/27018/27701, SOC 1/2/3, PCI DSS, BSI C5:2020 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/compliance-security-controls)
- **Suppression de données** : sur demande utilisateur, sous 60 jours (Source : https://docs.cloud.google.com/gemini/enterprise/docs/security-overview)
- **Localisations disponibles** : multi-régions `eu` et `us`, et localisation `global` recommandée par défaut (meilleurs temps de réponse, dernières versions de modèles, fonctionnalités les plus récentes) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/locations)
- **Localisations pays (sur liste d'autorisation)** : Canada (`ca`), Inde (`in`), Japon (`asia-northeast1`), Singapour (`sg`), Royaume-Uni (`europe-west2`) — avec limitations fonctionnelles plus fortes qu'en `us`/`eu`/`global` (Source : https://docs.cloud.google.com/gemini/enterprise/docs/locations)
- **Modèles Gemini 3.7/3.6 Flash disponibles uniquement en `global`** ; génération vidéo indisponible en multi-région `us`/`eu` (Source : https://docs.cloud.google.com/gemini/enterprise/docs/locations)

**Implication de scoping** : un client ayant une exigence stricte de résidence des données en France/UE devra probablement choisir la région `eu` ou `europe-west2` (UK), ce qui **réduit l'accès à certaines fonctionnalités récentes** (derniers modèles, génération vidéo) par rapport à la localisation `global` (Source : https://docs.cloud.google.com/gemini/enterprise/docs/locations).

---

## 11. Compétences / rôles requis côté client

D'après l'ensemble des pages consultées, un projet de mise en œuvre nécessite généralement la coordination de plusieurs profils côté client :

1. **Un administrateur Google Cloud** disposant des droits pour créer/gérer un projet, activer les API, et attribuer des rôles IAM (`roles/resourcemanager.projectCreator`, Service Usage Admin) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quickstart-gemini-enterprise)
2. **Un administrateur de facturation (Billing Account Administrator)** pour l'achat des souscriptions, la distribution de licences entre projets, et l'activation des dépassements (Source : https://docs.cloud.google.com/gemini/enterprise/docs/licenses-faqs ; https://docs.cloud.google.com/gemini/enterprise/docs/configure-overages)
3. **Un administrateur Gemini Enterprise** (rôle `roles/discoveryengine.agentspaceAdmin`) pour la configuration fonctionnelle quotidienne : data stores, apps, contrôle d'accès, fournisseur d'identité (Source : https://docs.cloud.google.com/gemini/enterprise/docs/iam-policy-for-apps)
4. **Un administrateur Google Workspace et/ou IAM tiers (Entra ID/Okta)** pour la configuration du SSO et de la fédération d'identité, en particulier si des connecteurs Microsoft 365 sont utilisés (Entra ID + Workforce Identity Federation obligatoires dans ce cas) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/configure-identity-provider)
5. **Un référent sécurité/réseau** si VPC Service Controls, CMEK/EKM ou des restrictions de pare-feu pour les connecteurs tiers sont requis (Source : https://docs.cloud.google.com/gemini/enterprise/docs/use-vpc-service-controls ; https://docs.cloud.google.com/gemini/enterprise/docs/security-overview)

**Conclusion** : pour les éditions Standard/Plus/Pay-as-you-go, le setup nécessite bien un GCP admin **et** potentiellement un Workspace/IdP admin (si SSO tiers ou connecteurs Microsoft 365) — ce n'est **pas** un déploiement purement self-serve. Seule l'édition **Business** échappe à ce besoin d'un projet Google Cloud géré par l'IT (Source : https://docs.cloud.google.com/gemini/enterprise/docs/editions ; https://support.google.com/g/answer/17100048?hl=en — ⚠️ ce dernier point de la source Business en self-serve reste une source secondaire).

---

## Checklist de prérequis

Avant qu'un projet client ATECNA de mise en œuvre Gemini Enterprise (édition Standard/Plus/Pay-as-you-go) puisse démarrer, vérifier que le client dispose de :

- [ ] Un compte Google / organisation Google Cloud existante (ou volonté d'en créer une) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quickstart-gemini-enterprise)
- [ ] Un projet Google Cloud dédié (existant ou à créer), avec un titulaire du rôle `roles/resourcemanager.projectCreator` si création nécessaire (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quickstart-gemini-enterprise)
- [ ] Un compte de facturation Cloud actif et lié au projet (Source : https://docs.cloud.google.com/gemini/enterprise/docs/before-you-begin)
- [ ] **Précision du type de compte de facturation** : self-serve (carte bancaire, plafonné à 25 sièges, dépassements impossibles à activer) vs **facturé/invoiced** (jusqu'à 1 000 sièges, dépassements activables) — à clarifier dès le cadrage car cela conditionne le comportement en cas de dépassement de quota (Source : https://docs.cloud.google.com/gemini/enterprise/docs/licenses ; https://docs.cloud.google.com/gemini/enterprise/docs/configure-overages)
- [ ] Les 4 API activées : `discoveryengine.googleapis.com`, `aiplatform.googleapis.com`, `storage.googleapis.com`, `iam.googleapis.com` (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quickstart-gemini-enterprise)
- [ ] Un utilisateur désigné avec le rôle **Gemini Enterprise Admin** (`roles/discoveryengine.agentspaceAdmin`) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/iam-policy-for-apps)
- [ ] Un utilisateur désigné avec le rôle **Billing Account Administrator** pour la gestion des souscriptions et des dépassements (Source : https://docs.cloud.google.com/gemini/enterprise/docs/licenses-faqs)
- [ ] Décision sur le fournisseur d'identité : Google Identity natif, ou fédération tierce (Entra ID / Okta / autre OIDC-SAML) — avec configuration SCIM si Entra ID/Okta (Source : https://docs.cloud.google.com/gemini/enterprise/docs/configure-identity-provider)
- [ ] Si connecteurs Microsoft 365 prévus : Microsoft Entra ID + Workforce Identity Federation opérationnels (Source : https://docs.cloud.google.com/gemini/enterprise/docs/configure-identity-provider)
- [ ] Édition choisie et nombre de sièges validé par rapport aux seuils (25 en self-serve / 1 000 en invoiced / 150+ requis en amont pour Frontline) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/licenses ; https://docs.cloud.google.com/gemini/enterprise/docs/editions)
- [ ] Localisation/région choisie (`global` par défaut, ou `eu`/`us`/pays spécifique selon contraintes de résidence des données), avec validation des limitations fonctionnelles associées (Source : https://docs.cloud.google.com/gemini/enterprise/docs/locations)
- [ ] Décision sur l'activation des dépassements (overages) et définition d'un **plafond de dépense mensuel** sur le périmètre `aiplatform.googleapis.com` avant mise en production (Source : https://docs.cloud.google.com/gemini/enterprise/docs/configure-overages)
- [ ] Alertes de budget configurées (seuils 50/80/100 %) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/manage-costs-overview)
- [ ] Si CMEK requis : clé enregistrée **avant** la création de l'app (Source : https://docs.cloud.google.com/gemini/enterprise/docs/create-app)
- [ ] Si VPC Service Controls requis : périmètre créé **avant** la création des data stores (non applicable rétroactivement sans suppression/recréation) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/use-vpc-service-controls)
- [ ] Au moins un data store et une source de données identifiés pour la première app (Cloud Storage ou connecteur tiers ; les data stores de type site web ne sont pas supportés pour les apps recherche/assistant) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/create-app)
- [ ] Validation tarifaire finale avec un commercial Google Cloud (les prix par siège figurant en §2.2 restent ⚠️ non vérifiés officiellement lors de cette recherche)
- [ ] Confirmation à jour, auprès de Google ou du contact commercial, des taux de dépassement applicables au compte du client, la bascule tarifaire du 17/08/2026 mentionnée en §9.6 n'ayant pas pu être totalement clarifiée
