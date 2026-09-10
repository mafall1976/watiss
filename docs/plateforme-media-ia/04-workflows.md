# 4. Les workflows
*Rôle simulé : directeur des opérations.*

← [Agents IA](03-agents-ia.md) · Suivant → [Comparatif des outils](05-comparatif-outils.md)

---

## 4.1 Workflow maître (bout-en-bout)

```mermaid
flowchart TD
    S1[1. Détection d'un sujet\nAnalyste des tendances] --> S2[2. Cadrage éditorial\nDirecteur éditorial]
    S2 -->|approuvé| S3[3. Recherche documentaire\nJournaliste]
    S2 -->|rejeté| END1[Archivé]
    S3 --> S4[4. Rédaction du script\nJournaliste]
    S4 --> S5{5. Fact-checking\nFact-checker}
    S5 -->|corrections requises| S4
    S5 -->|drapeau sensible| H1{{Validation humaine}}
    H1 -->|refusé| END1
    H1 -->|validé| S6
    S5 -->|validé, non sensible| S6[6. Adaptation multi-canal\nCopywriter]
    S6 --> S7[7. Création des prompts visuels\nPrompt Engineer]
    S7 --> S8[8a. Génération d'images\nDesigner IA]
    S7 --> S9[8b. Génération vidéo\nRéalisateur vidéo]
    S6 --> S10[8c. Génération voix off\nNarrateur]
    S8 --> S11[9. Montage final\nMonteur]
    S9 --> S11
    S10 --> S11
    S11 --> S12{10. Contrôle qualité\nResponsable qualité}
    S12 -->|score insuffisant| S13[Retour à l'agent producteur concerné]
    S13 --> S11
    S12 -->|score OK| S14[11. Métadonnées SEO par canal\nExpert SEO]
    S14 --> S15[12. Publication programmée\nCommunity Manager]
    S15 --> S16[13. Collecte analytics\nAnalyste de données]
    S16 --> S17[14. Détection d'opportunités de revenu\nResponsable monétisation]
    S16 --> S18[15. Boucle d'apprentissage]
    S18 -.réinjecte.-> S1
    S18 -.réinjecte.-> S7
```

**Points de contrôle humain obligatoires (non contournables par design, cf. `01-vision-strategique.md` §1.5 et `06-automatisation.md` §validations) :**
1. Sujet marqué sensible par la charte de marque (santé, finance, politique, mineurs) → validation avant script.
2. Score qualité insuffisant après 2 tentatives de correction automatique par le même agent → escalade humaine plutôt que boucle infinie.
3. Nouveau partenariat de monétisation (jamais automatique, cf. `03-agents-ia.md` Responsable monétisation).
4. Réponse de modération sortant du script prédéfini (Community Manager).

## 4.2 Workflow détaillé — Production vidéo longue (YouTube)

```mermaid
sequenceDiagram
    participant DE as Directeur éditorial
    participant JO as Journaliste
    participant FC as Fact-checker
    participant CW as Copywriter
    participant PE as Prompt Engineer
    participant DI as Designer IA
    participant RV as Réalisateur vidéo
    participant NA as Narrateur
    participant MT as Monteur
    participant RQ as Responsable qualité
    participant CM as Community Manager

    DE->>JO: Brief (sujet, angle, durée cible 8-12 min)
    JO->>FC: Script + sources
    FC-->>JO: Corrections (itération 1-N)
    FC->>CW: Script validé
    CW->>PE: Découpage en ~40-60 plans
    par Génération parallèle
        PE->>DI: Prompts images (miniature + inserts)
        PE->>RV: Prompts vidéo (plans animés)
        CW->>NA: Script minuté
    end
    DI-->>MT: Assets image
    RV-->>MT: Clips vidéo
    NA-->>MT: Piste audio + sous-titres
    MT->>RQ: Vidéo assemblée (master 16:9)
    RQ-->>MT: Score qualité + corrections éventuelles
    RQ->>CM: Vidéo validée
    MT->>MT: Déclinaisons formats (9:16, 1:1) à partir du master
    CM->>CM: Publication programmée multi-plateforme
```

🟡 Recommandation : générer un **master unique** (16:9 haute résolution) puis dériver automatiquement les formats verticaux/carrés par recadrage intelligent + reformatage des sous-titres, plutôt que régénérer une vidéo IA distincte par format — c'est le levier de coût le plus direct sur l'agent le plus cher (Réalisateur vidéo, cf. `03-agents-ia.md` §3.3).

## 4.3 Workflow détaillé — Contenu court (Shorts / Reels / TikTok)

