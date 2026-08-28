# Gemini Enterprise — Gouvernance & Sécurité

*Document de référence interne ATECNA — à destination DSI/RSSI. Périmètre : Google Gemini Enterprise (anciennement Google Agentspace), plateforme agentique d'entreprise de Google Cloud, éditions Business, Standard, Plus, Pay-as-you-go et Frontline. Recherche menée le 28/08/2026 à partir de la documentation officielle Google Cloud (docs.cloud.google.com/gemini/enterprise, docs.cloud.google.com/gemini-enterprise-agent-platform, cloud.google.com) et du support Google Workspace.*

⚠️ **Avertissement méthodologique** : la documentation Gemini Enterprise évolue rapidement (produit encore en forte évolution en 2026) et certaines pages de documentation Google sont rendues en JavaScript, limitant parfois l'extraction automatisée du contenu complet. Chaque affirmation ci-dessous est sourcée ; les points n'ayant pu être confirmés par une lecture directe de la page primaire sont explicitement marqués « ⚠️ Non vérifié ». Avant toute proposition commerciale engageante, il est recommandé de revérifier les certifications en cours de validité sur la page Google dédiée, Google lui-même recommandant cette vérification (Source : https://docs.cloud.google.com/gemini/enterprise/docs/compliance-security-controls).

---

## 1. Vue d'ensemble et éditions

Gemini Enterprise se décline en plusieurs éditions aux périmètres de sécurité et de gouvernance différents :

- **Business** : édition destinée aux petites structures (jusqu'à ~300 utilisateurs), documentée séparément dans le centre d'aide Google Workspace, sans accès à l'écosystème complet de connecteurs de données ni à l'Agent Marketplace (Source : https://support.google.com/g/answer/17140632?hl=en).
- **Standard / Plus** : éditions destinées aux organisations ayant des exigences de sécurité et de conformité plus strictes, avec quotas et stockage plus élevés (30 Gio/utilisateur pour Standard, 75 Gio pour Plus) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/editions).
- **Pay-as-you-go** : sans abonnement de base, facturation à la consommation de tokens/compute (Source : https://docs.cloud.google.com/gemini/enterprise/docs/editions).
- **Frontline** : palier à faible coût pour les travailleurs de terrain, en lecture seule sur des agents pré-provisionnés par un administrateur, doit être combiné avec Standard ou Plus (minimum 150 utilisateurs) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/editions).

⚠️ **Point de vigilance majeur** : la documentation officielle sur les certifications de conformité (section 9 ci-dessous) mentionne explicitement les éditions **Standard, Plus et Gemini Notebook Enterprise** (Source : https://docs.cloud.google.com/gemini/enterprise/docs/compliance-security-controls). Le statut de conformité précis de l'édition **Business** (documentée séparément via le centre d'aide Workspace) n'a pas pu être confirmé dans cette recherche — ⚠️ Non vérifié. Pour un client à exigences réglementaires fortes, il convient de vérifier explicitement l'édition sur laquelle repose chaque certification avant de s'engager.

---

## 2. Chiffrement & sécurité réseau

### Chiffrement au repos
- Gemini Enterprise applique un chiffrement par défaut avec **Customer-Managed Encryption Keys (CMEK)** via Cloud Key Management Service (Source : https://docs.cloud.google.com/gemini/enterprise/docs/security-overview).
- Le CMEK permet de garder la maîtrise du niveau de protection, de la localisation des clés, du calendrier de rotation, des permissions d'usage et d'accès (Source : https://docs.cloud.google.com/gemini/enterprise/docs/security-overview).
- Gemini Enterprise prend également en charge un **External Key Manager (EKM)** ou un module matériel de sécurité (**HSM**) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/security-overview).
- ⚠️ **Limitation régionale critique** : le CMEK et l'**Access Transparency** ne sont **pas disponibles dans la région `global`** ; le CMEK nécessite les API multi-régions US ou UE uniquement (Source : https://docs.cloud.google.com/gemini/enterprise/docs/compliance-security-controls).

### VPC Service Controls (VPC-SC)
- Gemini Enterprise est intégré à VPC Service Controls, permettant de créer un périmètre de sécurité autour des ressources (Source : https://docs.cloud.google.com/gemini/enterprise/docs/security-overview).
- Une fois le périmètre activé, l'accès public à l'API Discovery Engine (`discoveryengine.googleapis.com`) est bloqué, ainsi que l'accès à l'interface Gemini Enterprise en dehors des règles d'ingress approuvées (Source : https://docs.cloud.google.com/gemini/enterprise/docs/use-vpc-service-controls).
- **Limitations documentées à connaître** :
  - Le mode « dry run » est recommandé avant application du périmètre (Source : https://docs.cloud.google.com/gemini/enterprise/docs/use-vpc-service-controls).
  - Les actions de l'assistant Gemini Enterprise sont **bloquées par défaut** une fois VPC-SC activé ; il faut contacter son représentant Google pour les autoriser (allowlisting) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/use-vpc-service-controls).
  - L'application d'un périmètre VPC-SC sur un projet ayant déjà des data stores existants **n'est pas prise en charge** : il faut supprimer et recréer les data stores (Source : https://docs.cloud.google.com/gemini/enterprise/docs/use-vpc-service-controls).
  - Les domaines personnalisés (ex. `entreprise.atlassian.net`) nécessitent un ajout manuel à la liste blanche via le représentant Google (Source : https://docs.cloud.google.com/gemini/enterprise/docs/use-vpc-service-controls).
  - VPC-SC est conçu pour gouverner les services Google Cloud et **ne bloque pas intrinsèquement le trafic vers des points de terminaison externes non-Google** (Source : https://docs.cloud.google.com/gemini/enterprise/docs/security-overview).

### Sécurité des connecteurs tiers
- Pour les connecteurs externes, le trafic sortant est sécurisé par des règles de pare-feu VPC restreignant les connexions sortantes aux seuls noms de domaine pleinement qualifiés (FQDN) du service externe (Source : https://docs.cloud.google.com/gemini/enterprise/docs/security-overview).
- L'authentification peut s'appuyer sur Workforce Identity Federation (recommandé pour la transmission de données vers des connecteurs tiers), Google Identity, ou Workload Identity Federation (Source : https://docs.cloud.google.com/gemini/enterprise/docs/security-overview).

---

## 3. Model Armor — filtrage de contenu et protection contre les attaques

- **Model Armor** filtre de manière proactive les prompts et réponses de l'assistant Gemini Enterprise pour se prémunir contre les injections de prompt, tentatives de jailbreak, fuite d'informations sensibles et génération de contenu nuisible (Source : https://docs.cloud.google.com/gemini/enterprise/docs/enable-model-armor).
- Il couvre également la détection d'URL malveillantes et de logiciels malveillants (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/govern/monitor-content-security).
- **Disponibilité** : pris en charge sur toutes les éditions Gemini Enterprise (Standard, Plus, Pay-as-you-go, Frontline) **sans coût supplémentaire** (Source : https://docs.cloud.google.com/gemini/enterprise/docs/enable-model-armor). Sur l'édition Business, la protection est activée par défaut via des modèles de sécurité préconfigurés gérés par Google (Source : https://support.google.com/g/answer/17140632?hl=en).
- ⚠️ **Limitation importante** : Model Armor **ne masque pas et ne dé-identifie pas** les informations personnelles ; en cas de détection via Sensitive Data Protection, Gemini Enterprise **bloque intégralement** la réponse concernée plutôt que de la caviarder (Source : https://docs.cloud.google.com/gemini/enterprise/docs/enable-model-armor).
- ⚠️ **Limitation de périmètre critique pour un RSSI** : Model Armor ne filtre les interactions qu'avec l'assistant et les agents créés par des employés ou par Google — **il ne couvre pas les agents personnalisés créés par l'organisation** (Source : https://docs.cloud.google.com/gemini/enterprise/docs/enable-model-armor).
- Le filtrage peut introduire de la latence, et sa configuration nécessite les rôles IAM « Gemini Enterprise Admin » (activation), « Model Armor Admin » (création de modèles) et « Model Armor User » (appels API) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/enable-model-armor).
- Un tableau de bord de supervision permet de suivre les interactions signalées/bloquées, avec vue au niveau projet ou agent, un classement des 10 agents les plus concernés, une interface de requêtes SQL (Observability Analytics) et un export CSV/PNG ; l'accès nécessite les rôles « Observability View Accessor » et « Logs Viewer » (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/govern/monitor-content-security).

---

## 4. IAM & contrôle d'accès

### Rôles prédéfinis (couche application Gemini Enterprise / Discovery Engine)
Quatre rôles hiérarchiques principaux sont proposés (Source : https://docs.cloud.google.com/gemini/enterprise/docs/access-control) :

| Rôle | Identifiant | Portée |
|---|---|---|
| Gemini Enterprise Admin | `roles/discoveryengine.agentspaceAdmin` | Administration complète : configuration Cloud AI Companion, journalisation, canaux de version, propositions de politiques IAM personnalisées |
| Discovery Engine Editor | `roles/discoveryengine.editor` | Lecture/écriture sur les ressources Discovery Engine |
| Gemini Enterprise User | `roles/discoveryengine.agentspaceUser` | Usage applicatif — nécessite une licence active |
| Discovery Engine Viewer | `roles/discoveryengine.viewer` | Lecture seule |

- Les rôles sont hiérarchiques : Editor inclut les permissions de Viewer, etc. (Source : https://docs.cloud.google.com/gemini/enterprise/docs/access-control).
- Des **rôles personnalisés** peuvent être créés lorsque les rôles prédéfinis ne correspondent pas exactement au besoin de moindre privilège (Source : https://docs.cloud.google.com/gemini/enterprise/docs/access-control).
- Pour désigner des administrateurs, le propriétaire du projet doit attribuer les rôles « Gemini Enterprise Admin », « Service Usage Consumer » et « Logs Viewer » (Source : https://docs.cloud.google.com/gemini/enterprise/docs/access-control).

### Rôles au niveau de la plateforme agentique sous-jacente
La couche « Agent Platform » (Vertex AI) dispose de ses propres rôles prédéfinis — Administrateur (`roles/aiplatform.admin`) et Utilisateur (`roles/aiplatform.user`) — distincts des rôles Discovery Engine ci-dessus, gérés via la console IAM de Google Cloud (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/machine-learning/general/access-control). Un RSSI doit donc considérer **deux couches IAM distinctes** (application Gemini Enterprise et plateforme d'agents sous-jacente) lors d'un audit d'accès.

### Politiques IAM au niveau des agents (Agent Gateway)
Au-delà de l'IAM classique par projet, Gemini Enterprise Agent Platform permet de définir des politiques d'accès **spécifiques à chaque agent**, appliquées via un composant Identity-Aware Proxy (Agent Gateway), couvrant quatre types d'interactions : agent-vers-registre, agent-vers-agent, agent-vers-serveur MCP, et agent-vers-endpoint (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/govern/policies/configure-iam-policies).

- Chaque agent possède une identité formatée `principal://TRUST_DOMAIN/AGENT_UNIQUE_IDENTIFIER` (agents natifs Agent Runtime/Gemini Enterprise) ou une identité par compte de service (agents « DIY » sur Cloud Run) (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/govern/policies/configure-iam-policies).
- Les politiques supportent des conditions au format CEL (« Common Expression Language ») portant sur cinq types : nom de ressource, lecture seule (`ReadOnly`), action destructive (`Destructive`), idempotence (`Idempotent`) et interaction avec le monde extérieur (`Open World`) (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/govern/policies/configure-iam-policies).
- Les ressources ciblées doivent être préalablement enregistrées dans l'Agent Registry ; un mode « dry-run » est recommandé lors de la configuration initiale de l'Agent Gateway (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/govern/policies/configure-iam-policies).
- Au-delà des politiques IAM, des **« Semantic Governance Policies »** ajoutent une couche de contrôle comportemental visant à s'assurer que les actions de l'agent correspondent à l'intention de l'utilisateur et aux contraintes organisationnelles (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/govern).

---

## 5. Gouvernance des agents (Agent Registry, topologie, cycle de vie)

L'Agent Platform sert de console centrale pour les administrateurs plateforme et sécurité afin de gouverner l'ensemble du cycle de vie des agents (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/govern).

- **Agent Registry** : catalogue centralisé permettant de stocker, découvrir et gouverner les serveurs, outils et agents IA au sein de Google Cloud (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/govern).
- **Graphes de topologie** : visualisation en temps réel des relations et flux de trafic entre l'ensemble des agents et serveurs MCP (Model Context Protocol), afin de comprendre les dépendances complexes entre agents (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/govern).
- **Agent Identity et Agent Gateways** garantissent que chaque interaction — de l'utilisateur jusqu'au modèle — est authentifiée et pilotée par une politique (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/govern).
- L'Agent Gateway fonctionne comme point de contrôle centralisé du trafic agentique, avec supervision du trafic, délégation d'autorisation et gestion de la connectivité VPC (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/govern).
- Des pistes d'audit sont maintenues via des journaux de politiques et des tableaux de bord de supervision, permettant de suivre les accès aux données et les journaux requête-réponse (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/govern).

⚠️ Ces fonctionnalités de gouvernance avancée (Agent Registry, topologie, Agent Gateway) relèvent de la couche « Gemini Enterprise **Agent Platform** » (anciennement partie de l'offre Agentspace / Vertex AI Agent Builder), distincte de l'application « Gemini Enterprise » grand public en libre-service. Leur disponibilité par édition commerciale n'a pas pu être confirmée précisément dans cette recherche — ⚠️ Non vérifié, à valider projet par projet.

---

## 6. Journalisation et audit

- Les journaux d'usage Gemini Enterprise sont accessibles via **Cloud Logging** et couvrent : opérations de recherche (requêtes, jetons d'attribution, identifiants de résultats), interactions avec l'assistant (contenu de requête/réponse, y compris contenu ancré et citations), gestion des moteurs (engines), opérations sur les agents (création, mise à jour, suppression, modifications de politiques IAM), mises à jour des connecteurs de données, et opérations sur fichiers (Source : https://docs.cloud.google.com/gemini/enterprise/docs/set-up-usage-audit-logs).
- ⚠️ **Point de vigilance majeur pour un RSSI** : la documentation indique explicitement que **« les données sensibles ne sont pas filtrées des journaux d'audit »** — le contenu des prompts et des réponses, y compris des données personnelles potentielles, est donc conservé tel quel dans les logs (Source : https://docs.cloud.google.com/gemini/enterprise/docs/set-up-usage-audit-logs). Cela implique un contrôle d'accès strict sur les journaux eux-mêmes.
- Configuration : nécessite le rôle « Gemini Enterprise Admin » (`roles/discoveryengine.agentspaceAdmin`) ; consultation des logs : rôle « Logs Viewer » (`roles/logging.viewer`) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/set-up-usage-audit-logs).
- Les logs sont envoyés par défaut au bucket `_Default` de Cloud Logging (Source : https://docs.cloud.google.com/gemini/enterprise/docs/set-up-usage-audit-logs).
- Des mécanismes de contrôle d'accès fin sont disponibles : conditions IAM, vues de logs (log views), puits (sinks), tags (Source : https://docs.cloud.google.com/gemini/enterprise/docs/set-up-usage-audit-logs).
- La durée de rétention des journaux d'audit eux-mêmes n'est pas précisée dans cette documentation — ⚠️ Non vérifié.

---

## 7. Confidentialité des données et utilisation pour l'entraînement des modèles

### Engagement de non-entraînement (Training Restriction)
- La documentation officielle de zéro rétention de données indique : **« Google won't use your data to train or fine-tune any AI/ML models without your prior permission or instruction »**, précisant que cela s'applique **à tous les modèles gérés sur Gemini Enterprise Agent Platform, y compris les modèles GA et pré-GA** (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/resources/zero-data-retention).
- Pour Gemini sur Google Cloud de manière générale : « Gemini doesn't use your prompts or its responses as data to train its models » (Source : https://docs.cloud.google.com/gemini/docs/discover/data-governance).
- Cet engagement repose contractuellement sur la clause dite « Training Restriction » des Service Specific Terms de Google Cloud : « Google will not use Customer Data to train or fine-tune any AI/ML models without Customer's prior permission or instruction » (Source : https://cloud.google.com/terms/service-terms). ⚠️ Il s'agit d'une clause contractuelle générale applicable aux services d'IA générative de Google Cloud, et non d'un texte spécifique à Gemini Enterprise — à faire confirmer par la direction juridique dans le contrat-cadre applicable au client.
- Ce principe s'inscrit dans le cadre plus large du « AI/ML Privacy Commitment » publié par Google Cloud (Source : https://cloud.google.com/blog/products/ai-machine-learning/google-cloud-unveils-ai-and-ml-privacy-commitment).

### ⚠️ Nuance importante : surveillance des abus (abuse monitoring)
- Pour atteindre une « rétention zéro » des données, le client doit prendre des mesures spécifiques par domaine fonctionnel ; en particulier, la journalisation des prompts à des fins de détection d'abus reste possible pour les modèles Google, en application de la section 4.3 « Generative AI Safety and Abuse » des conditions de service Google Cloud Platform, selon laquelle **Google peut journaliser les prompts pour détecter des abus potentiels et des violations de sa politique d'utilisation acceptable** (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/resources/zero-data-retention). Ce point constitue une exception documentée à l'engagement de non-utilisation/non-conservation des données, à mentionner explicitement à un client sensible à la confidentialité.

### Rétentions spécifiques par fonctionnalité
- **CodeMender** : les données de session (extraits de code, états de suivi) sont conservées jusqu'à 7 jours, puis supprimées automatiquement (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/resources/zero-data-retention).
- **Deep Research** : prompts et résultats générés conservés 7 jours en traitement standard ; lorsque le « Grounding with Google Search » est utilisé, Google conserve prompts, informations contextuelles et résultats générés pendant 3 jours à des fins de débogage et de test (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/resources/zero-data-retention).
- **Grounding with Parallel Web Search** : une option de rétention zéro dédiée existe pour les charges de travail sensibles, nécessitant un abonnement spécifique et l'activation d'un indicateur `enable_zero_data_retention` dans les appels API (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/resources/zero-data-retention).
- Suppression des données à la demande de l'utilisateur : Gemini Enterprise supprime les données concernées **sous 60 jours** (Source : https://docs.cloud.google.com/gemini/enterprise/docs/security-overview).

---

## 8. Résidence des données (Data Residency)

- Régions multi-régionales disponibles : `us` (États-Unis), `eu` (Union européenne), `global` (par défaut, mondial) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/locations).
- Régions locales (« in-country », en disponibilité générale sur liste blanche) : Canada (`ca`), Inde (`in`), Japon (`asia-northeast1`), Singapour (`sg`), Royaume-Uni (`europe-west2`) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/locations).
- La localisation choisie contrôle à la fois la **résidence des données au repos** (Data Residency Zone) et la **localisation du traitement de Machine Learning** (entraînement, prédiction, ajustement de modèle — « MLP ») : un choix `eu` garantit que le MLP se déroule dans la multi-région UE (Source : https://docs.cloud.google.com/gemini/enterprise/docs/locations).
- ⚠️ **Arbitrage à exposer clairement à un client européen** : la région `global` offre de meilleurs temps de réponse, les derniers modèles et fonctionnalités les plus récentes, mais **sacrifie l'engagement de résidence des données** (Source : https://docs.cloud.google.com/gemini/enterprise/docs/locations). Certaines fonctionnalités avancées (par ex. certaines capacités liées à Gemini 3.7 Flash, la génération vidéo, les facettes dynamiques, le « Grounding with Google Search ») ne sont disponibles **que** dans la région `global` (Source : https://docs.cloud.google.com/gemini/enterprise/docs/locations). Les régions locales ont des limitations de parité fonctionnelle similaires aux multi-régions `us`/`eu` (Source : https://docs.cloud.google.com/gemini/enterprise/docs/locations).
- Le CMEK n'est pas disponible en région `global` (Source : https://docs.cloud.google.com/gemini/enterprise/docs/locations ; https://docs.cloud.google.com/gemini/enterprise/docs/compliance-security-controls).

### Positionnement RGPD
- Aucune « certification RGPD » en tant que telle n'apparaît dans la liste des certifications Gemini Enterprise (voir section 9) — le RGPD n'est pas un référentiel de certification mais un cadre réglementaire adressé de façon **contractuelle** (Data Processing Addendum / DPA couvrant les obligations de l'article 28) et **technique** (options de résidence UE ci-dessus) (Source : https://docs.cloud.google.com/gemini/docs/discover/data-governance, qui référence le Cloud Data Processing Addendum). ⚠️ Le contenu précis du DPA applicable à Gemini Enterprise spécifiquement (par opposition au DPA Google Cloud générique) n'a pas été vérifié directement dans cette recherche — ⚠️ Non vérifié, à faire valider par le service juridique via https://cloud.google.com/terms/data-processing-addendum.

---

## 9. Conformité & certifications

D'après la page officielle de conformité, s'appliquant aux éditions **Standard, Plus, et Gemini Notebook Enterprise** (Source : https://docs.cloud.google.com/gemini/enterprise/docs/compliance-security-controls) :

| Référentiel | Statut mentionné | Remarques |
|---|---|---|
| HIPAA | Pris en charge | Nécessite en pratique un Business Associate Agreement (BAA) signé et l'usage d'un périmètre de produit éligible — HIPAA ne s'applique qu'aux surfaces produit couvertes par la BAA (Source : https://docs.cloud.google.com/gemini/enterprise/docs/compliance-security-controls) |
| FedRAMP | Pris en charge | Voir distinction Low / High détaillée ci-dessous |
| ISO 27001, 27017, 27018, 27701 | Pris en charge | Sécurité de l'information, sécurité cloud, protection des données personnelles, gestion de la vie privée |
| SOC 1, SOC 2, SOC 3 | Pris en charge | — |
| PCI DSS | Pris en charge | — |
| BSI C5:2020 | Pris en charge | Référentiel allemand (Cloud Computing Compliance Criteria Catalogue) |

⚠️ **Recommandation explicite de Google elle-même** : la documentation invite l'utilisateur à rechercher le nom exact du produit (« Gemini Enterprise » ou « Gemini Notebook ») sur les pages de conformité de sécurité de Google Cloud afin de confirmer quel produit précis détient chaque certification (Source : https://docs.cloud.google.com/gemini/enterprise/docs/compliance-security-controls) — ce qui suggère que la liste peut évoluer et ne doit pas être considérée comme figée dans une proposition commerciale.

⚠️ **Produits adjacents à ne pas confondre avec Gemini Enterprise** : la même page de documentation liste des exclusions pour deux produits distincts figurant dans le même tableau de comparaison — **AlphaEvolve** (ne prend en charge ni ITAR, ni FedRAMP Modéré/Élevé, ni IL4/IL5, ni les certifications ISO) et **Antigravity** (ne prend en charge ni Access Transparency, ni FedRAMP Modéré/Élevé, ni IL4/IL5, ni les certifications ISO, ni ITAR, ni SOC 1/2/3) (Source : https://docs.cloud.google.com/gemini/enterprise/docs/compliance-security-controls). Il s'agit d'outils Google distincts (agents/outils de développement), non de Gemini Enterprise lui-même ; à ne pas mélanger dans un discours commercial.

### FedRAMP — deux parcours distincts à ne pas confondre

**a) FedRAMP 20x Class B (Low)**
- Autorisation couvrant « des informations publiquement diffusables avec une sensibilité minimale » (Source : https://docs.cloud.google.com/docs/security/compliance/config-fedramp20x-gemini-gov).
- Neuf services sont couverts par cette autorisation : Gemini Enterprise, l'IA générative sur Gemini Enterprise Agent Platform, BigQuery, Cloud Storage, Looker (cœur Google Cloud), Conversational Agents, Gemini Code Assist, NotebookLM Enterprise, et Agent Search sur Gemini Enterprise Agent Platform (Source : https://docs.cloud.google.com/docs/security/compliance/config-fedramp20x-gemini-gov).
- Configuration : création d'un projet Google Cloud, activation de Gemini Enterprise (édition Standard activée automatiquement avec Gemini for Government), mise en œuvre d'IAM, VPC-SC, CMEK, Access Transparency et journalisation d'audit selon les politiques de l'agence, puis suivi via le Compliance Manager de Security Command Center (Source : https://docs.cloud.google.com/docs/security/compliance/config-fedramp20x-gemini-gov).
- ⚠️ Cette autorisation est destinée aux informations non classifiées à sensibilité minimale uniquement ; les artefacts d'audit fournis « ne garantissent pas de satisfaire toutes les exigences des auditeurs ou régulateurs » (Source : https://docs.cloud.google.com/docs/security/compliance/config-fedramp20x-gemini-gov).

**b) FedRAMP High + DoD Impact Level 4 (IL4) — via « Gemini for Government »**
- Nécessite un déploiement au sein d'un dossier **Assured Workloads** configuré pour le régime de conformité visé, avec sélection obligatoire de la région « US Multi-region » (Source : https://docs.cloud.google.com/docs/security/compliance/deploy-gemini-gov).
- Les data stores autorisés pour FedRAMP High et IL4 sont limités à Cloud Storage et BigQuery (Source : https://docs.cloud.google.com/docs/security/compliance/deploy-gemini-gov).
- ⚠️ **De nombreuses fonctionnalités doivent être désactivées manuellement ou ne sont tout simplement pas autorisées** dans ce mode : galerie de prompts, ancrage (grounding) via Google Maps/Search, génération d'images (Imagen) et de vidéos (Veo), collecte d'événements utilisateurs, personnalisation et fonctions de mémoire, Private Knowledge Graph, **Model Armor (non autorisé en IL4)**, mise en cache de contexte implicite, NotebookLM (IL4/IL5) ; par ailleurs, l'agent Idea Generation, les fonctionnalités d'Analytics associées, Gemini dans BigQuery/Looker, Gemini Code Assist, Cloud SQL et Firestore comme data stores ne peuvent pas être désactivés et nécessitent une évaluation de risque dédiée (Source : https://docs.cloud.google.com/docs/security/compliance/deploy-gemini-gov).
- ⚠️ Le statut de Looker diffère selon le régime : « autorisé » pour FedRAMP High mais seulement « soumis » (non encore autorisé) pour IL4, ce qui affecte les fonctionnalités Gemini-dans-Looker qui en dépendent (Source : https://docs.cloud.google.com/docs/security/compliance/deploy-gemini-gov).
- La conformité des modèles tiers reste de la responsabilité du client malgré une infrastructure de service autorisée (Source : https://docs.cloud.google.com/docs/security/compliance/deploy-gemini-gov).

**Conclusion à retenir pour un discours DSI/RSSI** : FedRAMP High n'est **pas** un mode « par défaut » de Gemini Enterprise — il exige une architecture de déploiement dédiée (Gemini for Government / Assured Workloads) avec un périmètre fonctionnel volontairement réduit. Présenter Gemini Enterprise standard comme « FedRAMP High compliant » sans cette précision serait trompeur.

---

## 10. Protection contre la perte de données (DLP) et données sensibles

- Model Armor s'intègre avec **Sensitive Data Protection** (service DLP de Google Cloud) pour détecter des types d'informations personnalisés et prédéfinis dans les prompts et réponses des agents (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/govern/monitor-content-security).
- ⚠️ **Distinction importante à ne pas gommer** : les contrôles DLP au niveau du navigateur (blocage du copier/coller, de l'impression, des téléversements/téléchargements de données sensibles autour de Gemini dans les applications Workspace) relèvent d'un **produit distinct**, Chrome Enterprise Premium, et non d'une fonctionnalité native de Gemini Enterprise Agent Platform (Source : https://workspace.google.com/blog/ai-and-machine-learning/enterprise-security-controls-google-workspace-gemini). ⚠️ Non vérifié en détail dans cette recherche — à confirmer avant de le présenter comme une fonctionnalité intégrée de Gemini Enterprise plutôt que comme un produit Workspace complémentaire.

---

## 11. Synthèse des points de vigilance pour un DSI/RSSI

Liste de contrôle des nuances à intégrer systématiquement dans tout discours commercial ou architecture de référence :

1. **Statut de conformité Business edition non confirmé** — le tableau de certifications officiel cible explicitement Standard/Plus/Notebook Enterprise ; vérifier séparément pour Business avant toute promesse contractuelle. ⚠️ Non vérifié.
2. **FedRAMP High n'est pas automatique** — nécessite un déploiement « Gemini for Government » via Assured Workloads, avec de nombreuses fonctionnalités désactivées (y compris Model Armor en IL4) (Source : https://docs.cloud.google.com/docs/security/compliance/deploy-gemini-gov).
3. **CMEK et Access Transparency indisponibles en région `global`** — un choix de région `global` pour bénéficier des derniers modèles/fonctionnalités implique de renoncer à ces contrôles (Source : https://docs.cloud.google.com/gemini/enterprise/docs/compliance-security-controls).
4. **Les journaux d'audit contiennent le texte intégral des prompts et réponses, non filtré des données sensibles** — un contrôle d'accès rigoureux sur Cloud Logging est indispensable (Source : https://docs.cloud.google.com/gemini/enterprise/docs/set-up-usage-audit-logs).
5. **Model Armor ne couvre pas les agents personnalisés créés par l'organisation**, seulement l'assistant et les agents Google/employés (Source : https://docs.cloud.google.com/gemini/enterprise/docs/enable-model-armor).
6. **L'engagement « pas d'entraînement sur les données clients » comporte une exception documentée pour la détection d'abus** (journalisation possible sous la clause 4.3 des conditions GCP) (Source : https://docs.cloud.google.com/gemini-enterprise-agent-platform/resources/zero-data-retention).
7. **Le RGPD est adressé contractuellement (DPA) et techniquement (résidence UE), pas via une « certification RGPD »** — à ne pas présenter comme une certification au même titre qu'ISO ou SOC.
8. **VPC-SC impose des contraintes de migration** : les data stores existants doivent être recréés pour appliquer un nouveau périmètre, et les actions de l'assistant sont bloquées par défaut jusqu'à allowlisting via un représentant Google (Source : https://docs.cloud.google.com/gemini/enterprise/docs/use-vpc-service-controls).
9. **Google recommande lui-même de revérifier en direct** la liste des certifications sur ses pages de conformité avant de s'appuyer dessus commercialement (Source : https://docs.cloud.google.com/gemini/enterprise/docs/compliance-security-controls).
10. **Deux couches IAM distinctes coexistent** (rôles Discovery Engine au niveau application, rôles `aiplatform.*` au niveau plateforme d'agents), à couvrir toutes deux lors d'un audit d'accès (Source : https://docs.cloud.google.com/gemini/enterprise/docs/access-control ; https://docs.cloud.google.com/gemini-enterprise-agent-platform/machine-learning/general/access-control).

---

## Sources consultées

- https://docs.cloud.google.com/gemini/enterprise/docs/security-overview
- https://docs.cloud.google.com/gemini/enterprise/docs/compliance-security-controls
- https://docs.cloud.google.com/gemini/enterprise/docs/use-vpc-service-controls
- https://docs.cloud.google.com/gemini/enterprise/docs/access-control
- https://docs.cloud.google.com/gemini/enterprise/docs/enable-model-armor
- https://docs.cloud.google.com/gemini/enterprise/docs/set-up-usage-audit-logs
- https://docs.cloud.google.com/gemini/enterprise/docs/locations
- https://docs.cloud.google.com/gemini/enterprise/docs/editions
- https://docs.cloud.google.com/gemini-enterprise-agent-platform/resources/zero-data-retention
- https://docs.cloud.google.com/gemini-enterprise-agent-platform/govern
- https://docs.cloud.google.com/gemini-enterprise-agent-platform/govern/monitor-content-security
- https://docs.cloud.google.com/gemini-enterprise-agent-platform/govern/policies/configure-iam-policies
- https://docs.cloud.google.com/gemini-enterprise-agent-platform/machine-learning/general/access-control
- https://docs.cloud.google.com/gemini/docs/discover/data-governance
- https://docs.cloud.google.com/docs/security/compliance/config-fedramp20x-gemini-gov
- https://docs.cloud.google.com/docs/security/compliance/deploy-gemini-gov
- https://cloud.google.com/terms/service-terms
- https://cloud.google.com/blog/products/ai-machine-learning/google-cloud-unveils-ai-and-ml-privacy-commitment
- https://support.google.com/g/answer/17140632?hl=en (Gemini Enterprise – Business Edition, sécurité)
- https://workspace.google.com/blog/ai-and-machine-learning/enterprise-security-controls-google-workspace-gemini

---

*Note sur la méthode de recherche : ce document a été construit en combinant (1) une lecture directe (WebFetch) des pages primaires `docs.cloud.google.com` et `cloud.google.com` chaque fois que possible, et (2) pour les pages dont le rendu JavaScript a empêché une extraction complète en lecture directe, l'exploitation des extraits indexés par la recherche web sur ces mêmes URLs officielles Google. Aucune source tierce (blogs non-Google, sites de conseil en conformité) n'a été utilisée comme fondement d'une affirmation factuelle dans ce document ; ces sources tierces rencontrées durant la recherche ont été écartées ou explicitement signalées lorsqu'un doute subsistait.*
