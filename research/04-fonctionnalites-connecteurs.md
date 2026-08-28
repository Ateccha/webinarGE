# Gemini Enterprise — Fonctionnalités & Connecteurs

*Document de référence interne — ATECNA. Recherche effectuée le 28/08/2026 à partir de la documentation officielle Google Cloud (docs.cloud.google.com, cloud.google.com, blog.google, deepmind.google) et de sources presse. Chaque affirmation est sourcée ; les points non confirmés directement dans la documentation sont marqués ⚠️ Non vérifié.*

> **Note de contexte importante** : entre le lancement initial de « Gemini Enterprise » (renommage d'Agentspace, 9-10 octobre 2025) et août 2026, Google a fait évoluer le produit en profondeur. Le 22 avril 2026, Google a annoncé la **Gemini Enterprise Agent Platform**, une refonte qui fait évoluer Vertex AI et fusionne l'ancien « Agentspace/Gemini Enterprise » côté utilisateur final avec une plateforme de développement d'agents complète côté développeurs (Source : https://cloud.google.com/blog/products/ai-machine-learning/the-new-gemini-enterprise-one-platform-for-agent-development). Ce document reflète l'état du produit à fin août 2026 et distingue, quand c'est pertinent, l'app « Gemini Enterprise » (utilisateur final) de la « Gemini Enterprise Agent Platform » (développeurs/plateforme).

---

## 1. Vue d'ensemble et historique

- Gemini Enterprise est décrit officiellement comme « an intranet search, AI assistant, and agentic platform » qui permet aux collaborateurs d'utiliser l'IA générative et des workflows agentiques en s'appuyant sur les sources de données de l'organisation (Source : https://docs.cloud.google.com/gemini/enterprise/docs).
- Le produit a été lancé sous ce nom le 9-10 octobre 2025, en remplacement/évolution de Google Agentspace, avec six piliers annoncés : modèles Gemini, un « no-code workbench », des agents Google prêts à l'emploi, une connectivité de données sécurisée (Google Workspace, Microsoft 365, Salesforce, SAP…), un cadre de gouvernance central, et un écosystème ouvert de plus de 100 000 partenaires (Source : https://cloud.google.com/blog/products/ai-machine-learning/introducing-gemini-enterprise).
- Le 22 avril 2026, Google a annoncé la **Gemini Enterprise Agent Platform**, structurée en quatre piliers : **Build** (construire), **Scale** (industrialiser), **Govern** (gouverner), **Optimize** (optimiser), avec un nouvel Agent Development Kit (ADK) orienté graphe, l'Agent Runtime, l'Agent-to-Agent Orchestration, la Memory Bank, l'Agent Identity, l'Agent Gateway, Model Armor, l'Agent Simulation et l'Agent Observability (Source : https://cloud.google.com/blog/products/ai-machine-learning/the-new-gemini-enterprise-one-platform-for-agent-development).
- Le 25 août 2026, Google a lancé une déclinaison verticale, **Gemini Enterprise for Financial Services**, avec un agent de recherche financière géré par Google, plus de 50 « skills » spécialisées et 13 connecteurs de données financières sous licence (Source : https://www.googlecloudpresscorner.com/2026-08-25-Google-Cloud-Launches-Gemini-Enterprise-for-Financial-Services).
- ⚠️ Non vérifié : l'existence et le contenu exact d'un article Wikipédia dédié « Gemini Enterprise Agent Platform » n'ont pas pu être confirmés (la page a renvoyé une erreur 404 lors de la vérification).

---

## 2. Concepts clés de la plateforme

D'après la documentation officielle, Gemini Enterprise repose sur les briques suivantes (Source : https://docs.cloud.google.com/gemini/enterprise/docs/concepts) :

- **Data sources** : connexions vers des sources Google et tierces.
- **Data stores** : chaque source de données crée un ou plusieurs magasins de données dédiés par type d'entité (ex. Jira Cloud crée des data stores distincts pour les issues, pièces jointes, commentaires, worklogs).
- **Apps** : fournissent résultats de recherche, actions et agents aux utilisateurs finaux ; une app peut se connecter à plusieurs data stores (relation many-to-many), permettant une recherche fédérée « blended » multi-sources.
- **Assistant** : l'interface de chat intégrée à l'app, qui génère des réponses aux questions et sous-questions en les ancrant (« grounding ») dans les données d'entreprise avec citations.
- **Actions** : permettent à l'assistant d'exécuter des tâches pour le compte de l'utilisateur (créer un événement de calendrier, éditer un ticket dans un système connecté, etc.).
- **Agents** : applications à but précis qui automatisent des processus multi-étapes et analysent l'information à l'aide des données d'entreprise et de divers outils ; les utilisateurs peuvent choisir des agents prêts à l'emploi ou en créer.
- **Skills** : instructions réutilisables et prompts standardisés qui personnalisent l'exécution des tâches par l'assistant, sans code.
- **Analytics** : tableau de bord donnant de la visibilité sur les tendances d'usage, la qualité de recherche et l'engagement des utilisateurs finaux.
- **Observability** : télémétrie temps réel (traces d'exécution, spans, logs d'audit) pour diagnostiquer la performance et analyser l'activité du système.

---

## 3. Fonctionnalités natives (Gemini Enterprise app)

### 3.1 Recherche d'entreprise (Search / Assistant)
- Recherche multimodale, respectueuse des permissions, sur l'ensemble des informations de l'entreprise, avec assistance conversationnelle IA et réponses à des questions complexes (Source : https://docs.cloud.google.com/gemini/enterprise/docs).
- Recherche image et vidéo devenue disponible en disponibilité générale (GA) le 13 mars 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).
- Contrôle d'accès fin au niveau de l'app (« app-level fine-grained access control ») en GA depuis le 2 février 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).

### 3.2 Gemini Notebook (Enterprise) — anciennement NotebookLM Enterprise
- Renommé de « NotebookLM Enterprise » à « **Gemini Notebook Enterprise** » le 16 juillet 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).
- Assistant de recherche et de rédaction basé sur l'IA qui fonctionne au mieux avec les sources que l'utilisateur importe (Source : recherche web, snippet issu de la documentation Google).
- Génère des « Audio Overviews » (résumés audio façon podcast) désormais disponibles dans plus de 50 langues, extension annoncée en avril 2025 et confirmée pour les éditions Gemini Business/Enterprise/Education (Source : https://blog.google/innovation-and-ai/models-and-research/google-labs/notebooklm-audio-overviews-50-languages/).
- Les options de durée du résumé audio (court/par défaut/long) restent uniquement en anglais même si la génération audio couvre 80+ langues selon certaines sources secondaires — ⚠️ Non vérifié directement sur la doc officielle Google Cloud (chiffre issu d'agrégateurs tiers).
- Diapositives (« slide decks ») et infographies générées par Gemini Notebook sont passées en GA le 2 juin 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).
- Conformité UE (data residency zone / local processing) pour les fonctionnalités cœur de Gemini Notebook Enterprise confirmée au 3 juin 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).
- L'API de podcast pour Gemini Notebook Enterprise a été dépréciée le 20 mai 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).

### 3.3 Deep Research (agent de recherche approfondie)
- Fait partie des agents « Made by Google » listés dans l'Agent Gallery (Source : https://docs.cloud.google.com/gemini/enterprise/docs/agent-gallery).
- Fonctionnement en boucle : **Plan → recherche multi-sources → itération → production du livrable**, en mode asynchrone (plusieurs minutes à plusieurs heures), adapté aux tâches ne nécessitant pas une réponse en temps réel (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/agents/use-deep-research).
- Sources exploitées : serveurs MCP distants, Google Search et « Enterprise Web Search », « Agent Search » (jeux de documents internes), fichiers/dossiers importés en ligne (PDF, tableurs) (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/agents/use-deep-research).
- Production de rapports détaillés et cités, avec visuels prêts à présenter (infographies intégrées, matrices de positionnement marché, graphiques de performance financière générés en HTML) (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/agents/use-deep-research).
- Limites documentées : mode mono-tour uniquement (pas de continuité conversationnelle), durée d'exécution maximale de 120 minutes avant échec, pas de support CMEK ni VPC Service Controls en Preview, mise en cache implicite non désactivable, rétention des données de 7 jours (3 jours pour les résultats issus du grounding Google Search) (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/agents/use-deep-research).
- Des paramètres d'observabilité pour les agents Deep Research sont passés en Public Preview le 23 juin 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).
- Une version enrichie a été présentée le 22 avril 2026 : planification multi-étapes complexe, synthèse autonome du web ouvert et des données internes de l'entreprise, raisonnement itératif avec inférence longue durée (Source : https://cloud.google.com/blog/products/ai-machine-learning/whats-new-in-gemini-enterprise).

### 3.4 Canvas
- Éditeur interactif intégré directement à Gemini Enterprise, permettant de créer/éditer des documents (Docs) ou présentations (Slides) dans un seul volet, avec mise en forme riche et co-édition en temps réel (Source : https://cloud.google.com/blog/products/ai-machine-learning/whats-new-in-gemini-enterprise).
- Interopérabilité avec Microsoft 365 (export vers les formats Office) (Source : https://cloud.google.com/blog/products/ai-machine-learning/whats-new-in-gemini-enterprise).
- La création de documents et de diapositives via Canvas a été lancée le 1er juin 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).

### 3.5 Data Insights Agent
- Agent natif « out-of-the-box » de Google qui fait le pont entre données structurées (entrepôts de données, bases de données) et sources non structurées (documents, e-mails, chat), génère dynamiquement des requêtes SQL et de recherche pour offrir une vue opérationnelle à 360° (Source : https://cloud.google.com/blog/products/ai-machine-learning/whats-new-in-gemini-enterprise).
- Transforme des feuilles de calcul complexes et des données BigQuery en insights exploitables sans connaissance préalable de SQL (Source : recherche web, synthèse documentaire Google).

### 3.6 Data Science Agent
- ⚠️ Nuance importante pour l'évaluation de faisabilité projet : le « Data Science Agent » documenté en détail par Google se trouve dans **Colab Enterprise**, un produit connexe de la Gemini Enterprise Agent Platform, plutôt que strictement dans l'app Gemini Enterprise elle-même (Source : https://docs.cloud.google.com/colab/docs/use-data-science-agent).
- Capacités : traitement de données à grande échelle via BigQuery ML, BigQuery DataFrames ou Managed Service for Apache Spark ; automatisation du nettoyage/transformation/analyse de données volumineuses ; exécution de code Python dans un environnement sandbox sécurisé pour effectuer calculs et analyses complexes (Source : https://docs.cloud.google.com/colab/docs/use-data-science-agent).
- Annoncé initialement en Preview le 10 octobre 2025 lors du lancement de Gemini Enterprise, avec automatisation du « data wrangling », de l'ingestion, de l'exploration de données et de la génération de plans multi-étapes pour l'entraînement et l'inférence de modèles ML (Source : https://cloud.google.com/blog/products/ai-machine-learning/introducing-gemini-enterprise).
- Une démo « Stateful Data Science Agent on Agent Runtime » illustre un agent BigQuery avec Memory Bank conservant les préférences utilisateur entre sessions (Source : https://cloud.google.com/blog/products/ai-machine-learning/13-demos-on-gemini-enterprise-agent-platform).

### 3.7 Idea Generation
- ⚠️ **Fonctionnalité retirée de la plateforme** : le journal des modifications indique explicitement « Idea Generation agent removed from platform » à la date du 14 juillet 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes). La page de documentation dédiée ne renvoie plus de contenu spécifique à cette fonctionnalité au 28/08/2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/idea-generation).
- Description historique (avant retrait) : agent combinant IA avancée et un cadre de « compétition façon tournoi » pour générer et classer des idées, utilisé pour l'innovation et la résolution de problèmes (Source : recherche web, synthèse documentaire Google — description historique, à considérer avec prudence puisque la fonctionnalité n'est plus active).

### 3.8 Core Assistant
- Lancé en GA le 28 mai 2026, avec fonctionnalités de traçage (tracing) et de métriques en Preview (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).
- Listé comme agent « Made by Google » dans l'Agent Gallery aux côtés de Deep Research (Source : https://docs.cloud.google.com/gemini/enterprise/docs/agent-gallery).

### 3.9 Co-Scientist agent
- Mentionné dans la documentation de l'Agent Gallery comme agent créé par Google (Source : https://docs.cloud.google.com/gemini/enterprise/docs/agent-gallery). ⚠️ Non vérifié : le détail fonctionnel précis n'a pas pu être confirmé au-delà de cette mention.

### 3.10 Skills
- Fonctionnalité permettant aux utilisateurs de créer et partager des instructions personnalisées (prompts réutilisables), passée en GA le 13 août 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).
- Une version antérieure était passée en GA+allowlist le 17 juin 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).
- Selon l'annonce du 22 avril 2026 : codifient l'expertise en workflows réutilisables (ex. application de la charte graphique, mise en forme de rapports), chargées dynamiquement par les agents pour l'efficience des coûts et pour éviter d'encombrer le raisonnement du modèle (Source : https://cloud.google.com/blog/products/ai-machine-learning/whats-new-in-gemini-enterprise).

### 3.11 Projects
- Espace de travail collaboratif dynamique pour humains et agents, unifiant le contexte de Google Workspace, Microsoft OneDrive et les discussions d'équipe ; collaboration en temps réel et asynchrone pour le brainstorming, la co-création et la prise de décision informée (Source : https://cloud.google.com/blog/products/ai-machine-learning/whats-new-in-gemini-enterprise).

### 3.12 Inbox (centre de commande des agents)
- Emplacement central pour surveiller et gérer toute l'activité des agents, avec notifications catégorisées (« Needs your input », « Errors », « Completed ») et vue consolidée de la progression des agents en cours (Source : https://cloud.google.com/blog/products/ai-machine-learning/whats-new-in-gemini-enterprise).
- Les annonces de nouveaux membres d'équipe sur la page d'accueil de l'app sont passées en GA le 18 août 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).

### 3.13 Long-running agents et Workflow agents
- Les agents longue durée gèrent des workflows multi-étapes s'étalant sur des heures voire des jours (ex. rapprochement financier de bout en bout, séquençage de prospects commerciaux), opérant de façon autonome dans des sandboxes cloud sécurisées de Google, pour des tâches ponctuelles ou récurrentes (Source : https://cloud.google.com/blog/products/ai-machine-learning/whats-new-in-gemini-enterprise).
- Les « Workflow agents », supportant l'exécution séquentielle de tâches, sont passés en GA+allowlist le 18 juin 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).
- Le « transparent thinking » (affichage du raisonnement en temps réel) est passé en GA le 27 juillet 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).

### 3.14 Interfaces UI dynamiques générées par agent (A2UI)
- Support du protocole **Agent-to-UI (A2UI)** : les agents personnalisés génèrent des composants d'interface natifs riches — visualisations de données interactives, formulaires structurés — intégrés nativement dans l'app Gemini Enterprise (Source : https://cloud.google.com/blog/products/ai-machine-learning/whats-new-in-gemini-enterprise).
- L'enregistrement des agents A2UI et A2A dans le Registre d'agents est passé en GA le 17 août 2026, avec support d'A2UI v0.9 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).
- Le catalogue de composants « A2UI Material » a été mis à jour le 26 août 2026 avec un style Material 3, des contrôles de validation et de nouvelles propriétés pour `MaterialIcon` et `MaterialChips` (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).

### 3.15 Agents High-code / Full-code
- Les équipes d'ingénierie peuvent construire des agents sophistiqués en code complet et les publier directement dans l'app Gemini Enterprise (Source : https://cloud.google.com/blog/products/ai-machine-learning/whats-new-in-gemini-enterprise).
- Les agents ADK déployés sur l'Agent Runtime sont passés en GA le 20 avril 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).

---

## 4. Agent Designer (constructeur d'agents no-code)

- Plateforme no-code/low-code intégrée à Gemini Enterprise pour créer, gérer et lancer des agents mono-étape et multi-étapes (Source : https://docs.cloud.google.com/gemini/enterprise/docs/agent-designer).
- **Deux modes de construction** :
  - **Conversationnel** : interface de chat pour construire et affiner l'agent via des prompts en langage naturel, permettant un prototypage rapide pour les utilisateurs non techniques.
  - **Éditeur visuel de workflow** : un « designer pane » offrant un contrôle low-code granulaire sur la configuration de l'agent, organisé en onglets (dont un onglet « Flow » présentant une représentation visuelle du workflow et de la logique de contrôle).
  (Source : https://docs.cloud.google.com/gemini/enterprise/docs/agent-designer)
- **Types d'agents** : agents mono-étape (tâches indépendantes et bien définies) et agents multi-étapes (agent principal coordonnant un ou plusieurs sous-agents pour accomplir une tâche complexe) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/agent-designer).
- **Connexions** : aux sources de données et outils Google et tiers (Gmail, Google Drive, Jira cités en exemple) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/agent-designer).
- **Planification** : exécution récurrente des agents sur un calendrier (Source : https://docs.cloud.google.com/gemini/enterprise/docs/agent-designer).
- **Aperçu en direct** pour tester avant déploiement (Source : https://docs.cloud.google.com/gemini/enterprise/docs/agent-designer).
- Selon l'annonce du 22 avril 2026, Agent Designer permet de « balance generative intelligence with deterministic nodes », d'inspecter/tester/approuver les étapes du workflow avant exécution, et d'intégrer des points de contrôle humain-dans-la-boucle (human-in-the-loop) pour approbations et guidance (Source : https://cloud.google.com/blog/products/ai-machine-learning/whats-new-in-gemini-enterprise).
- **Évolution du modèle par défaut** : les agents Agent Designer utilisaient Gemini 2.5 et ont migré automatiquement vers **Gemini 3.1 Pro** à partir du 17 mai 2026 (US et région Global) ; la migration automatique de tous les agents existants de Gemini 2.5 vers Gemini 3.1 Pro a eu lieu le 1er juin 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).
- Le partage d'agents Agent Designer est passé en GA le 23 février 2026, avec des contrôles étendus et le support des Google Groups (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes) ; le partage d'agents avec des Google Groups en général est passé en GA le 9 juin 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).
- Un bug de configuration de modèle dans Agent Designer a été corrigé le 4 mars 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).

---

## 5. Marketplace / Agent Gallery (agents tiers)

### 5.1 Structure de l'Agent Gallery
L'Agent Gallery organise les agents en quatre sections (Source : https://docs.cloud.google.com/gemini/enterprise/docs/agent-gallery) :
1. **Made by Google** — agents prêts à l'emploi créés par Google (ex. Deep Research, Core Assistant, Co-Scientist).
2. **From your organization** — agents créés ou partagés au sein de l'organisation.
3. **Your agents** — agents personnalisés construits via Agent Designer.
4. **Marketplace** — agents de fournisseurs tiers nécessitant une demande d'accès.

### 5.2 Activation
- Pour utiliser un agent du Marketplace, l'utilisateur doit cliquer sur **Request access** ; la demande est envoyée à l'administrateur pour validation. Une fois approuvé, l'agent apparaît dans la section de l'organisation et peut être invoqué via la syntaxe `@nom_agent` (Source : https://docs.cloud.google.com/gemini/enterprise/docs/agent-gallery).
- Les agents « Made by Google » ne sont pas disponibles dans l'édition Frontline ; l'accès complet aux agents organisationnels nécessite les éditions Standard ou Plus (Source : https://docs.cloud.google.com/gemini/enterprise/docs/agent-gallery). Voir également le tableau des éditions en section 7.
- La demande d'accès aux agents du Marketplace est passée en Preview le 20 avril 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).
- ⚠️ Non vérifié : aucune information précise sur la tarification ou les frais de licence par agent Marketplace n'a été trouvée dans la documentation officielle ; les coûts semblent dépendre de chaque fournisseur individuellement (abonnement propre au vendeur dans certains cas, voir exemple Alteryx ci-dessous).

### 5.3 Écosystème de partenaires (liste représentative, non exhaustive)
Le blog officiel « Partner-built agents available in Gemini Enterprise » recense **plus de 80 agents partenaires** ; en voici une sélection représentative des acteurs cités explicitement dans la demande d'ATECNA, plus quelques exemples notables (Source : https://cloud.google.com/blog/products/ai-machine-learning/partner-built-agents-available-in-gemini-enterprise) :

| Partenaire | Agent | Fonction |
|---|---|---|
| **Adobe** | Adobe Marketing Agent | Requêtes en langage naturel sur les capacités CX Adobe (performance de campagnes, insights d'audience) |
| **Salesforce** | Agentforce Sales | Engagement des leads, briefs de réunion, détection des risques deal, gestion de pipeline en temps réel |
| **ServiceNow** | Now Assist for IT Operations Management | Opère sur ServiceNow AI Platform ; optimise la gestion des alertes et incidents |
| **Sana (Workday)** | Sana Self-Service Agent | Trouve et résume instantanément l'information issue de Workday ; 300+ skills RH et finance |
| **Atlassian** | Rovo | Coéquipier IA intégré à Jira, Confluence et à la suite d'outils ; remonte la connaissance et automatise les tâches |
| **Oracle** | Oracle AI Database Agent | Interroger les données Oracle directement depuis Gemini Enterprise |
| **Accenture** | Supply Chain Inventory Intelligent Advisor | Optimisation de la planification et du suivi des stocks via données temps réel |
| **Deloitte** | Tariff Management Agentic Suite | Automatisation des workflows réglementaires douaniers |
| **Alteryx** | Alteryx AI Insights Agent | Insights analytiques curés dans Gemini Enterprise (nécessite un abonnement Alteryx One) |
| **Dun & Bradstreet** | Business Verification Agent | Vérification d'entreprise fiable, résolution vers un numéro D-U-N-S® |
| **Neo4j** | Neo4j Agent | Traduit le langage naturel en requêtes Cypher pour bases de données en graphe |
| **Replit** | Replit Agent | Permet aux utilisateurs métier de créer des applications d'entreprise en langage naturel |
| **Lovable** | Lovable | Création d'applications et sites web réels par conversation avec l'IA |
| **Palo Alto Networks** | Prisma AIRS Model Security | Scan de plus de 35 formats de modèles pour détecter code malveillant, poids empoisonnés, portes dérobées |
| **Teradata** | Data Analyst AI Agent | Analytique en langage naturel sur les données d'entreprise dans Google Cloud |
| **Red Hat** | Red Hat Lightspeed Agent | Assiste les SRE/admins dans la gestion de l'infrastructure RHEL sur Google Cloud |
| **UKG** | Agentic People Assist — HR Service Delivery | Transforme l'intention en action à travers les workflows RH |
| **WRITER** | WRITER Agent | IA autonome pour les entreprises du Fortune 500, planifie et exécute selon le contexte de l'entreprise |
| **S&P Global** | S&P Global Data Retrieval Agent | Accès cité aux jeux de données S&P Global pour les professionnels de la finance |
| **Monday.com** | monday.com agent | Transforme la planification en exécution (création de tableaux, résumés, automatisations) |

*(Liste complète de plus de 80 agents partenaires disponible à la source citée ; parmi les autres partenaires notables identifiés dans les recherches complémentaires : Acalvio, Amdocs, AODocs, Ascendo, Avalara, Carto, Dynatrace, Enigma, Eon, EPAM, Exa AI, Genpact, Genspark, HCLTech, Iron Mountain, Lilt, LumApps, Manhattan Associates, Menlo Security, OpenText, Pendo, Persistent Systems, Pluto7, Quantum Metric, Saviynt, Skyflow, Supermetrics, Tech Mahindra, Typeface, XM Cyber.)*

- L'annonce du 22 avril 2026 confirme également des partenariats de lancement avec **Oracle, Salesforce, ServiceNow, Adobe, Workday, Accenture** (Source : https://cloud.google.com/blog/products/ai-machine-learning/the-new-gemini-enterprise-one-platform-for-agent-development et https://cloud.google.com/blog/products/ai-machine-learning/whats-new-in-gemini-enterprise).
- Atlassian, via son agent Rovo, a été nommé « 2026 Google Cloud Partner of the Year » dans la catégorie Application Development – Developer Experience (Source : recherche web, résumé d'un article Atlassian Community, ⚠️ non vérifié par accès direct à la source officielle Google Cloud Partner Awards).
- **Déclinaison sectorielle Financial Services (25 août 2026)** : agents partenaires additionnels — D&B Business Verification Agent (KYC), FlowX Agents (traitement de prêts, extraction documentaire), Obin Financial Agent (analyse marchés privés), S&P Global Data Retrieval Agent, S&P Global Energy Horizons Agents (Source : https://www.googlecloudpresscorner.com/2026-08-25-Google-Cloud-Launches-Gemini-Enterprise-for-Financial-Services).

---

## 6. Connecteurs natifs — liste complète

Gemini Enterprise utilise deux mécanismes de connexion aux données (Source : https://docs.cloud.google.com/gemini/enterprise/docs/connectors/introduction-to-connectors-and-data-stores) :
- **Fédération (federation)** : récupère l'information directement à la source sans la copier, ce qui peut réduire la qualité de recherche.
- **Ingestion / indexation** : copie les données dans l'index Gemini Enterprise, ce qui améliore la recherche mais consomme davantage de stockage et de temps.
- Un connecteur **MCP personnalisé (Custom MCP Server)** permet également de connecter des sources de données propriétaires via le Model Context Protocol ; les connecteurs MCP personnalisés non authentifiés sont passés en Public Preview le 22 juillet 2026, et les connecteurs MCP personnalisés (data stores) en GA le 7 août 2026, avec suppression du champ « description » lors de la configuration le 6 août 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).

Le tableau ci-dessous compile la liste des connecteurs identifiés à travers la page officielle « Introduction to connectors and data stores », les journaux de version (release notes) de janvier à août 2026, et les résultats de recherche croisés. **Cette liste n'est probablement pas totalement exhaustive** (Google ajoute de nouveaux connecteurs en continu — plusieurs dizaines par mois selon les release notes), mais elle représente l'inventaire le plus complet compilable à la date de cette recherche.

*(Sources groupées pour l'ensemble du tableau : https://docs.cloud.google.com/gemini/enterprise/docs/connectors/introduction-to-connectors-and-data-stores ; https://docs.cloud.google.com/gemini/enterprise/docs/release-notes ; recherche web croisée.)*

### Google Workspace / Google Cloud
| Connecteur | Statut connu |
|---|---|
| Google Drive | Disponible (chat sur fichiers Drive : GA le 26/03/2026 ; inclusion de documents cross-domaine : Preview le 30/03/2026) |
| Gmail | Disponible |
| Google Calendar | Disponible |
| Google Chat | Filtrage en Public Preview (13/04/2026), data store en Public Preview (11/03/2026) |
| Google Sites | Filtrage en Public Preview (26/05/2026), data store en Public Preview (07/05/2026) |
| Google Groups | Disponible |
| Google Stitch | Data store en Public Preview (15/06/2026) |
| Compute Engine | Data store en Public Preview (29/07/2026) |
| BigQuery | Disponible |
| Cloud Storage | Disponible |
| Cloud SQL | Disponible |
| Spanner | Disponible |
| Firestore | Disponible |
| Bigtable | Disponible |
| AlloyDB for PostgreSQL | Disponible |
| Gemini Notebook Enterprise (ex-NotebookLM Enterprise) | Disponible |

### Microsoft
| Connecteur | Statut connu |
|---|---|
| Microsoft Entra ID | Disponible |
| Microsoft OneDrive | Filtrage en Public Preview (24/03/2026), filtrage d'actions en Public Preview (29/06/2026) |
| Microsoft Outlook | Chat sur pièces jointes en GA (04/03/2026) |
| Microsoft SharePoint Online | Filtrage en Public Preview (13/03/2026), filtres passés GA (30/06/2026), chat fichiers GA (19/02/2026) |
| Microsoft SharePoint Data Center (on-prem) | Disponible |
| Microsoft Teams | Data store fédéré en GA (28/07/2026) |
| Microsoft Learn | Data store en Public Preview (14/04/2026) |
| Dynamics 365 | Data store en Public Preview (15/06/2026) |

### Gestion de projet / travail collaboratif
| Connecteur | Statut connu |
|---|---|
| Jira Cloud | Disponible |
| Jira Data Center (on-prem) | Federation GA (03/04/2026), filtrage d'actions en Preview (15/07/2026) |
| Confluence Cloud | Disponible |
| Confluence Data Center (on-prem) | Federation GA (26/06/2026) |
| Asana | Data store en Public Preview (05/06/2026) |
| Monday.com | Data store en Public Preview (26/02/2026) |
| Linear | Data store en Public Preview (06/02/2026) |
| Smartsheet | Data store en Public Preview (15/05/2026) |
| Wrike | Data store en Public Preview (15/05/2026) |
| Notion | Data store en Public Preview (09/02/2026) |
| Fibery | Data store en Public Preview (11/08/2026) |
| Attio | Data store en Public Preview (03/08/2026) |
| Miro | Data store en Public Preview (11/08/2026) |
| Excalidraw | Data store en Public Preview (14/04/2026) |
| Mermaid Chart | Data store en Public Preview (06/05/2026) |

### CRM / Ventes / Marketing
| Connecteur | Statut connu |
|---|---|
| Salesforce | Federation lancée (31/03/2026) |
| HubSpot | Data store GA (29/06/2026) |
| Zoho CRM | Data store en Public Preview (15/06/2026) |
| Pendo | Data store en Public Preview (21/08/2026) |
| Crossbeam | Data store en Public Preview (19/05/2026) |
| Marketo Cloud | Disponible *(cité dans recherche croisée)* |
| ZoomInfo | Data store en Public Preview (15/07/2026) |
| PandaDoc | Data store en Public Preview (15/05/2026) |
| Gamma | Data store en Public Preview (03/08/2026) |
| Supermetrics | Data store en Public Preview (21/08/2026) |
| SurveyMonkey | Data store en Public Preview (03/08/2026) |
| Calendly | Data store en Public Preview (15/06/2026) |
| MailerLite | Data store en Public Preview (15/06/2026) |

### ITSM / Support client
| Connecteur | Statut connu |
|---|---|
| ServiceNow | Actions + federation GA (16/06/2026) |
| Zendesk | Data store en Preview (28/01/2026) |
| Freshservice | Data store en Public Preview (15/06/2026), actions ajoutées (21/08/2026) |
| PagerDuty | Data store en Preview (26/05/2026) |
| Intercom | Data store en Public Preview (15/06/2026) |
| Guru | Data store en Public Preview (11/08/2026) |

### Développement logiciel
| Connecteur | Statut connu |
|---|---|
| GitHub | Data store en Public Preview (04/03/2026), federation GA (12/08/2026) |
| GitLab | Data store en Public Preview (12/05/2026) |
| Sourcegraph | Data store en Public Preview (29/07/2026) |
| Hugging Face | Data store en Public Preview (14/04/2026) |
| Sanity | Data store en Public Preview (03/08/2026) |

### Communication / Collaboration
| Connecteur | Statut connu |
|---|---|
| Slack | Data store GA (27/05/2026), app d'intégration Slack GA (17/06/2026) |
| Webex Meetings | Data store en Public Preview (11/08/2026) |
| Cisco Workspaces | Data store en Public Preview (11/08/2026) |
| Fullstory | Data store en Public Preview (21/08/2026) |

### Stockage de fichiers
| Connecteur | Statut connu |
|---|---|
| Dropbox | Federation GA (07/04/2026), action de téléchargement ajoutée (28/01/2026) |
| Box | Federation GA (08/05/2026), chat sur pièces jointes GA (04/03/2026) |
| Egnyte | Data store en Public Preview (29/07/2026) |
| AODocs | Disponible *(cité dans recherche croisée)* |
| Coda | Disponible *(cité dans recherche croisée)* |

### Finance, données de marché et conformité
| Connecteur | Statut connu |
|---|---|
| Stripe | Data store en Public Preview (21/08/2026) |
| Oracle NetSuite | Data store en Public Preview (03/08/2026) |
| Ramp | Data store en Public Preview (21/08/2026) |
| Mercury | Data store en Public Preview (11/08/2026) |
| FactSet | Data store en Public Preview (21/08/2026) ; FactSet AI-Ready Data également listé |
| Fiscal.ai | Data store en Public Preview (03/08/2026) |
| Moody's | Data store en Public Preview (03/08/2026) |
| S&P Global | Data store en Public Preview (03/08/2026) |
| D&B Commercial Graph | Data store en Public Preview (24/08/2026) |
| Vanta | Data store en Public Preview (11/08/2026) |
| Docusign | Data store en Public Preview (23/03/2026) |
| iManage Platform | Data store en Public Preview (03/08/2026) |
| NetDocuments | Data store en Public Preview (03/08/2026) |
| Cohesity | Data store en Public Preview (11/08/2026) |
| Atlan | Data store en Public Preview (21/08/2026) |
| SAP HANA | Disponible *(cité dans recherche croisée ; à confirmer pour SAP S/4HANA et autres modules SAP)* |
| Workday | Disponible *(cité comme connecteur au lancement d'octobre 2025)* |
| Zoho Books / Zoho Desk / Zoho Projects | Data stores en Public Preview (15/05/2026) |
| Adobe Experience Manager | Disponible *(cité dans recherche croisée)* |
| Okta | Disponible *(cité dans recherche croisée, IdP)* |
| WordPress | Disponible *(cité dans recherche croisée)* |
| Supabase | Data store en Public Preview (21/08/2026), actions ajoutées |

### Divers / long tail (ajoutés en Public Preview en 2026, périmètre plus spécialisé ou vertical)
Aiwyn Tax, AllTrails, Apollo GraphOS, Autodesk Product Help, AWS Marketplace, Bitly, Blockscout, Clinical Trials *(repassé en Private Preview le 05/08/2026)*, CoinDesk Data & Indices, Courtroom5, Crypto, Descript, Dice, Fiscal.ai, Globalping, Gong, Hex, Invideo, Kiwi, LastMinute, LegalZoom, Lovable, LumApps, Midpage, Nexla, Open Targets, pg-aiguide, Pylon, S&P Global Energy Horizons, ServiceM8, Shopify, Solve Intelligence, Taskrabbit, Tavily, Trivago, Twilio Docs, Viator, Wix, GoDaddy, Granted, AirOps, GitHub *(voir dev tools)*, Guidepoint, LSEG, MSCI, PitchBook, SEC Edgar, Daloopa *(ces 5 derniers spécifiques à la déclinaison Financial Services du 25/08/2026)*.

(Source pour l'ensemble de cette section « Divers / long tail » : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes et https://www.googlecloudpresscorner.com/2026-08-25-Google-Cloud-Launches-Gemini-Enterprise-for-Financial-Services)

---

## 7. Éditions et disponibilité des fonctionnalités

D'après la page de comparaison des éditions (Source : https://docs.cloud.google.com/gemini/enterprise/docs/editions), Gemini Enterprise propose cinq éditions : **Business** (1-500 utilisateurs), **Standard**, **Plus**, **Pay-as-you-go**, et **Frontline** (150+ utilisateurs).

| Fonctionnalité | Business | Standard | Plus | Pay-as-you-go | Frontline |
|---|---|---|---|---|---|
| Stockage / indexation par utilisateur | 25 GiB (pool) | 30 GiB (pool) | 75 GiB (pool) | À la consommation | 2 GiB (pool) |
| Connecteurs sélectionnés | ✓ | ✓ | ✓ | ✓ | ✓ |
| Écosystème complet de connecteurs | ✓ | ✓ | ✓ | ✓ | — |
| Recherche d'entreprise sensible aux permissions | ✓ | ✓ | ✓ | ✓ | ✓ |
| Ancrage (grounding) sur données d'entreprise | ✓ | ✓ | ✓ | ✓ | ✓ |
| Accès prioritaire aux modèles | ✓ | ✓ | ✓ | — | — |
| Génération de médias (images/vidéos) | ✓ | ✓ | ✓ | ✓ | ✓ |
| Ancrage web (web grounding) | ✓ | ✓ | ✓ | ✓ | ✓ |
| Création et publication de Notebook | ✓ | ✓ | — | — | — |
| Accès au chat Notebook | ✓ | ✓ | ✓ | ✓ | ✓ |
| Gemini Code Assist Standard | ✓ | ✓ | — | — | — |
| Agents no-code personnalisés (création) | ✓ | ✓ | ✓ | ✓ | — |
| Agents no-code personnalisés (utilisation) | ✓ | ✓ | ✓ | ✓ | ✓ |
| Deep Research | ✓ | ✓ | ✓ | ✓ | ✓ |
| Data Insights | ✓ | ✓ | ✓ | — | — |
| Agents full-code personnalisés | ✓ | ✓ | ✓ | ✓ | — |
| Agent Marketplace | ✓ | ✓ | ✓ | ✓ | — |

- Les utilisateurs Frontline ne peuvent accéder qu'aux agents déjà provisionnés par leur administrateur (Source : https://docs.cloud.google.com/gemini/enterprise/docs/editions).
- L'édition **Pay-as-you-go** (tarification à la consommation, sans quota mutualisé) est passée en GA le 1er août 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).
- Les outils de développement IA sont disponibles pour l'édition « Standard Emerging Market » depuis le 21 août 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).
- Limites de sièges d'abonnement mises en application au 21 août 2026 : 25 sièges max en self-serve, 1 000 sièges max pour les comptes facturés (« invoiced ») (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).
- ⚠️ Non vérifié : les montants tarifaires précis (prix par siège, coût à la consommation) n'ont pas été trouvés dans les pages consultées et nécessiteraient une vérification directe sur la page de pricing officielle ou auprès d'un représentant Google Cloud.

---

## 8. Modèles et capacités multimodales

### 8.1 Ligne de modèles Gemini (constatée dans les release notes, à titre indicatif de rythme de sortie)
D'après le journal des versions, la ligne de modèles Gemini disponible dans Gemini Enterprise a évolué très rapidement entre février et août 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes) :
- **Gemini 3 Pro (Preview)** → remplacé par **Gemini 3.1 Pro (Preview)** le 19 février 2026.
- **Gemini 3 Pro** et **Gemini 3.1 Flash Image** passés en GA le 2 juin 2026.
- **Gemini 3.1 Pro** et **3 Flash** confirmés en Limited Availability avec SLO de GA le 30 avril 2026 ; disponibilité région UE mise à jour en « coming soon » le 13 mai 2026.
- Agent Designer passe par défaut sur **Gemini 3.1 Pro** en régions US/Global le 17 mai 2026.
- **Gemini 3.5 Flash** : GA globale/US/UE le 19 mai 2026 ; activation par défaut confirmée le 5 juin 2026 ; dépréciation annoncée (toggle) le 8 juin 2026 ; retrait initialement prévu le 4 août 2026 puis **reporté** (annoncé le 6 août 2026).
- **Gemini 3.6 Flash** : sorti en région Global le 21 juillet 2026 ; disponible en région US avec allowlist le 24 juillet 2026 ; disponible en US/UE multi-régions sans allowlist le 18 août 2026.
- **Gemini 3.7 Flash** : GA en régions globale/US/UE le 13 août 2026 ; disponible dans l'app mobile (GA) le 14 août 2026.

⚠️ **Point de vigilance pour usage projet client** : compte tenu du rythme très rapide de sortie/retrait de versions Flash (3.5 → 3.6 → 3.7 en quelques semaines) observé dans les release notes, il est recommandé de revérifier la version de modèle active au moment du cadrage de chaque projet client plutôt que de se fier à ce document dans la durée.

### 8.2 Fenêtre de contexte et modalités (Gemini 3 / 3.1 Pro)
- Fenêtre de contexte en entrée : jusqu'à **1 million de tokens** ; sortie plafonnée à **64 000 tokens** (Source : https://deepmind.google/models/model-cards/gemini-3-1-pro/).
- Modalités d'entrée acceptées : **texte, audio, images, vidéo, et dépôts de code entiers** (Source : https://deepmind.google/models/model-cards/gemini-3-1-pro/).
- Modalité de sortie : texte uniquement (le modèle de langage lui-même ; la génération d'image/vidéo/audio passe par des modèles dédiés — voir 8.4) (Source : https://deepmind.google/models/model-cards/gemini-3-1-pro/).
- Mode **« Deep Think »** disponible pour un raisonnement renforcé sur les évaluations de sécurité frontière (Source : https://deepmind.google/models/model-cards/gemini-3-1-pro/).
- Canaux de distribution : Gemini App, Google Cloud/Vertex AI, Google AI Studio, Gemini API, Google Antigravity, **Gemini Enterprise**, et NotebookLM (Source : https://deepmind.google/models/model-cards/gemini-3-1-pro/).
- ⚠️ Non vérifié : le nombre exact de langues supportées nativement par le modèle de langage Gemini 3.1 Pro lui-même n'est pas explicitement chiffré dans la fiche modèle consultée (seule une évaluation multilingue via le benchmark « MMMLU Multilingual Q&A » est mentionnée).

### 8.3 Support linguistique de l'app / des agents conversationnels
- Les agents conversationnels de Gemini Enterprise supporteraient plus de 40 langues, et le module de synthèse vocale associé plus de 220 voix et plus de 40 langues — ⚠️ Non vérifié directement dans la documentation officielle Google Cloud pour Gemini Enterprise (chiffres issus d'agrégation de résultats de recherche, à confirmer ; ce chiffre de « 220+ voix » pourrait en réalité concerner les voix Cloud Text-to-Speech / Chirp3 générales plutôt que spécifiquement Gemini TTS — voir section 8.5 pour les chiffres officiels documentés de Gemini TTS).
- Au lancement d'octobre 2025, les agents conversationnels nouvelle génération (« next-gen conversational agents ») avec constructeur visuel low-code supportaient **plus de 40 langues** (Source : https://cloud.google.com/blog/products/ai-machine-learning/introducing-gemini-enterprise).
- L'UI de Google Workspace with Gemini (produit proche, non strictement identique à Gemini Enterprise) a été élargie à des langues telles que l'espagnol, l'ukrainien, le portugais, l'hindi, le bengali, le gujarati, le kannada, le malayalam, le marathi, le tamoul, le télougou, l'ourdou, l'arabe, le néerlandais, le français, le coréen — ⚠️ Non vérifié comme s'appliquant identiquement à Gemini Enterprise (source secondaire, produit Workspace connexe).

### 8.4 Autres modèles Google accessibles via Model Garden
Model Garden fournit un accès de premier niveau à plus de 200 modèles, incluant des modèles Google, des modèles tiers et des modèles open source (Source : https://cloud.google.com/model-garden, confirmé par recherche croisée).
- **Gemma** : modèle ouvert. La dernière génération (Gemma 4 selon les sources consultées) supporte le texte et l'image en entrée pour toutes les variantes, plus l'audio pour les variantes E2B/E4B ; Gemma 3 supporte texte + image avec plus de **140 langues** et une fenêtre de contexte de **128K tokens** ; variantes spécialisées PaliGemma (vision-langage) et CodeGemma (code) également disponibles (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/models/open-models/use-gemma).
- **Veo** (génération vidéo) : Veo 2 (texte/image → vidéo), Veo 3 et Veo 3 Fast, Veo 3.1 (Source : recherche web, synthèse documentaire Google). Veo 3.1 a remplacé Veo 3.0 en GA le 3 mars 2026 pour la génération vidéo dans Gemini Enterprise (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).
- **Lyria** : génération de musique/pistes audio complètes à partir de prompts texte et image (Source : recherche web, synthèse documentaire Google).
- **Modèles tiers accessibles via Model Garden** : Anthropic Claude (Opus, Sonnet, Haiku selon une source), Grok, Mistral AI, ainsi que des modèles open-weights comme DeepSeek, Llama, Qwen — ⚠️ Non vérifié de façon exhaustive et à confirmer pour chaque modèle individuellement, car la disponibilité précise par modèle/région évolue rapidement (Source : recherche web, synthèse documentaire Google Cloud Model Garden).

### 8.5 Synthèse vocale (Gemini TTS)
Chiffres officiels documentés pour **Gemini TTS** (Source : https://docs.cloud.google.com/text-to-speech/docs/gemini-tts) :
- **28 voix distinctes** (masculines et féminines, ex. Kore, Charon, Callirrhoe, Puck).
- **68 langues au total** : 23 langues en disponibilité générale (dont anglais US, français, allemand, espagnol, japonais, coréen) et 45 langues en Preview.
- Synthèse **multi-locuteurs** (dialogue) à partir de texte libre ou de tours structurés, avec contrôle du style, de l'accent, du rythme, du ton et de l'expression émotionnelle ; latence faible permettant des échanges fluides.
- Fonctionne avec les modèles **Gemini 3.1 Flash TTS** et **Gemini 2.5 Pro TTS**.

⚠️ **Chiffres divergents identifiés** : d'autres sources (secondaires, non issues de la documentation officielle Google Cloud Text-to-Speech) mentionnent pour Gemini 3.1 Flash TTS spécifiquement « 70+ langues », « 30 voix », ou encore « 90+ langues » avec détection automatique de la langue, ainsi que plus de 200 « audio tags » (balises de contrôle de la prosodie/émotion). Ces chiffres ne concordent pas parfaitement avec les 28 voix / 68 langues de la documentation officielle Cloud TTS — probablement du fait de versions de modèle ou de canaux de distribution différents (AI Studio vs Vertex AI vs Cloud Text-to-Speech). **À vérifier au cas par cas selon le canal d'intégration retenu pour un projet client.**
- Le contenu audio généré est marqué avec **SynthID** pour prévenir la désinformation (Source : recherche web, synthèse documentaire Google).

### 8.6 Grounding et multimodalité côté recherche/agents
- Recherche image et vidéo en GA depuis le 13 mars 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).
- Deep Research accepte des entrées multimodales (images et documents PDF/tableurs en pièce jointe) (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/agents/use-deep-research).

---

## 9. Orchestration multi-agents

- **Agent-to-Agent (A2A) Orchestration** : cadre central de la plateforme, conçu pour faire évoluer la « main-d'œuvre agentique » de l'organisation en permettant aux agents d'interagir et de collaborer, de se déléguer/transmettre des tâches entre eux. La plateforme supporte à la fois des schémas d'orchestration génératifs complexes et des schémas déterministes garantissant des résultats prévisibles (Source : recherche web, synthèse documentaire Google Cloud sur A2A Orchestration).
- **Agent Gateway** : composant réseau régional managé qui agit comme « tour de contrôle » du trafic et point d'application des politiques d'exécution pour les agents A2A, les serveurs MCP et les endpoints. Il sécurise et gouverne la connectivité entre clients et agents A2A, entre agents A2A et outils backend, et entre agents A2A et d'autres agents. Les développeurs peuvent utiliser au choix les protocoles MCP, A2A, REST ou gRPC, tout en respectant les standards de sécurité d'entreprise (Source : recherche web, synthèse documentaire Google Cloud sur Agent Gateway).
- **Agent Runtime** : suite intégrée d'outils et services qui déploie les agents sur un runtime entièrement managé, avec gestion de session intégrée et une **Memory Bank** (mémoire long terme). Les runtimes managés (Agent Runtime et Gemini Enterprise) routent automatiquement le trafic agent via l'Agent Gateway (Source : recherche web, synthèse documentaire Google Cloud sur Agent Runtime).
- **Agent Development Kit (ADK)** : framework permettant aux développeurs de construire des orchestrations multi-agents complexes, avec un contrôle granulaire sur la logique, les outils et la simulation d'environnement ; la version présentée en avril 2026 introduit une approche « graph-based » permettant d'organiser des agents en réseaux de sous-agents (Source : https://cloud.google.com/blog/products/ai-machine-learning/the-new-gemini-enterprise-one-platform-for-agent-development).
- **Interopérabilité inter-frameworks démontrée** : un exemple documenté montre un « ADK control room » qui délègue la planification à une machine à états LangGraph, laquelle distribue ensuite des tâches à une équipe d'exécution CrewAI, le tout connecté via le protocole A2A, avec re-planification automatique en cas d'échec d'une étape — démontrant l'orchestration multi-frameworks (ADK, LangGraph, CrewAI, A2A) en production (Source : https://cloud.google.com/blog/products/ai-machine-learning/13-demos-on-gemini-enterprise-agent-platform).
- **Pipeline multi-agents cross-langage** : exemple d'un pipeline de conformité contractuelle où un agent Python (extraction des termes via Gemini) et un agent Go (validation contre la politique de l'entreprise) sont connectés via le protocole A2A et orchestrés par l'ADK ; `RemoteA2aAgent` permet de transformer des services conformes A2A en sous-agents locaux (Source : https://cloud.google.com/blog/products/ai-machine-learning/13-demos-on-gemini-enterprise-agent-platform).
- **Model Context Protocol (MCP)** : protocole ouvert permettant de créer des outils MCP réutilisables (interrogation BigQuery, recherche de fichiers, appels API) offrant une compatibilité inter-fournisseurs (Source : https://cloud.google.com/blog/products/ai-machine-learning/13-demos-on-gemini-enterprise-agent-platform).
- **Agent Registry** : catalogue central permettant aux équipes IT de curer et distribuer les agents approuvés à l'échelle de l'organisation ; l'intégration de gouvernance de l'Agent Registry est passée en GA le 25 juin 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes ; https://cloud.google.com/blog/products/ai-machine-learning/whats-new-in-gemini-enterprise).
- **Agents longue durée (pause/reprise)** : trois patrons architecturaux documentés — machines à états durables, gestion événementielle des temps d'inactivité, et « checkpoint-and-resume » avec sessions persistantes, illustrés par un exemple d'agent d'onboarding survivant à des redémarrages de conteneur (Source : https://cloud.google.com/blog/products/ai-machine-learning/13-demos-on-gemini-enterprise-agent-platform).

---

## 10. Gouvernance et sécurité (éléments pertinents pour la faisabilité projet)

- **Agent Identity** : identifiants numériques cryptographiques uniques pour chaque agent, appliquant le principe du moindre privilège, fonctionnant à travers toutes les plateformes ; la capacité de visualisation de l'identité des agents est passée en Preview le 21 avril 2026 (Source : https://cloud.google.com/blog/products/ai-machine-learning/whats-new-in-gemini-enterprise ; https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).
- **Agent Gateway** : point de gestion centralisé des politiques réseau, des contrôles d'accès aux données et des garde-fous de sécurité ; protège contre l'injection de prompt ; capacités de « Context Aware Access » ; empêche l'envoi de données vers des endpoints non approuvés ; transforme le « Shadow AI » en « Managed AI » (Source : https://cloud.google.com/blog/products/ai-machine-learning/whats-new-in-gemini-enterprise).
- **Model Armor** : protection contre l'injection de prompt, l'empoisonnement d'outils (tool poisoning) et la fuite de données sensibles (Source : https://cloud.google.com/blog/products/ai-machine-learning/the-new-gemini-enterprise-one-platform-for-agent-development).
- **Agent Simulation** : outil de test de charge/résilience des agents face à des scénarios réels (Source : https://cloud.google.com/blog/products/ai-machine-learning/the-new-gemini-enterprise-one-platform-for-agent-development).
- **Agent Observability** : supervision temps réel de la sécurité et de la performance, passée en GA avec métriques et traçage le 24 juin 2026 ; observabilité individuelle par agent en Preview depuis le 15 juin 2026 ; alignement sur les conventions sémantiques OpenTelemetry le 7 août 2026 ; support de traçage de bout en bout avec spans `execute_tool` et `invoke_connector` le 4 août 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).
- **IAM** : rôles IAM dédiés « Gemini Enterprise Admin » et « Gemini Enterprise User » introduits le 15 avril 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).
- **Conformité** : contraintes de politique organisationnelle managées pour les connecteurs de données en GA le 7 juillet 2026 ; logs d'audit d'usage dans Cloud Logging en GA le 4 février 2026 pour les deux plateformes (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).
- **Disponibilité régionale** : support Japon/UK en GA+allowlist le 6 juillet 2026 ; support Inde/Singapour en GA+allowlist le 30 juin 2026 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes).

---

## 11. Annonces récentes et jalons 2025-2026 (chronologie synthétique)

| Date | Événement |
|---|---|
| 9-10 octobre 2025 | Lancement de « Gemini Enterprise » (renommage/évolution d'Agentspace) ; annonce d'A2A, AP2, Google Skills, GEAR Program (Source : https://cloud.google.com/blog/products/ai-machine-learning/introducing-gemini-enterprise) |
| 4 février 2026 | Logs d'audit d'usage GA ; contrôle d'accès app-level GA le 2 février (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes) |
| 19 février 2026 | Gemini 3.1 Pro Preview remplace Gemini 3 Pro Preview (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes) |
| 3 mars 2026 | Veo 3.1 remplace Veo 3.0 pour la génération vidéo (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes) |
| 13 mars 2026 | Recherche image/vidéo GA (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes) |
| 22 avril 2026 | Annonce majeure : **Gemini Enterprise Agent Platform**, Agent Designer, Inbox, Projects, Canvas, Agent Gallery enrichie, partenaires Oracle/Salesforce/ServiceNow/Adobe/Workday/Accenture (Source : https://cloud.google.com/blog/products/ai-machine-learning/the-new-gemini-enterprise-one-platform-for-agent-development ; https://cloud.google.com/blog/products/ai-machine-learning/whats-new-in-gemini-enterprise) |
| 1er juin 2026 | Migration automatique des agents Agent Designer vers Gemini 3.1 Pro ; lancement de Canvas (documents/slides) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes) |
| 2 juin 2026 | Gemini 3 Pro et 3.1 Flash Image GA ; slide decks/infographies Gemini Notebook GA (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes) |
| 16 juillet 2026 | Renommage NotebookLM Enterprise → Gemini Notebook Enterprise (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes) |
| 14 juillet 2026 | Retrait de l'agent Idea Generation (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes) |
| 27 juillet 2026 | Refonte de l'interface web (navigation, thème) ; « transparent thinking » GA (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes) |
| 1er août 2026 | Édition Pay-as-you-go GA (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes) |
| 13 août 2026 | Fonctionnalité Skills GA ; Gemini 3.7 Flash GA (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes) |
| 17 août 2026 | Enregistrement d'agents A2UI/A2A en GA, support A2UI v0.9 (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes) |
| 25 août 2026 | Lancement de **Gemini Enterprise for Financial Services** (Source : https://www.googlecloudpresscorner.com/2026-08-25-Google-Cloud-Launches-Gemini-Enterprise-for-Financial-Services) |
| 26 août 2026 | Mise à jour du catalogue A2UI Material (Material 3) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/release-notes) |

---

## 12. Synthèse des points de vigilance pour l'évaluation de faisabilité (ATECNA)

1. **Volatilité du produit** : la plateforme évolue très rapidement (plusieurs dizaines de connecteurs et agents ajoutés par mois en 2026) ; toute clause contractuelle ou devis de faisabilité doit être revérifiée à la date de démarrage du projet plutôt que figée sur ce document.
2. **Beaucoup de connecteurs sont en Public Preview**, pas en GA — à valider explicitement avec le client/Google avant de s'engager sur un connecteur précis en production (le tableau de la section 6 indique le statut connu à chaque fois qu'il a pu être déterminé).
3. **Data Science Agent** relève en réalité de Colab Enterprise plus que de l'app Gemini Enterprise stricto sensu — à clarifier avec le client si le besoin porte spécifiquement sur de la data science avancée.
4. **Idea Generation a été retiré** de la plateforme (14/07/2026) — ne pas le proposer dans une offre commerciale actuelle.
5. **Le coût des agents Marketplace tiers n'est pas standardisé** : certains nécessitent un abonnement séparé chez l'éditeur (ex. Alteryx One) ; cela doit être budgété séparément par client/cas d'usage.
6. **Chiffres de capacités multimodales (langues, voix TTS) divergents selon les sources** — à reconfirmer directement avec un représentant Google Cloud ou la documentation à jour au moment du chiffrage, en particulier pour les engagements contractuels avec le client final.

---

*Fin du document. Compilé à partir de plus de 25 pages de documentation officielle Google Cloud et de sources presse consultées le 28 août 2026.*