```mermaid
flowchart LR
    A[Master vidéo longue\nOU sujet dédié format court] --> B{Source ?}
    B -->|Extrait du long format| C[Détection automatique\ndes meilleurs moments\nAnalyste de données + Copywriter]
    B -->|Création dédiée| D[Cycle complet accéléré\nscript court → prompts → génération]
    C --> E[Recadrage 9:16 + sous-titres dynamiques]
    D --> E
    E --> F[Hook renforcé dans les 3 premières secondes\nCopywriter]
    F --> G[Contrôle qualité rapide\nResponsable qualité — grille allégée]
    G --> H[Publication native par plateforme\nCommunity Manager]
    H --> I[TikTok]
    H --> J[YouTube Shorts]
    H --> K[Instagram Reels]
```

🟡 Le format court a une **grille de contrôle qualité allégée** (durée de production plus courte, moindre enjeu réputationnel unitaire) mais **jamais nulle** — le Responsable qualité reste dans la boucle car le volume élevé de shorts est justement ce qui peut faire dériver la marque le plus vite si non supervisé.

## 4.4 Workflow détaillé — Blog + Newsletter (contenu texte long)

```mermaid
flowchart TD
    A[Script/Article source\nJournaliste + Fact-checker] --> B[Structuration SEO\nExpert SEO]
    B --> C[Rédaction longue optimisée\nCopywriter]
    C --> D[Génération d'illustrations\nDesigner IA]
    D --> E[Mise en page\npublication headless CMS]
    E --> F{Contrôle qualité}
    F -->|OK| G[Publication blog]
    G --> H[Adaptation format newsletter\nCopywriter + Expert SEO]
    H --> I[Segmentation audience\nResponsable monétisation]
    I --> J[Envoi programmé]
    J --> K[Suivi taux d'ouverture/clic\nAnalyste de données]
```

## 4.5 Workflow détaillé — Podcast

```mermaid
flowchart TD
    A[Script dialogué ou monologue\nJournaliste] --> B[Génération voix multi-locuteurs\nNarrateur — ElevenLabs voix distinctes]
    B --> C[Montage audio + habillage sonore\nMonteur]
    C --> D[Génération des chapitres + résumé\nExpert SEO]
    D --> E[Extraction de clips vidéo\npour promotion croisée sur Shorts/TikTok]
    E --> F[Publication multi-plateforme\nSpotify/Apple Podcasts/YouTube Podcasts]
    F --> G[Analytics d'écoute\nAnalyste de données]
```

## 4.6 Boucle d'apprentissage (le workflow le plus stratégique)

```mermaid
flowchart LR
    A[Publication] --> B[Collecte de métriques\nvues, rétention, engagement, conversions]
    B --> C[Analyse comparative\npar sujet / format / hook / heure / canal / langue]
    C --> D{Signal significatif ?}
    D -->|Non — bruit statistique| E[Archivage, pas d'action]
    D -->|Oui| F[Mise à jour des priorités\nAnalyste des tendances]
    D -->|Oui, lié au visuel/prompt| G[Mise à jour des templates de prompts\nPrompt Engineer]
    D -->|Oui, lié au montage/rythme| H[Mise à jour des templates de montage\nMonteur]
    F --> I[Prochain cycle de production]
    G --> I
    H --> I
```

🔴 Point de vigilance méthodologique : avec un volume de contenu encore faible (phase MVP/V1), le risque de **sur-interpréter du bruit statistique comme un signal** est réel. Le workflow doit imposer un seuil minimal de données (nombre de publications comparables) avant qu'une recommandation de l'Analyste de données ne modifie automatiquement un template — sinon la boucle d'apprentissage peut dégrader la qualité au lieu de l'améliorer. Détail des seuils en `06-automatisation.md`.

## 4.7 Gestion des reprises après erreur (vue d'ensemble workflow)

Chaque étape du workflow maître (§4.1) est conçue pour être **rejouable indépendamment** :

| Type d'échec | Comportement |
|---|---|
| Échec technique d'un agent (timeout API, erreur modèle) | Retry automatique (backoff exponentiel, 3 tentatives) sans repartir du début du pipeline |
| Échec de qualité (Responsable qualité rejette) | Retour ciblé à l'agent producteur identifié, pas à tout le pipeline |
| Échec de publication (API plateforme indisponible, quota atteint) | Mise en file d'attente avec nouvelle tentative programmée, alerte si échec répété |
| Dérive détectée en boucle d'apprentissage | Pas de reprise automatique — génère une tâche de revue humaine sur le template concerné |

Détail technique complet (files d'attente, idempotence, alerting) en `06-automatisation.md`.

---
← [Agents IA](03-agents-ia.md) · Suivant → [Comparatif des outils](05-comparatif-outils.md)
