# Gemini Enterprise — Antigravity, Crédits & Cas d'usage clients

*Document de référence interne ATECNA — recherche effectuée le 28/08/2026. Toute affirmation non vérifiable via une source primaire est explicitement signalée "⚠️ Non vérifié".*

## Partie 1 — Intégration de Google Antigravity dans les licences Gemini Enterprise

### 1.1 Nom exact du produit et clarification terminologique importante

Il existe **deux familles d'outils de développement Google distinctes et actuellement actives en parallèle** — il ne faut pas les confondre :

1. **Google Antigravity** — plateforme agentique de développement (IDE de type "chat-first", CLI, SDK) annoncée le 18 novembre 2025 aux côtés de Gemini 3, en preview publique dès son annonce (Source : https://en.wikipedia.org/wiki/Google_Antigravity). C'est **ce produit qui est désormais inclus dans Gemini Enterprise** (voir 1.2).
2. **Gemini Code Assist Standard / Enterprise** — un produit distinct de la gamme "Gemini for Google Cloud", assistant IDE plus classique (extension dans VS Code/JetBrains), qui **continue d'exister comme produit séparé** et n'est pas celui concerné par le bundle objet de cette note (Source : https://docs.cloud.google.com/gemini/docs/codeassist/overview).

Par ailleurs, pour les comptes **individuels** (Gemini Code Assist for individuals, Google AI Pro, Google AI Ultra), Google a mis fin le 18 juin 2026 aux extensions IDE "Gemini Code Assist" et à "Gemini CLI", au profit d'Antigravity / Antigravity CLI (Source : https://developers.googleblog.com/an-important-update-transitioning-gemini-cli-to-antigravity-cli/). Cette transition ne concerne que le grand public/les comptes individuels, pas directement le sujet de ce document, mais explique pourquoi le nom "Antigravity" a supplanté "Gemini CLI" dans la communication récente de Google.

**Conclusion terminologique : le produit correctement nommé pour ce document est "Google Antigravity".**

### 1.2 Le bundle Gemini Enterprise + Antigravity (annonce du 21 août 2026)

Le 21 août 2026, Google a annoncé qu'Antigravity est désormais **inclus dans les abonnements Gemini Enterprise, sans coût additionnel** :

> « Antigravity is available now as part of eligible Gemini Enterprise app subscriptions, including out-of-the-box administrative and spend controls. »
(Source : https://cloud.google.com/blog/products/ai-machine-learning/expanding-google-antigravity-for-enterprise-customers)

> « Equipping your developers with advanced agentic tools shouldn't mean managing separate add-on licenses, invoices, billing consoles or security settings. »
(Source : https://cloud.google.com/blog/products/ai-machine-learning/expanding-google-antigravity-for-enterprise-customers)

Cette annonce est corroborée par la presse spécialisée : « Google announced on August 21 that Antigravity, its autonomous coding agent, is now included in Gemini Enterprise Standard and Plus subscriptions at no additional cost » (Source : https://enterprisedna.co/resources/news/google-antigravity-gemini-enterprise-bundled-ai-coding-agents-august-2026/) et « Antigravity now comes with Gemini Enterprise Standard and Plus subscriptions at no additional cost » (Source : https://itbrief.asia/story/google-adds-antigravity-to-gemini-enterprise-subscriptions).

### 1.3 Quelles éditions Gemini Enterprise incluent Antigravity ?

D'après la documentation officielle Google Cloud, l'accès aux outils de développement IA (dont Antigravity) nécessite l'une des éditions suivantes :

> « You must have a subscription to the Gemini Enterprise Standard, Plus, Standard Emerging Market, or Pay-as-you-go edition. »
(Source : https://docs.cloud.google.com/gemini/enterprise/docs/ai-developer-tools-overview)

Soit, de manière consolidée à partir de plusieurs sources concordantes (blog Google Cloud, blog Antigravity, documentation officielle) :

| Édition Gemini Enterprise | Antigravity inclus ? |
|---|---|
| **Standard** | ✅ Oui, sans coût additionnel |
| **Plus** | ✅ Oui, sans coût additionnel |
| **Standard Emerging Market** | ✅ Oui |
| **Pay-as-you-go** | ✅ Oui (accès confirmé par la doc officielle, modèle de facturation à la consommation) |
| **Business** | ⚠️ Non confirmé comme inclus — la documentation officielle exclut cette édition de la liste d'éligibilité et redirige vers une documentation séparée : « This documentation set is for the Standard, Plus, Pay-as-you-go, and Frontline editions of Gemini Enterprise. For the Business edition documentation, see the Gemini Enterprise - Business edition Help Center. » (Source : https://docs.cloud.google.com/gemini/enterprise/docs/ai-developer-tools-overview) |
| **Frontline** | ⚠️ Non vérifié — mentionnée dans le périmètre de la documentation générale, mais absente de la phrase d'éligibilité explicite citée ci-dessus. Statut ambigu dans les sources consultées. |

**Sources multiples confirmant Standard/Plus/Standard Emerging Market comme le cœur du périmètre annoncé :**
- « Google Antigravity in Gemini Enterprise is available today for eligible Gemini Enterprise Standard, Plus, and Standard Emerging Market licenses, with broader support coming soon. » (Source : https://antigravity.google/blog/antigravity-enterprise)
- « The update expands access beyond Antigravity's standalone surfaces and adds it to Gemini Enterprise Standard, Plus, and Standard Emerging Market subscriptions. » (Source : https://itbrief.asia/story/google-adds-antigravity-to-gemini-enterprise-subscriptions)

L'édition **Business** de Gemini Enterprise (l'entrée de gamme, ~21 $/utilisateur/mois selon des sources tierces — voir 1.6) semble donc **exclue** de ce bundle à ce stade, mais aucune source consultée ne le dit de façon 100% explicite et univoque ("Business n'a pas Antigravity") — c'est une déduction à partir du périmètre documentaire. ⚠️ **À confirmer directement auprès d'un représentant commercial Google Cloud avant toute communication client ferme sur ce point.**

### 1.4 Crédits ou quotas inclus — chiffres en dollars/tokens

**Point central de la demande initiale : aucune source consultée ne publie de montant précis (en dollars ou en tokens/requêtes) correspondant au quota "inclus" avec une licence Gemini Enterprise.**

Ce que les sources officielles confirment concernant la gestion des quotas et dépenses :

> « Administrators can set monthly project-level budget caps directly in the Billing console, with additional per-user and team controls rolling out later this year. » (Source : https://cloud.google.com/blog/products/ai-machine-learning/expanding-google-antigravity-for-enterprise-customers)

> « Shared token pools provide flexibility to high-demand teams, preventing purchased quota from sitting idle across the organization. » (Source : https://cloud.google.com/blog/products/ai-machine-learning/expanding-google-antigravity-for-enterprise-customers)

> « Administrators can opt into overages with monthly spend caps, smoothly transitioning excess usage to standard consumption-based rates. » (Source : https://cloud.google.com/blog/products/ai-machine-learning/expanding-google-antigravity-for-enterprise-customers)

> « Centralized usage tracking provides visibility into token consumption, API calls, and developer activity. » (Source : https://cloud.google.com/blog/products/ai-machine-learning/expanding-google-antigravity-for-enterprise-customers)

La documentation technique Antigravity Enterprise distingue deux modèles d'accès, sans détailler de chiffres :

> « Gemini Enterprise Agent Platform — Connect directly to Agent Platform API to use Antigravity with consumption-based billing » (accès sans licence Gemini Enterprise, facturation 100% à la consommation)
> « Gemini Enterprise license — Provides access to included quotas, managed overages as well as advanced administrative controls » (accès via licence, avec des « quotas inclus » dont le volume n'est pas publié)
(Source : https://antigravity.google/docs/enterprise/)

**⚠️ Non vérifié : le volume exact des "quotas inclus" (en $ ou en tokens) n'est publié dans aucune des sources consultées** (blog Google Cloud, blog Antigravity, documentation Antigravity Enterprise, presse spécialisée Enterprise DNA/ITBrief/The Register). Il est probable que ce chiffre dépende du contrat/de l'édition et ne soit communiqué qu'au moment de la vente (devis Google Cloud ou revendeur). **Ne pas avancer de chiffre à un client sans confirmation directe par Google Cloud ou un revendeur agréé.**

**Note complémentaire (à recouper avec le document 02-prerequis-quotas.md) : la page officielle des quotas indique un « crédit outils IA développeurs » de 10 $/utilisateur/mois pour Standard et 15 $/utilisateur/mois pour Plus, appliqué sur un pool partagé en fenêtre glissante de 7 jours, non reporté d'une semaine sur l'autre (Source : https://docs.cloud.google.com/gemini/enterprise/docs/quotas-and-overages).** Ce chiffre est le seul montant précis trouvé à travers l'ensemble de cette recherche pour le crédit Antigravity inclus — à confirmer qu'il correspond bien au même bundle que celui annoncé le 21 août 2026.

### 1.5 ⚠️ Point de vigilance — Ne pas confondre avec l'offre "100 $ de crédits AI Ultra"

Les recherches font remonter une offre distincte qu'il ne faut **pas** attribuer à Gemini Enterprise :

> « For a limited time, we're offering new and existing Google AI Ultra subscribers USD $100 in bonus AI credits [for Antigravity], activating once you hit your plan's quota limit. »
(Source : https://antigravity.google/blog/changes-to-antigravity-plans)

Cette offre concerne les abonnés **individuels/grand public "Google AI Ultra"** (un abonnement personnel à 200 $/mois, distinct de Gemini Enterprise qui est un produit B2B vendu par siège). Elle avait une date limite de réclamation (25 mai 2026), donc probablement déjà expirée à la date de rédaction (28 août 2026). **Ce crédit de 100 $ n'a aucun lien confirmé avec les licences Gemini Enterprise** — il ne doit pas être cité comme un avantage du bundle entreprise.

### 1.6 Contrôles de sécurité et prérequis techniques (contexte complémentaire)

- Sandboxing configurable de l'espace de travail, contrôle des accès navigateur et serveurs MCP, journalisation d'audit centralisée capturant prompts, réponses et métadonnées (Source : https://enterprisedna.co/resources/news/google-antigravity-gemini-enterprise-bundled-ai-coding-agents-august-2026/).
- Prérequis techniques : compte de facturation Cloud actif, activation de l'API Agent Platform (`aiplatform.googleapis.com`), authentification SSO avec compte professionnel (Source : https://antigravity.google/docs/enterprise/).
- Extensions IDE disponibles : Visual Studio Code, Visual Studio, JetBrains, Zed, en plus de l'app desktop et de la CLI existantes ; une source mentionne aussi Xcode (Source : https://antigravity.google/docs/enterprise/ ; https://cloud.google.com/blog/products/ai-machine-learning/expanding-google-antigravity-for-enterprise-customers).

### 1.7 Repères de tarification Gemini Enterprise (sources tierces, non officielles Google)

⚠️ Non vérifié sur une page de tarification officielle Google directement accessible (la page `cloud.google.com/gemini-enterprise/pricing` retourne une erreur 404 au moment de la recherche). Les chiffres ci-dessous proviennent d'agrégateurs tiers spécialisés et doivent être reconfirmés avant tout usage commercial :

- **Business** : à partir de 21 $/utilisateur/mois (Source : https://coworker.ai/blog/gemini-enterprise-pricing)
- **Standard** : 30 $/mois (engagement 12 mois) ou 35 $/mois (sans engagement) (Source : https://coworker.ai/blog/gemini-enterprise-pricing)
- **Plus** : environ 50 $/mois (engagement annuel) ou 60 $/mois (sans engagement) (Source : https://coworker.ai/blog/gemini-enterprise-pricing)
- **Frontline** : tarif sur devis, nécessite un minimum de 150 licences Standard ou Plus actives pour être activée (Source : https://coworker.ai/blog/gemini-enterprise-pricing)

Les cinq noms d'édition (**Business, Standard, Plus, Frontline, Pay-as-you-go**) sont en revanche confirmés par la documentation officielle Google Cloud elle-même (Source : https://docs.cloud.google.com/gemini/enterprise/docs/licenses).

### 1.8 Synthèse Partie 1

| Question | Réponse | Niveau de confiance |
|---|---|---|
| Un outil de codage est-il inclus avec Gemini Enterprise ? | Oui — Google Antigravity, sans coût additionnel | Élevé (sources officielles multiples) |
| Éditions concernées | Standard, Plus, Standard Emerging Market, Pay-as-you-go | Élevé |
| Édition Business concernée ? | Probablement non, mais non explicitement démenti | ⚠️ Moyen — à reconfirmer |
| Édition Frontline concernée ? | Statut ambigu dans les sources | ⚠️ Non vérifié |
| Montant/volume exact des crédits ou quotas inclus | 10 $/utilisateur/mois (Standard) et 15 $/utilisateur/mois (Plus), selon la doc quotas | Moyen — à recouper avec l'annonce Antigravity du 21/08 |
| Le crédit "100 $" est-il lié à Gemini Enterprise ? | Non — lié à l'abonnement individuel Google AI Ultra | Élevé (source officielle) |

---

## Partie 2 — Cas d'usage clients réels de Gemini Enterprise

### 2.1 Études de cas publiées directement par Google Cloud (page officielle "Customer Stories")

Page index : https://cloud.google.com/customers (Attention : cette page et les fiches individuelles `cloud.google.com/customers/*` sont fortement dynamiques en JavaScript ; leur contenu textuel complet n'a pas pu être extrait intégralement via récupération automatisée. Les éléments ci-dessous proviennent de résumés générés à partir de l'indexation de ces pages ; les chiffres marqués ⚠️ doivent être revérifiés sur la page live avant citation à un client.)

**Virgin Voyages (croisiéristes, grand public/loisirs) — le cas le mieux corroboré par une source primaire indépendante (communiqué de presse officiel)**
- Déploiement de plus de 50 agents IA spécialisés sur Gemini Enterprise, dont "Email Ellie", un agent de marketing personnalisé développé par l'équipe créative interne (Source : https://www.prnewswire.com/news-releases/virgin-voyages-partners-with-google-cloud-to-launch-a-fleet-of-50-ai-agents-on-gemini-enterprise-powering-a-company-wide-transformation-302579376.html).
- Résultat chiffré confirmé par communiqué officiel : **réduction d'environ 40 % du temps consacré à la création de contenu marketing (copy des campagnes email)** — « The marketing team has reduced time spent on campaign copy creation by an estimated 40%. » (même source).
- **Hausse de 28 % du chiffre d'affaires en glissement annuel sur le mois de juillet**, présentée comme contribuant à un mois de ventes record (même source).
- Fiche client officielle Google Cloud (contenu non intégralement vérifié) : https://cloud.google.com/customers/virginvoyages

**Berenberg (banque privée allemande, fondée en 1590, secteur bancaire/gestion de fortune)**
- Premier établissement bancaire d'Europe à déployer Gemini Enterprise à l'échelle de toute la banque, partenariat avec Google Cloud depuis 2022 (Source : https://cloud.google.com/customers/berenberg ; vidéo témoignage client officielle : https://www.youtube.com/watch?v=kUNyCj4RpFY).
- Utilisation par les analystes en recherche actions, gérants de portefeuille et équipes banque d'investissement pour synthétiser rapports de brokers, dépôts réglementaires et actualités marché.
- ⚠️ **Chiffre non vérifié directement sur la page source** (contenu de la page inaccessible en extraction automatisée complète, information obtenue via résumé d'indexation moteur de recherche, cohérent sur deux requêtes distinctes) : gain de **85 à 90 % de rapidité sur la génération de contenu** grâce aux flux assistés par IA. **À reconfirmer avant citation client.**

**Kohl's (grande distribution/retail)**
- Utilisation de l'architecture agentique unifiée de Gemini Enterprise comme "porte d'entrée" pour interroger en langage naturel les données d'entreprise gouvernées (analytique conversationnelle : comparaisons de performance, identification des catégories les plus performantes, etc.).
- Extension vers le client final avec le "Kohl's Gift Finder" pour la fête des Mères, agent conversationnel d'aide au choix de cadeaux.
- Aucun résultat chiffré (%, temps, coût) n'a pu être identifié dans les sources consultées.
(Source : https://cloud.google.com/customers/kohls)

**Gordon Food Service (distribution alimentaire, l'un des plus grands distributeurs privés d'Amérique du Nord)**
- Déploiement combiné de Gemini Enterprise et Google Workspace dans le cadre d'une stratégie IA globale ; les connecteurs prêts à l'emploi de Gemini Enterprise ont permis d'éviter des développements sur mesure pour intégrer les nombreuses applications internes.
- Développement de systèmes agent-à-agent (avec notamment Tyson Foods, cité comme référence sectorielle comparable) pour fluidifier la chaîne d'approvisionnement.
- Aucun résultat chiffré identifié dans les sources.
(Sources : https://cloud.google.com/customers/gordonfoodservice ; communiqué officiel du 9 octobre 2025 : https://www.googlecloudpresscorner.com/2025-10-09-Gordon-Food-Service-Fuels-Digital-Transformation-and-AI-Powered-Growth-with-Gemini-Enterprise-and-Google-Workspace)

**Huge (agence créative)**
- Automatisation du processus de qualification ("vetting") des demandes entrantes : recherche automatisée sur les concurrents, la position marché et les données financières des prospects, remplaçant un travail de recherche manuel.
- Résultat qualitatif : traitement "en quelques minutes ce qui prenait auparavant des heures voire des jours".
- Extension des services proposés aux clients (production vidéo à grande échelle via Veo 3, le modèle de génération vidéo de Google, combiné à Gemini Enterprise).
- Aucun résultat chiffré (%) identifié.
(Source : https://cloud.google.com/customers/huge)

**B3Networks**
- Réduction du temps de traitement des requêtes de connaissance interne et de brainstorming.
- ⚠️ Chiffre non vérifié directement (résumé d'indexation uniquement) : "20+ minutes gagnées par requête".
(Source : https://cloud.google.com/customers/b3networks)

**Etsy et Unilever** (mentionnés sur la page d'index des cas clients Google Cloud, mais avec des informations limitées et en partie antérieures au lancement de Gemini Enterprise en tant que marque, en octobre 2025)
- Etsy : personnalisation de l'expérience pour 90 millions d'acheteurs en combinant Vertex AI / Gemini Enterprise Agent Platform, BigQuery, Dataflow et les modèles Gemini. Description essentiellement qualitative, périmètre technique plus large que le seul "Gemini Enterprise app". ⚠️ Lien direct avec la marque "Gemini Enterprise" à confirmer.
- Unilever : agents connectés de bout en bout pour accélérer les décisions d'approvisionnement des équipes achats (procurement). Description qualitative uniquement.
(Source : https://cloud.google.com/customers)

### 2.2 Secteur financier — "Gemini Enterprise for Financial Services" (lancement du 25 août 2026)

Google Cloud a lancé une déclinaison sectorielle de Gemini Enterprise dédiée aux marchés de capitaux et à la banque d'entreprise, avec un agent "Financial Research" managé par Google et plus de 50 compétences ("skills") spécialisées (Source : https://cloud.google.com/blog/products/ai-machine-learning/introducing-gemini-enterprise-for-financial-services).

**Deutsche Bank** — partenaire de conception ("design partner") pour l'agent Financial Research, citation officielle et nominative :

> « As a design partner for the Financial Research agent, Deutsche Bank has helped shape this capability in view of the realities of a highly regulated industry – from data protection and governance to the workflows our teams use every day. Starting in the Corporate Bank, we see significant potential to reduce manual research effort, improve the consistency and auditability of outputs, and give our teams more time for client conversations. »
— Marie-Jeanne Deverdun, Chief Technology, Data and Innovation Officer et membre du directoire de Deutsche Bank
(Source : https://cloud.google.com/blog/products/ai-machine-learning/introducing-gemini-enterprise-for-financial-services)

**Autres institutions citées comme utilisatrices** (mentionnées nommément dans la même annonce Google Cloud, mais **sans détail de cas d'usage ni chiffre quantifié disponible dans les sources consultées** — à traiter comme une simple liste de logos clients, pas comme des études de cas à part entière) :
- **CME Group** — cité comme adoptant précoce, sans détail.
- **BNY** — plateforme "Eliza AI".
- **Citi Wealth** — plateforme "Citi Sky".
- **Lloyds Banking Group**.
- **Macquarie Bank** — titre de communiqué séparé mentionnant une mise à l'échelle de l'innovation client via l'IA agentique.
- **Signal Iduna** (assurance) — déploiement de Gemini Enterprise auprès de plus de 10 000 employés.
(Source pour l'ensemble de cette liste : https://cloud.google.com/blog/products/ai-machine-learning/introducing-gemini-enterprise-for-financial-services)

**⚠️ Le seul chiffre de performance mentionné dans ce communiqué n'est pas attribué à un client précis** — il s'agit d'un exemple générique de capacité produit : « It reduces complex bond portfolio risk exposure analysis to a sub-5-minute execution, complete with automated duration-hedging strategy suggestions. » (même source). **Ne pas présenter ce chiffre comme un résultat client vérifié.**

### 2.3 Agents partenaires disponibles dans l'écosystème Gemini Enterprise (Genpact)

Il ne s'agit pas d'un client de Gemini Enterprise à proprement parler, mais d'un partenaire ayant construit des agents disponibles via la marketplace Gemini Enterprise — pertinent pour illustrer l'écosystème :

> Genpact Finance One – Revenue Lens and PnL Agents, suite d'agents construits sur Google ADK et le protocole A2A, permettant aux équipes finance d'obtenir des analyses de revenus et de compte de résultat en langage naturel au sein de Gemini Enterprise, destinés à améliorer la précision des prévisions de revenus et la gestion de trésorerie.
(Source : https://media.genpact.com/2026-05-07-Genpact-and-Google-Cloud-Expand-Alliance-to-Bring-Agentic-Solutions-to-the-Office-of-the-CFO)

Aucun résultat chiffré n'est publié pour ce partenariat.

### 2.4 Cas d'usage documentés par un intégrateur partenaire (Endava) — clients anonymisés

Endava, société de conseil/intégration partenaire de Google Cloud, publie ses propres études de cas de déploiement de Gemini Enterprise chez des clients anonymisés (nom du client non divulgué, secteur précisé) :

**Distribution/Retail (18 000 employés, non nommé)**
- Mise en place d'une solution de recherche conversationnelle agentique intégrée à l'intranet de l'entreprise.
- Résultat qualitatif uniquement : « a significant reduction in time spent on manual searches » — **aucun pourcentage chiffré n'est publié** pour ce cas précis.
(Source : https://www.endava.com/case-studies/transforming-enterprise-search-in-retail-with-ai-and-gemini-enterprise)

**Média/Technologie (non nommé)**
- Recherche en langage naturel across Jira, Confluence, Outlook et dépôts Git pour les équipes ingénierie et QA.
- Résultats chiffrés publiés : **« 60% reduction in documentation search time »** et **« 30% faster onboarding »**, solution validée auprès de plus de 50 utilisateurs (backend, QA, DevOps).
(Source : https://www.endava.com/case-studies/revolutionising-engineering-knowledge-discovery-in-media-with-gemini-enterprise)

*Note méthodologique : ces deux cas sont publiés par Endava (partenaire intégrateur), pas directement par Google Cloud. Les clients sont anonymisés — impossible de vérifier l'identité réelle de l'entreprise. À utiliser en complément, pas comme substitut aux cas Google Cloud nommés ci-dessus.*

### 2.5 Cas d'usage documentés par fonction métier — source officielle Google Cloud

La documentation officielle Gemini Enterprise liste des exemples d'usage par fonction (liste non exhaustive, extraite telle quelle de la page officielle) :

**Finance** : analyser des états financiers et calculer des ratios ; détecter des anomalies dans les données de transaction ; rédiger des synthèses de rapports financiers ; résumer une transcription de résultats trimestriels ("earnings call").

**RH** : créer des supports d'onboarding personnalisés ; analyser les données salariales internes.

**Juridique** : conduire des recherches juridiques ; préparer des dépositions et l'audition de témoins ; rédiger de la correspondance juridique ; rédiger des documents juridiques simples ; résumer des documents juridiques.

**Marketing** : générer de nouvelles idées de contenu ; prolonger et actualiser des assets créatifs existants ; résumer une campagne ; adapter le ton et le message publicitaire à une audience cible.

**R&D** : accélérer la découverte de matériaux ; analyser des concepts et méthodologies de recherche ; revoir des standards de conception.

**Ventes** : créer des segments de clientèle cible ; personnaliser l'e-mail outreach ; préparer un premier rendez-vous client ; obtenir un retour sur un pitch commercial.

**Développement logiciel** : déboguer et diagnostiquer du code ; générer et refactoriser du code ; générer des cas de test ; optimiser la performance.

**Support** : résoudre des tickets/incidents IT ; simplifier l'onboarding et la formation.

(Source pour l'ensemble de cette section : https://docs.cloud.google.com/gemini/enterprise/docs/example-use-cases)

**Important : cette page présente des exemples d'usage génériques proposés par Google, pas des résultats mesurés chez de vrais clients.** Elle ne doit pas être confondue avec les études de cas nommées de la section 2.1.

### 2.6 Synthèse Partie 2 — ce qui est réellement documenté vs. ce qui ne l'est pas

| Client | Source | Chiffre publié et confirmé | Fiabilité |
|---|---|---|---|
| Virgin Voyages | Communiqué de presse officiel (PR Newswire / Google Cloud Press Corner) | -40 % temps de création de contenu marketing ; +28 % CA en glissement annuel (juillet) | ✅ Élevée — source primaire directement citée |
| Deutsche Bank | Blog officiel Google Cloud, citation nominative | Aucun chiffre, mais citation attribuée et vérifiable | ✅ Élevée pour la citation, pas de métrique chiffrée |
| Berenberg | Fiche client Google Cloud + vidéo témoignage | 85-90 % de gain de rapidité (⚠️ non revérifié sur la page source directement) | ⚠️ Moyenne |
| Endava — client média anonymisé | Étude de cas Endava | -60 % temps de recherche documentaire, +30 % rapidité d'onboarding | ✅ Élevée pour la source (mais client anonymisé) |
| Kohl's, Gordon Food Service, Huge, Etsy, Unilever, Genpact | Fiches clients / communiqués Google Cloud | Aucun chiffre quantifié trouvé | Qualitatif uniquement |
| CME Group, BNY, Citi Wealth, Lloyds, Macquarie, Signal Iduna | Cités nommément dans un communiqué Google Cloud | Aucun détail d'usage ni chiffre | Liste de logos uniquement |

---

## Recommandation pour usage client (ATECNA)

1. **Partie 1** : le message "Antigravity est inclus sans coût additionnel dans Gemini Enterprise Standard/Plus" peut être communiqué avec un niveau de confiance élevé. **Ne jamais avancer de montant précis de crédits inclus** sans le recouper avec les 10 $/15 $ par utilisateur/mois documentés côté quotas — orienter le client vers un devis Google Cloud pour confirmation finale.
2. **Partie 2** : le cas **Virgin Voyages** est le plus solide à citer en clientèle (source = communiqué de presse officiel, chiffres directement vérifiables). Les cas **Berenberg** et **B3Networks** nécessitent une revérification directe sur `cloud.google.com/customers` avant citation avec chiffres précis. Les cas Endava sont utilisables mais doivent être présentés comme anonymisés et non attribués à Google Cloud directement.
