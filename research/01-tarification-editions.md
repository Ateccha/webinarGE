# Gemini Enterprise — Tarification & Éditions

*Document de référence interne ATECNA — compilé le 28/08/2026 à partir de sources primaires Google Cloud (pages produit, documentation officielle, notes de version) et de sources secondaires clairement identifiées. Google modifie fréquemment ces informations (au moins 3 changements documentés rien qu'en août 2026) : à revalider avant tout chiffrage client.*

---

## 0. Périmètre et clarification terminologique essentielle

Avant toute chose, il faut distinguer **cinq produits Google qui portent des noms proches et sont fréquemment confondus** :

| Produit | Ce que c'est | Facturation |
|---|---|---|
| **Gemini Enterprise (l'application)** | Plateforme agentique pour les métiers (recherche d'entreprise, agents, no-code) — objet de ce document | Par licence utilisateur / mois |
| **Gemini Enterprise Agent Platform** | Anciennement *Vertex AI* / *AI Platform* — plateforme technique pour développeurs (entraînement de modèles, IA générative à l'usage) | Paiement à l'usage (tokens, calcul, stockage) |
| **Application Gemini** (grand public / Workspace) | Assistant IA du quotidien, inclus gratuitement avec les licences Google Workspace | Inclus dans Workspace |
| **Gemini for Workspace (ancien add-on)** | Add-ons payants historiques "Gemini Business" (20$) et "Gemini Enterprise" (30$) pour Workspace | **Retirés en mars 2025**, fonctionnalités intégrées aux forfaits Workspace |
| **Google Agentspace** | Nom précédent du produit documenté ici, avant octobre 2025 | — |

Sur la question explicite « *Gemini Enterprise Agent Platform est-il inclus dans l'application Gemini Enterprise ?* », la FAQ officielle répond textuellement :

> « **Non.** Bien que les deux fassent partie de l'écosystème Gemini Enterprise, ils doivent être achetés séparément : Application Gemini Enterprise : service sur abonnement [...] facturée **par licence et par mois** [...]. Gemini Enterprise Agent Platform : plate-forme axée sur les développeurs (l'évolution de Vertex AI) [...] utilise la **facturation à l'usage**. »
(Source : https://cloud.google.com/gemini-enterprise/faq)

Le 9 octobre 2025, Google a renommé Agentspace en Gemini Enterprise ; toutes les capacités et agents existants ont migré automatiquement, sans changement fonctionnel de fond.
(Source : https://www.theregister.com/2025/10/09/google_rearranges_agentspace_into_gemini/ ; annonce officielle : https://cloud.google.com/blog/products/ai-machine-learning/introducing-gemini-enterprise)

**Ce document couvre exclusivement l'application Gemini Enterprise** (le produit à licence par utilisateur), pas la tarification des modèles Gemini via API/Vertex AI, ni l'app Gemini grand public, ni les anciens add-ons Workspace.

---

## 1. Éditions actuellement commercialisées

D'après la page officielle de comparaison des éditions (mise à jour le 27/08/2026, soit hier), Gemini Enterprise propose désormais **cinq éditions commerciales principales**, plus des variantes régionales/sectorielles :

1. **Business**
2. **Standard**
3. **Plus**
4. **Gemini Enterprise – Paiement à l'usage** *(nouvelle édition, lancée mi/fin août 2026)*
5. **Frontline** *(module complémentaire, pas une édition autonome)*

S'y ajoutent des éditions à accès restreint non couvertes en détail ici : **Education / Education Pro** (secteur académique) et des éditions **« Marchés émergents »** (Standard Emerging Market, Emerging Market EDU/gouvernements — accès sur éligibilité, à valider avec l'équipe compte Google).
(Source : https://docs.cloud.google.com/gemini/enterprise/docs/editions ; https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages)

### Nombre de sièges par édition

| Édition | Sièges |
|---|---|
| Business | 1 à 500 utilisateurs *(voir incohérence ci-dessous)* |
| Standard | 1 utilisateur ou plus (illimité) |
| Plus | 1 utilisateur ou plus (illimité) |
| Paiement à l'usage | 1 siège minimum pour démarrer |
| Frontline | 150 utilisateurs ou plus **de Standard ou Plus déjà existants** — Frontline n'est achetable qu'en complément |
(Source : https://docs.cloud.google.com/gemini/enterprise/docs/editions)

⚠️ **Incohérence entre sources officielles** : la page produit grand public (cloud.google.com/gemini-enterprise) et sa FAQ indiquent que l'édition Business cible « les petites entreprises et les équipes **jusqu'à 300 personnes** » (« 1-300 Places » dans l'encart tarifaire), alors que la documentation technique des éditions indique « 1 à **500** utilisateurs ». Les deux pages sont officielles et datées de la même période (août 2026) — à faire confirmer par le commercial Google Cloud avant de s'engager sur un chiffre précis pour un client proche de ce seuil.
(Sources : https://cloud.google.com/gemini-enterprise et https://docs.cloud.google.com/gemini/enterprise/docs/editions)

---

## 2. Tarification par édition (prix public affiché)

**Tous les tarifs Google Cloud sont affichés en USD** ; aucun tarif EUR spécifique n'est publié sur les pages officielles, y compris en version française (« Les tarifs sont indiqués en dollars américains (USD) »).
(Source : https://cloud.google.com/gemini-enterprise)

| Édition | Prix affiché (officiel, 28/08/2026) | Statut |
|---|---|---|
| **Business** | **21 $ USD** par licence utilisateur et par mois (« à partir de ») | Achat en libre-service possible, essai gratuit 30 jours |
| **Standard / Plus** | **30 $ USD** par licence utilisateur et par mois (« à partir de ») — **prix unique affiché conjointement pour les deux éditions** | Bouton « Contacter le service commercial » ou essai gratuit 30 jours |
| **Frontline** | **Non publié** — sur devis uniquement | Add-on, contact commercial obligatoire |
| **Paiement à l'usage** | Pas de frais d'abonnement fixe ; facturation selon la consommation | Nécessite un compte de facturation Cloud facturé (« invoiced ») |
(Source : https://cloud.google.com/gemini-enterprise, page consultée le 28/08/2026)

### ⚠️ Point d'attention majeur : différenciation Standard vs Plus

La page officielle actuelle **n'affiche plus de prix distinct pour Plus** — elle présente un bloc unique « Éditions Standard/Plus » à partir de 30 $/utilisateur/mois. C'est un changement par rapport au lancement.

Au lancement (9 octobre 2025), la presse rapportait, en citant Google Cloud : *« Gemini Enterprise targets large organizations, starting at a monthly fee of $30 per person, while Gemini Business [...] costs $21 per person each month »* — donc déjà une formulation « à partir de 30 $ » sans prix Plus distinct clairement publié.
(Source : https://www.cnbc.com/2025/10/09/google-launches-gemini-enterprise-to-boost-ai-agent-use-at-work.html)

Plusieurs sites tiers (agrégateurs/revendeurs, non officiels) avancent des chiffres plus précis pour Plus :
- ⚠️ **Non vérifié** : Standard à 30 $/mois (engagement 12 mois) ou 35 $/mois (sans engagement) ; Plus à 50 $/mois (engagement annuel) ou 60 $/mois (sans engagement).
(Sources, à traiter comme non officielles : https://coworker.ai/blog/gemini-enterprise-pricing ; https://www.gosearch.ai/faqs/gemini-enterprise-pricing/)

**Recommandation ATECNA** : ne jamais citer les chiffres 35 $/50 $/60 $ à un client comme des prix officiels Google. Ils proviennent de revendeurs/blogs tiers, pas de cloud.google.com. Pour tout devis réel, obtenir un tarif nominatif via l'interlocuteur commercial Google Cloud (le prix par licence dépend du volume, de la durée d'engagement et de la relation commerciale — Google le confirme lui-même : *« Pour en savoir plus, contactez votre assistant commercial Google Cloud »*).
(Source : https://cloud.google.com/gemini-enterprise)

### Frontline — estimation de coût total

Frontline nécessitant un minimum de 150 licences Standard/Plus **avant** de pouvoir être acheté, le ticket d'entrée minimal est donc de facto : 150 × 30 $ (au moins) = **4 500 $/mois de licences Standard/Plus**, avant même le premier siège Frontline. Le prix des sièges Frontline eux-mêmes n'est pas publié.
(Déduction à partir de : https://docs.cloud.google.com/gemini/enterprise/docs/editions — non un chiffre officiel Google, calcul ATECNA)

### Essai gratuit

Un essai gratuit de **30 jours** est proposé aussi bien pour l'édition Business que pour Standard/Plus, directement depuis la page produit (« Démarrer votre essai de 30 jours »).
(Source : https://cloud.google.com/gemini-enterprise)
⚠️ Non vérifié : les conditions précises de l'essai (carte bancaire requise ou non, quotas pendant l'essai, édition assignée par défaut) ne sont pas détaillées sur les pages consultées.

---

## 3. Tableau comparatif des fonctionnalités par édition

Tableau reconstitué intégralement depuis la documentation officielle (dernière mise à jour 27/08/2026) :

| Fonctionnalité | Business | Standard | Plus | Paiement à l'usage | Frontline |
|---|:---:|:---:|:---:|:---:|:---:|
| Stockage et indexation des données par utilisateur | 25 Gio (mutualisé) | 30 Gio (mutualisé) | 75 Gio (mutualisé) | Paiement à l'usage | 2 Gio (mutualisé) |
| Connecteurs sélectionnés pertinents par segment | ✔ | ✔ | ✔ | ✔ | ✔ |
| Accès à l'écosystème complet de connecteurs de données | — | ✔ | ✔ | ✔ | ✔ |
| Recherche d'entreprise tenant compte des autorisations | ✔ | ✔ | ✔ | ✔ | ✔ |
| Ancrage sur données d'entreprise (Google + tiers) | ✔ | ✔ | ✔ | ✔ | ✔ |
| Accès prioritaire aux derniers modèles Gemini | — | ✔ | ✔ | ✔ | — |
| Recherche + génération de texte combinées | ✔ | ✔ | ✔ | ✔ | ✔ |
| Génération de contenus multimédias (images/vidéos) | ✔ | ✔ | ✔ | ✔ | ✔ |
| Ancrage recherche Google / ancrage Web | ✔ | ✔ | ✔ | ✔ | ✔ |
| Tâches et actions d'agent prédéfinies | ✔ | ✔ | ✔ | ✔ | ✔ |
| Discussion avec notebooks Gemini Notebook Enterprise publiés | ✔ | ✔ | ✔ | — | ✔ |
| Création et publication de notebooks Gemini Notebook Enterprise | ✔ | ✔ | ✔ | — | — |
| Gemini Code Assist Standard | — | ✔ | ✔ | — | — |
| Création d'agents personnalisés no-code (aperçu) | ✔ | ✔ | ✔ | ✔ | — |
| Utilisation d'agents personnalisés no-code | ✔ | ✔ | ✔ | ✔ | ✔ |
| Deep Research (Google) | ✔ | ✔ | ✔ | ✔ | ✔ |
| Data Insights (Google) | — | ✔ | ✔ | ✔ | ✔ |
| Agents full-code externes (ADK, tiers) | — | ✔ | ✔ | ✔ | ✔ * |
| Accès au marketplace des agents | — | ✔ | ✔ | ✔ | ✔ |
| Gouvernance et administration de base des agents | ✔ | ✔ | ✔ | ✔ | — |
| Sécurité et conformité de niveau entreprise (VPC-SC, CMEK, Access Transparency, résidence des données, HIPAA, FedRAMP High) | — | ✔ | ✔ | ✔ | ✔ |
| Outils IA pour les développeurs (Antigravity, Android Studio) | — | ✔ | ✔ | ✔ | — |

*\* Avec Frontline, les utilisateurs ne peuvent accéder qu'aux agents déjà développés et provisionnés par leur administrateur — pas de création.*
(Source : https://docs.cloud.google.com/gemini/enterprise/docs/editions)

Les fonctionnalités de sécurité avancées (VPC Service Controls, clés de chiffrement gérées par le client, Access Transparency, résidence des données, conformité HIPAA et FedRAMP High) sont réservées à Standard et Plus.
(Source : https://cloud.google.com/gemini-enterprise)

Les outils de développement Google Antigravity et Gemini dans Android Studio sont en cours de déploiement progressif pour Standard/Plus et ne sont, à ce jour, disponibles que pour un groupe limité de clients.
(Source : https://cloud.google.com/gemini-enterprise)

---

## 4. Conditions contractuelles

- **Type d'abonnement** : mensuel ou annuel, au choix, avec option de renouvellement automatique activable/désactivable.
(Source : https://docs.cloud.google.com/gemini/enterprise/docs/licenses)
- **Plafonds de sièges selon le type de compte de facturation**, lorsque l'abonnement est géré directement dans la console Google Cloud :
  - Comptes de facturation en libre-service (en ligne) et revendus : **25 licences maximum** par compte.
  - Comptes de facturation avec paiement sur facture (hors connexion / « invoiced »): **1 000 licences maximum** par compte.
  - Au-delà, il faut passer par une commande hors connexion via le conseiller commercial Google Cloud, ou demander une exemption.
(Source : https://docs.cloud.google.com/gemini/enterprise/docs/licenses — confirmé par la note de version du 19/08/2026 : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes)
- **Résiliation** : il faut désactiver le renouvellement automatique ; l'abonnement reste actif (et facturé) jusqu'à la fin de la période en cours.
- **Délai de grâce en cas de résiliation anticipée** : 7 jours pendant lesquels les licences passent en état « Désactivation » avant expiration complète, pour permettre une migration sans coupure de service.
(Source : https://docs.cloud.google.com/gemini/enterprise/docs/licenses)
- Un abonnement Standard ou Plus donne aussi accès à **Gemini Code Assist Standard** dans les IDE compatibles, mais ces licences doivent être attribuées séparément depuis les pages d'administration Gemini Code Assist (non incluses automatiquement).
(Source : https://docs.cloud.google.com/gemini/enterprise/docs/licenses)
- Le **Paiement à l'usage n'est disponible que pour les comptes de facturation « facturés » (invoiced)** ; il faut, en plus, que le projet ait reçu un e-mail spécifique confirmant l'activation des nouveaux contrôles de facturation des dépassements lancés le 17 août 2026.
(Source : https://docs.cloud.google.com/gemini/enterprise/docs/editions)

### Gemini Notebook Enterprise (NotebookLM) en licence séparée

Il est possible d'acheter Gemini Notebook Enterprise **indépendamment** de l'application Gemini Enterprise, jusqu'à **5 000 licences**, en abonnement mensuel ou annuel avec renouvellement automatique optionnel. Au-delà de 5 000 licences, il faut contacter le service commercial.
(Source : https://cloud.google.com/gemini-enterprise/faq)
⚠️ Non vérifié : un chiffre de ~9 $/licence est avancé par un site tiers (coworker.ai) pour NotebookLM Enterprise autonome — aucune confirmation officielle trouvée.

---

## 5. Quotas inclus et fonctionnement des coûts à l'usage (au-delà du siège)

C'est le point le plus complexe et le plus important pour un chiffrage client : **le prix par siège n'inclut qu'un quota d'usage quotidien**, mutualisé (« pooled ») entre tous les utilisateurs d'une même édition, dans un même projet et une même localisation.

### 5.1 Principe de mutualisation

- Sauf pour le stockage/indexation (mutualisé projet+localisation, toutes éditions confondues), chaque quota fonctionnalité est mutualisé **par édition**, par projet et par localisation.
- Exemple donné explicitement par Google : avec 100 licences Standard (160 requêtes Assistant/jour/licence) et 50 licences Plus (200 requêtes/jour/licence) dans le même projet/localisation, on obtient deux pools séparés : 16 000 requêtes/jour pour le pool Standard, 10 000 requêtes/jour pour le pool Plus — non cumulables entre eux.
- Un utilisateur individuel n'est pas plafonné à sa propre part théorique : « tous les utilisateurs de l'édition puisent dans le pool partagé de leur édition jusqu'à ce qu'il soit épuisé ».
(Source : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages)

### 5.2 Quotas quotidiens par édition (Standard vs Plus)

| Fonctionnalité | Standard | Plus |
|---|---|---|
| Stockage et indexation | 30 Gio | 75 Gio |
| Assistant (requêtes de chat) | 160 requêtes/jour/licence | 200 requêtes/jour/licence |
| Création d'agents no-code | 1 agent/jour | 10 agents/jour |
| Génération de vidéos | 2 demandes/jour | 3 demandes/jour |
| Génération d'images | 5 images/jour | 10 images/jour |
| Deep Research | 3/jour | 10/jour |
| Crédit outils IA développeurs (Antigravity) | 10 $/utilisateur/mois | 15 $/utilisateur/mois |
(Source : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages)

Frontline (Starter : 20 requêtes Assistant/jour ; Worker : 40/jour, avec accès Deep Research 1/jour et génération d'image/vidéo limitée) et les éditions Business/EDU ont leurs propres grilles de quotas, plus restrictives.
(Source : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages)

Note technique sur les crédits Antigravity : bien qu'exprimés en montant mensuel par utilisateur, ils sont en réalité appliqués sur une **fenêtre glissante de 7 jours**, sous forme de pool partagé (montant mensuel ÷ 4 × nombre total de licences) ; le quota inutilisé n'est **pas reporté** à la semaine suivante.
(Source : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages)

### 5.3 Dépassements (« overages »)

- Les **dépassements sont pris en charge uniquement pour Standard, Plus et Standard Emerging Market** — pas pour Business, ni pour Frontline.
- Ils exigent un compte de facturation Cloud « facturé » (invoiced) et au moins un abonnement actif hors essai gratuit.
- Sans activation des dépassements, l'usage est simplement bloqué une fois le quota épuisé (message « Limite d'utilisation atteinte »), jusqu'au renouvellement du quota ou du cycle de facturation suivant.
- Tarif de dépassement du **stockage/indexation : 5 $ par Gio et par mois**, calculé au prorata (exemple officiel : 30 Gio en excédent pendant 1 jour sur un mois de 30 jours = 5 $).
- Pour les autres fonctionnalités (requêtes Assistant, génération d'images/vidéos, Deep Research, outils no-code, outils dev IA), le dépassement est facturé **aux « Tarifs d'Agent Platform »**, c'est-à-dire selon la grille de tarification à l'usage de Vertex AI / IA générative (tokens, calcul) — pas un tarif forfaitaire par requête publié séparément pour Gemini Enterprise.
- Les frais de dépassement sont en outre soumis à des **frais d'assistance variables** selon le niveau de support souscrit.
(Source : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages)

⚠️ **Point de vigilance commercial** : cela signifie que le coût réel d'un déploiement Gemini Enterprise à forte intensité d'usage dépend directement des tarifs Vertex AI/Gemini API sous-jacents (tokens d'entrée/sortie, génération d'image/vidéo), qui évoluent indépendamment et par modèle. Un chiffrage précis des dépassements nécessite de connaître le modèle Gemini activé (ex. Gemini 3.6/3.7 Flash) et le volume de tokens estimé — hors périmètre de ce document, à traiter avec la page tarifs Vertex AI dédiée à l'IA générative.

### 5.4 Contrôle des dépenses (nouveauté août 2026)

Fonctionnalité de gestion des dépassements et plafonds de dépenses généralisée le **11-12 août 2026** (note de version officielle) :
- Un administrateur peut définir une **limite de dépenses mensuelle** dans Cloud Billing (champ d'application « Vertex AI / aiplatform.googleapis.com »), couvrant à la fois l'application Gemini Enterprise, Gemini Enterprise Agent Platform et les outils IA développeurs.
- Une fois la limite atteinte, l'usage en dépassement est automatiquement stoppé (avec un délai de quelques minutes, pouvant entraîner un léger dépassement facturé).
- **Alertes budgétaires par e-mail à 50 %, 80 % et 100 %** du budget configuré, envoyées aux administrateurs de facturation (destinataires personnalisables). Il n'existe **pas** d'alerte automatique native dans l'application Gemini Enterprise elle-même en dehors de ce mécanisme Cloud Billing.
(Source : https://docs.cloud.google.com/gemini/enterprise/docs/manage-costs-overview)

La presse spécialisée évoque également une future fonctionnalité de tarification « heures creuses » offrant jusqu'à 50 % de réduction pour différer certaines tâches — ⚠️ **fonctionnalité annoncée mais non encore confirmée sur la documentation officielle consultée**, à considérer comme une intention produit plutôt qu'une offre active.
(Source secondaire : https://www.vktr.com/ai-platforms/google-adds-pay-as-you-go-pricing-and-spending-caps-to-gemini-enterprise-as-ai-bills-balloon/)

---

## 6. Édition Paiement à l'usage — nouveauté récente

Édition lancée avec les contrôles de facturation associés autour du **17 août 2026** (email officiel requis : « [Billing Update] New Gemini Enterprise overage billing controls launching August 17, 2026 »).
(Source : https://docs.cloud.google.com/gemini/enterprise/docs/editions)

Caractéristiques :
- **Aucun frais d'abonnement fixe ni engagement minimum** — facturation intégralement à l'usage.
- **Aucune limite de quota mutualisé** : « vous payez ce que vous utilisez ».
- Nécessite un compte de facturation Cloud facturé (invoiced) avec facture mensuelle active.
- 1 siège minimum pour démarrer.
(Source : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages ; https://docs.cloud.google.com/gemini/enterprise/docs/editions)

Cette édition ne dispose pas des crédits Antigravity inclus « de base » (contrairement à Standard/Plus).
(Déduit de : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages)

---

## 7. Chronologie des évolutions (pour comprendre la volatilité de l'offre)

| Date | Évènement | Source |
|---|---|---|
| Avant oct. 2025 | Produit connu sous le nom **Google Agentspace** | theregister.com/2025/10/09 |
| Mars 2025 | Retrait des anciens add-ons Workspace « Gemini Business » (20 $) et « Gemini Enterprise » (30 $), fonctionnalités intégrées aux forfaits Workspace | (mentionné par des sources tierces — ⚠️ à revérifier auprès de Google Workspace directement) |
| 9 oct. 2025 | Lancement officiel de **Gemini Enterprise** (rebranding d'Agentspace) ; tarifs annoncés : Business 21 $, Standard/Enterprise à partir de 30 $ | cnbc.com/2025/10/09 ; cloud.google.com/blog/.../introducing-gemini-enterprise |
| 11-12 août 2026 | Généralisation des dépassements, plafonds de dépenses et alertes budgétaires (comptes facturés) | docs.cloud.google.com/.../release-notes |
| 17 août 2026 | GA des outils IA développeurs (Antigravity 2.0, Antigravity CLI, Android Studio) pour Standard/Plus/PAYG ; lancement des contrôles de facturation des dépassements | docs.cloud.google.com/.../release-notes |
| 19 août 2026 | Formalisation des plafonds de sièges par type de compte (25 en libre-service / 1 000 en facturé) | docs.cloud.google.com/.../release-notes |
| 27 août 2026 | Dernière mise à jour connue de la page de comparaison des éditions | docs.cloud.google.com/gemini/enterprise/docs/editions |

---

## 8. Synthèse pour un chiffrage ATECNA

1. **Seul un prix plancher est public** : 21 $/mois (Business) et « à partir de 30 $/mois » (Standard/Plus indifférenciés). **Il n'existe aucun tarif Plus officiellement publié** au 28/08/2026 — tout devis Plus doit passer par un commercial Google Cloud.
2. **Le prix du siège n'achète qu'un quota quotidien** ; au-delà, la facturation bascule sur les tarifs Vertex AI/Agent Platform à l'usage (tokens, images, vidéos) — un poste de coût variable à modéliser séparément selon l'intensité d'usage prévue du client.
3. **Frontline n'est jamais un point d'entrée** : il faut déjà 150 licences Standard/Plus payantes en place, et son tarif propre n'est pas public.
4. **Le Paiement à l'usage est réservé aux comptes de facturation « invoiced »** — à vérifier systématiquement en amont côté client (un compte self-service standard ne pourra pas y accéder directement).
5. **Toujours confirmer les seuils de sièges avec le commercial Google** avant de les citer au client : la documentation officielle elle-même se contredit entre 300 et 500 utilisateurs maximum pour Business.
6. Pour tout engagement dépassant 25 licences en libre-service ou nécessitant du Frontline/EDU/Marchés émergents, un accompagnement commercial Google Cloud est obligatoire — ce qui est cohérent avec un rôle d'intégrateur/revendeur comme ATECNA.

---

## 9. Sources consultées

**Sources primaires (Google, officielles) :**
- https://cloud.google.com/gemini-enterprise
- https://cloud.google.com/gemini-enterprise/faq
- https://docs.cloud.google.com/gemini/enterprise/docs/editions
- https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages
- https://docs.cloud.google.com/gemini/enterprise/docs/licenses
- https://docs.cloud.google.com/gemini/enterprise/docs/manage-costs-overview
- https://docs.cloud.google.com/gemini/enterprise/docs/release-notes
- https://cloud.google.com/blog/products/ai-machine-learning/introducing-gemini-enterprise
- https://cloud.google.com/products/gemini-enterprise-agent-platform/pricing (pour distinguer l'Agent Platform, hors périmètre tarifaire de ce document)

**Sources secondaires (presse spécialisée, à titre de corroboration seulement) :**
- https://www.cnbc.com/2025/10/09/google-launches-gemini-enterprise-to-boost-ai-agent-use-at-work.html
- https://www.theregister.com/2025/10/09/google_rearranges_agentspace_into_gemini/
- https://www.vktr.com/ai-platforms/google-adds-pay-as-you-go-pricing-and-spending-caps-to-gemini-enterprise-as-ai-bills-balloon/
- https://www.techrepublic.com/article/news-google-gemini-enterprise-pay-as-you-go-pricing/

**Sources tierces non officielles (chiffres non confirmés, cités uniquement pour signaler ce qui circule sur le marché — ⚠️ Non vérifié) :**
- https://coworker.ai/blog/gemini-enterprise-pricing
- https://www.gosearch.ai/faqs/gemini-enterprise-pricing/
