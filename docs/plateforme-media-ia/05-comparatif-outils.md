# 5. Comparatif des outils
*Rôle simulé : consultant technologique / veille outils.*

← [Workflows](04-workflows.md) · Suivant → [Automatisation](06-automatisation.md)

---

> ⚠️ **Avertissement méthodologique** : les tarifs des outils d'IA générative évoluent en moyenne tous les 2-4 mois (nouveaux modèles, nouveaux paliers). Tous les coûts ci-dessous sont des **ordres de grandeur 🔴 à revérifier sur le site officiel avant tout engagement budgétaire** — ils servent à comparer les outils *entre eux*, pas à construire un budget définitif (le budget chiffré du plan de développement, `09-plan-developpement.md`, applique une marge d'incertitude pour cette raison).

## 5.1 Modèles de langage (LLM) — rédaction, raisonnement, orchestration

| Outil | Avantages | Inconvénients | Coût (ordre de grandeur) | Cas d'usage dans YARKAT MEDIA OS | Recommandation |
|---|---|---|---|---|---|
| **Claude** (Anthropic) | 🟢 Excellent en raisonnement long, suivi d'instructions structurées, fiabilité sur les tâches à enjeu (fact-checking, cohérence éditoriale), bon rapport qualité/coût sur les modèles milieu de gamme | 🟡 Pas de génération image/vidéo native | 🔴 Facturation à l'usage (tokens), plusieurs paliers de modèles (rapide/économique → raisonnement avancé) | Directeur éditorial, Journaliste, Fact-checker, Copywriter, Responsable qualité (LLM-as-judge) | 🟡 **Modèle par défaut du pipeline éditorial** — utiliser le palier économique pour les tâches à fort volume (Copywriter, SEO) et le palier avancé pour les décisions à enjeu (Directeur éditorial, Fact-checker) |
| **ChatGPT / GPT** (OpenAI) | 🟢 Écosystème très large, bons plugins/outils natifs, intégration native à certains outils tiers | 🟡 Coût comparable à Claude selon le palier, positionnement produit parfois plus grand public | 🔴 Facturation à l'usage, paliers multiples | Alternative/second fournisseur pour éviter la dépendance à un seul LLM (redondance stratégique) | 🟡 Garder en **fournisseur secondaire qualifié** (A/B testing qualité, bascule si incident chez le fournisseur principal) — ne pas multiplier les fournisseurs sans raison, mais ne jamais dépendre d'un seul (cf. principe d'architecture découplée §02) |
| **Gemini** (Google) | 🟢 Bonne intégration avec l'écosystème Google (YouTube Data API, Google Trends), contexte long | 🟡 Moins mature sur le suivi d'instructions complexes selon les retours d'usage courants | 🔴 Facturation à l'usage | Utile spécifiquement pour l'Analyste des tendances (proximité avec les données Google) | 🟡 Évaluer en complément ciblé plutôt qu'en remplacement du LLM principal |
| **Perplexity (API)** | 🟢 Recherche web + citation de sources en un seul appel — gain de temps déterminant pour le Fact-checker et le Journaliste | 🟡 Moins adapté à la génération créative longue | 🔴 Facturation à l'usage / abonnement API | Journaliste (recherche documentaire), Fact-checker (vérification sourcée) | 🟢 **Recommandé** comme brique de recherche dédiée plutôt que de faire chercher le LLM généraliste sur le web sans garde-fou de citation |

## 5.2 Génération d'images

| Outil | Avantages | Inconvénients | Coût (ordre de grandeur) | Cas d'usage | Recommandation |
|---|---|---|---|---|---|
| **Midjourney** | 🟢 Qualité esthétique parmi les plus hautes du marché, forte cohérence stylistique | 🟡 Contrôle fin du prompt moins direct (paramètres propriétaires), pas d'API officielle stable — accès souvent via Discord ou solutions tierces non garanties | 🔴 Abonnement mensuel par palier d'usage | Miniatures et visuels premium à fort impact esthétique | 🟡 Utiliser pour les **assets à forte visibilité** (miniatures YouTube) où l'esthétique prime, pas pour la génération en volume automatisée (contrainte d'API) |
| **FLUX** (Black Forest Labs) | 🟢 Très bon rapport qualité/coût, API stable, contrôle fin, poids ouverts disponibles pour certaines variantes (auto-hébergement possible) | 🟡 Esthétique légèrement en retrait de Midjourney sur certains styles très stylisés | 🔴 Facturation à l'image via API, ou coût de calcul si auto-hébergé | Génération d'images en volume dans le pipeline (inserts, illustrations d'article de blog) | 🟢 **Recommandé comme moteur d'image par défaut** du pipeline automatisé — API-first et économique à l'échelle |
| **Ideogram** | 🟢 Excellent rendu du texte intégré à l'image (typographie propre) | 🟡 Moins polyvalent hors cas d'usage « texte dans l'image » | 🔴 Facturation à l'usage | Miniatures avec texte accrocheur, visuels avec citations | 🟢 Recommandé spécifiquement pour les **miniatures avec texte** en complément de FLUX |

## 5.3 Génération vidéo

| Outil | Avantages | Inconvénients | Coût (ordre de grandeur) | Cas d'usage | Recommandation |
|---|---|---|---|---|---|
| **Runway** | 🟢 Contrôle créatif avancé (mouvements de caméra, extension de vidéo, édition), outils de production complémentaires (green screen IA, etc.) | 🟡 Coût par seconde de vidéo relativement élevé | 🔴 Abonnement par crédits, consommation rapide en usage intensif | Plans nécessitant un contrôle de mise en scène (Réalisateur vidéo) | 🟡 Réserver aux **plans à forte exigence créative**, pas à la génération de volume |
| **Luma (Dream Machine)** | 🟢 Bon réalisme, qualité photoréaliste | 🟡 Moins de contrôle fin sur le mouvement de caméra que Runway | 🔴 Facturation à l'usage | Plans photoréalistes (paysages, scènes réalistes) | 🟡 Alternative qualité/prix à Runway selon le style visuel de la marque |
| **Pika** | 🟢 Rapide, coût plus accessible, bon pour l'itération | 🟡 Qualité/contrôle en retrait sur les plans complexes | 🔴 Facturation à l'usage/abonnement | Génération de volume pour formats courts (Shorts/TikTok) où la vitesse d'itération prime | 🟢 **Recommandé pour le format court à haut volume**, où le coût par plan doit rester bas (cf. `03-agents-ia.md` §3.3 — poste le plus coûteux du pipeline) |

🟡 **Recommandation d'arbitrage global vidéo** : ne pas se lier à un seul fournisseur vidéo. Le Réalisateur vidéo (agent, `03-agents-ia.md`) doit pouvoir router chaque plan vers l'outil le plus rentable selon le type de plan (Pika pour le volume, Runway pour les plans premium, Luma pour le photoréalisme) — c'est précisément ce que permet l'architecture découplée définie en `02-architecture-systeme.md` §2.1.

## 5.4 Voix off / synthèse vocale

| Outil | Avantages | Inconvénients | Coût (ordre de grandeur) | Cas d'usage | Recommandation |
|---|---|---|---|---|---|
| **ElevenLabs** | 🟢 Référence qualité/naturel du marché, clonage de voix pour créer une « voix de marque » reconnaissable, support multilingue large (couvre FR/EN/ES/AR) | 🟡 Coût qui grimpe avec le volume de caractères générés à haut débit | 🔴 Abonnement par volume de caractères/minutes générées | Narrateur — toutes les marques et toutes les langues | 🟢 **Recommandé comme moteur vocal unique** de la plateforme, pour garantir une voix de marque cohérente et reconnaissable par audience |

## 5.5 Montage vidéo

| Outil | Avantages | Inconvénients | Coût (ordre de grandeur) | Cas d'usage | Recommandation |
|---|---|---|---|---|---|
| **CapCut** (API) | 🟢 Templates prêts à l'emploi optimisés pour le format court, très adapté aux codes visuels TikTok/Reels | 🟡 Moins flexible pour un montage narratif long et sur mesure | 🔴 Version API/entreprise facturée séparément de l'app grand public gratuite | Montage automatisé des formats courts (Shorts, Reels, TikTok) | 🟡 Utiliser pour les **formats courts en volume** |
| **Descript** | 🟢 Montage par édition de texte (couper la vidéo = couper le texte de la transcription), excellent pour le podcast et les formats parlés | 🟡 Moins adapté au montage très visuel/rythmé façon réseaux sociaux | 🔴 Abonnement mensuel par palier | Montage podcast, contenus longs parlés, génération de sous-titres | 🟡 Recommandé pour le **pipeline podcast** spécifiquement |
| **Pipeline FFmpeg programmatique** (non listé par l'utilisateur mais nécessaire) | 🟢 Gratuit, open source, contrôle total, scriptable pour un assemblage 100 % automatisé sans intervention dans une UI | 🔴 Demande du développement sur mesure (pas de studio visuel) | 🟢 Gratuit (coût = temps d'ingénierie) | Assemblage final automatisé (montage de base : clips + voix + sous-titres + habillage) à grande échelle | 🟢 **Recommandé comme moteur de montage principal** pour le volume, avec CapCut/Descript en complément pour les cas nécessitant un contrôle créatif humain ponctuel |

🟡 Point clé : à l'échelle de centaines de contenus/jour visée à terme (§01), **un montage 100 % piloté par une UI (CapCut/Descript en usage manuel) n'est pas industrialisable**. Le Monteur (agent) doit s'appuyer sur un pipeline FFmpeg scriptable, les outils UI restant réservés aux cas à forte valeur créative ou en phase MVP le temps de roder les templates.

## 5.6 Automatisation / orchestration

| Outil | Avantages | Inconvénients | Coût (ordre de grandeur) | Cas d'usage | Recommandation |
|---|---|---|---|---|---|
| **n8n** | 🟢 Open source, auto-hébergeable (coût maîtrisé à l'échelle), 400+ intégrations, workflows visuels lisibles par des non-développeurs, pas de coût par exécution en auto-hébergé | 🟡 Nécessite une compétence DevOps pour l'auto-hébergement en production | 🟢 Gratuit en auto-hébergé (coût = infrastructure) ou abonnement cloud managé | Orchestrateur principal de tous les workflows éditoriaux (§04) | 🟢 **Recommandé comme colonne vertébrale d'orchestration** — voir arbitrage détaillé `02-architecture-systeme.md` §2.3.3 |
| **Make (Integromat)** | 🟢 Très simple à démarrer, pas d'infrastructure à gérer, bonne UX visuelle | 🔴 Coût par « opération » qui grimpe vite à haut volume — problématique dès que le volume de contenu augmente significativement | 🔴 Abonnement par paliers d'opérations mensuelles | Prototypage rapide, workflows non critiques en volume | 🟡 Utile en **phase de prototypage MVP** pour valider un workflow vite, à migrer vers n8n avant l'industrialisation pour maîtriser le coût marginal |

## 5.7 Infrastructure et données

| Outil | Avantages | Inconvénients | Coût (ordre de grandeur) | Cas d'usage | Recommandation |
|---|---|---|---|---|---|
| **Supabase** | 🟢 PostgreSQL managé + Auth + Stockage + API auto-générée « clé en main », excellent pour démarrer vite, open source (peut être auto-hébergé plus tard) | 🟡 Certaines fonctionnalités avancées (Row-Level Security complexe multi-tenant) demandent une bonne maîtrise de Postgres | 🔴 Offre gratuite généreuse puis abonnement par paliers d'usage | Base de données + Auth du MVP | 🟢 **Recommandé pour démarrer** — migration vers Postgres auto-géré possible sans réécriture (même moteur) si le coût à l'échelle le justifie |
| **PostgreSQL** | 🟢 Standard de fait, robustesse éprouvée, extensions riches (pgvector pour le vectoriel), pas de verrouillage fournisseur | 🟡 Nécessite une gestion (sauvegardes, montée en charge) si auto-géré hors Supabase | 🟢 Gratuit (open source), coût = hébergement | Base de données principale multi-tenant (cf. `10-documentation-technique.md`) | 🟢 **Recommandé** comme moteur de données unique de la plateforme |
| **Cloudflare** (R2, CDN, Workers) | 🟢 Pas de frais de sortie sur R2 (déterminant pour le volume vidéo), CDN mondial, Workers pour des fonctions légères à la volée | 🟡 Workers moins adaptés aux traitements longs/lourds (génération vidéo) — à réserver au front léger | 🟡 Offre gratuite généreuse puis facturation à l'usage, généralement compétitive à l'échelle | Stockage/diffusion des médias (§02) | 🟢 **Recommandé** pour le stockage média et le CDN |
| **Vercel** | 🟢 Déploiement continu très simple pour Next.js, CDN intégré, excellente expérience développeur | 🟡 Coût qui peut grimper sur les fonctions serverless à très haut volume d'exécutions | 🔴 Offre gratuite puis abonnement par paliers d'usage | Hébergement du dashboard SaaS interne (front-end) | 🟢 **Recommandé** pour le front-end uniquement — pas pour les traitements IA lourds (à héberger séparément, cf. `02-architecture-systeme.md` §2.5) |

## 5.8 Synthèse — pile technologique recommandée (MVP)

| Couche | Outil retenu | Alternative de secours |
|---|---|---|
| LLM principal | Claude (paliers économique/avancé selon l'agent) | ChatGPT/GPT en fournisseur secondaire |
| Recherche factuelle | Perplexity API | — |
| Image | FLUX (volume) + Ideogram (texte) + Midjourney (assets premium ponctuels) | — |
| Vidéo | Pika (volume) + Runway (premium) + Luma (photoréaliste) | — |
| Voix | ElevenLabs | — |
| Montage | Pipeline FFmpeg (moteur principal) + CapCut (court) + Descript (podcast) | — |
| Orchestration | n8n auto-hébergé | Make en phase de prototypage uniquement |
| Base de données | Supabase (PostgreSQL managé) | PostgreSQL auto-géré si migration nécessaire |
| Stockage médias | Cloudflare R2 + CDN | AWS S3 |
| Front-end | Vercel (Next.js) | Cloudflare Pages |

🟡 Cette pile est un point de départ, pas un engagement figé : le principe d'architecture découplée (`02-architecture-systeme.md` §2.1) garantit que chaque brique peut être remplacée indépendamment quand un meilleur outil apparaît — condition de survie dans un marché qui évolue aussi vite.

---
← [Workflows](04-workflows.md) · Suivant → [Automatisation](06-automatisation.md)
