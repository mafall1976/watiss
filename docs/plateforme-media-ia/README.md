# Dossier de conception — Plateforme média pilotée par IA
### Nom de code du projet : **YARKAT MEDIA OS**

> Filiale média augmentée par l'IA d'une holding patrimoniale — production et distribution automatisées de contenus multi-plateformes, multi-marques, multilingues.

---

## Pourquoi ce dossier est découpé en plusieurs documents

Un document unique de cette ampleur (stratégie + architecture + IA + automatisation + UI + finance + planning + specs techniques) dilue la profondeur de chaque sujet. Ce dossier applique donc la méthode demandée : **chaque volet est traité comme s'il provenait d'un prompt spécialisé dédié**, rédigé par un rôle d'expert différent (CTO, architecte, directeur produit, économiste, etc.), puis assemblé en un dossier cohérent. Les documents se référencent mutuellement plutôt que de se répéter.

## Convention de lecture

- 🟢 **Établi** : fait vérifiable (capacités d'un outil, prix public, contrainte technique connue).
- 🟡 **Recommandation** : choix argumenté de ce dossier, à valider par vous/le comité d'investissement.
- 🔴 **Hypothèse à confirmer** : donnée manquante, estimée par analogie sectorielle — à ne pas traiter comme un fait.

Tous les coûts sont indiqués en **EUR**, TVA/charges non incluses sauf mention contraire, avec l'hypothèse retenue explicitée à chaque fois.

## Sommaire

| # | Document | Rôle auteur simulé | Contenu |
|---|----------|--------------------|---------|
| 1 | [`01-vision-strategique.md`](01-vision-strategique.md) | Entrepreneur / CEO | Mission, modèle économique, avantages concurrentiels, risques, barrières à l'entrée, feuille de route 3 ans |
| 2 | [`02-architecture-systeme.md`](02-architecture-systeme.md) | Architecte systèmes / CTO | Architecture complète, composants, schémas Mermaid, choix techniques justifiés |
| 3 | [`03-agents-ia.md`](03-agents-ia.md) | Directeur IA / Prompt engineer | 15 agents spécialisés : mission, compétences, modèles, I/O, interactions |
| 4 | [`04-workflows.md`](04-workflows.md) | Directeur des opérations | Workflows bout-en-bout, diagrammes Mermaid, boucles de reprise |
| 5 | [`05-comparatif-outils.md`](05-comparatif-outils.md) | Consultant techno / veille outils | Comparatif chiffré de 19 outils (LLM, génératif image/vidéo/voix, automatisation, infra) |
| 6 | [`06-automatisation.md`](06-automatisation.md) | Expert automatisation (n8n/Make/MCP) | Déclencheurs, files d'attente, validations auto, reprise après erreur, observabilité |
| 7 | [`07-interface-utilisateur.md`](07-interface-utilisateur.md) | Directeur produit / UX | Wireframes texte du SaaS interne : dashboard, calendrier éditorial, médiathèque, analytics |
| 8 | [`08-modele-economique.md`](08-modele-economique.md) | CFO / stratège monétisation | 10 leviers de revenus, 3 scénarios de croissance chiffrés |
| 9 | [`09-plan-developpement.md`](09-plan-developpement.md) | Directeur de programme | MVP → V1 → V2 → Entreprise : fonctionnalités, budget, ressources, délais, risques |
| 10 | [`10-documentation-technique.md`](10-documentation-technique.md) | Lead développeur | Arborescence, conventions, modèles de données, API REST/GraphQL, schémas JSON, sécurité, sauvegardes |
| 11 | [`11-ameliorations-futures.md`](11-ameliorations-futures.md) | R&D | Fonctionnalités moyen/long terme |

## Périmètre couvert par la demande d'origine

- **Canaux** : YouTube, YouTube Shorts, Facebook, Instagram, TikTok, LinkedIn, X, Podcasts, Blog, Newsletter.
- **Langues au lancement** : FR, EN, ES, AR (RTL) — extensible.
- **Modularité** : socle technique unique (« YARKAT MEDIA OS ») opérant plusieurs marques de contenu indépendantes (« brands » / tenants).
- **Chaîne de valeur automatisée** : détection de sujets → vérification → script → génération image/vidéo → voix → montage → miniatures → métadonnées SEO par réseau → publication → analytics → apprentissage.

## Ce que ce dossier n'est pas

- Ce n'est pas un audit juridique (droit d'auteur IA, RGPD, obligations de transparence IA type AI Act/DSA) — un volet dédié dans `01-vision-strategique.md` §6 signale ce risque mais **ne remplace pas un avis juridique**.
- Les prix d'API listés dans `05-comparatif-outils.md` évoluent vite : à revérifier avant tout engagement budgétaire (marqués 🔴 le cas échéant).
