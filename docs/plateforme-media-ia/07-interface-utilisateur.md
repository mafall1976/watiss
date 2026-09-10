# 7. Interface utilisateur
*Rôle simulé : directeur produit / UX designer.*

← [Automatisation](06-automatisation.md) · Suivant → [Modèle économique](08-modele-economique.md)

---

## 7.1 Principes de conception

- **Une seule interface, plusieurs marques** : sélecteur de marque (tenant) en permanence visible, jamais besoin de se reconnecter pour changer de marque.
- **Le volume ne doit jamais devenir illisible.** À 300 contenus/jour, une liste plate est inutilisable — l'interface privilégie les vues agrégées (calendrier, files, exceptions) et ne descend au niveau du contenu individuel que sur demande explicite.
- **La file des exceptions est l'écran le plus important du produit.** Si tout fonctionne, l'utilisateur humain n'a presque rien à regarder — l'interface doit remonter en priorité ce qui a besoin d'un humain (cf. `06-automatisation.md` §6.5), pas noyer cette information dans un flux général.

## 7.2 Plan de navigation

```
┌─ YARKAT MEDIA OS ────────────────────────────────────────┐
│ [Sélecteur de marque ▾]   🔔 Alertes (3)   👤 Compte      │
├───────────────────────────────────────────────────────────┤
│ 🏠 Tableau de bord                                         │
│ 📅 Calendrier éditorial                                    │
│ 🎬 Médiathèque                                             │
│ 🚦 File des exceptions (validations en attente)            │
│ 📣 Suivi des publications                                  │
│ 📊 Analytics                                                │
│ 💰 Coûts & Revenus                                          │
│ 🤖 Performance des agents                                   │
│ ⚙️  Paramètres de marque (charte éditoriale, canaux, voix)  │
└───────────────────────────────────────────────────────────┘
```

## 7.3 Tableau de bord (écran d'accueil)

```
┌───────────────────────────────────────────────────────────────────┐
│  Marque : ATLAS FINANCE ▾               Période : 7 derniers jours │
├───────────────────────────────────────────────────────────────────┤
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐ ┌─────────────┐  │
│  │ Publiés      │ │ En file     │ │ En attente  │ │ Coût total  │  │
│  │ 42           │ │ 18          │ │ validation  │ │ 312 €       │  │
│  │ ▲ 12% sem-1  │ │             │ │ 3 ⚠️         │ │ ▼ 4% sem-1  │  │
│  └─────────────┘ └─────────────┘ └─────────────┘ └─────────────┘  │
│                                                                     │
│  🚦 Nécessite votre attention                                      │
│  ┌─────────────────────────────────────────────────────────────┐  │
│  │ ⚠️ Sujet sensible détecté — "Réforme fiscale 2026" — script  │  │
│  │    prêt, en attente de validation             [Examiner →]  │  │
│  │ ⚠️ Score qualité insuffisant — Vidéo #4821 (Shorts FR)       │  │
│  │                                                [Examiner →]  │  │
│  │ ⚠️ Budget vidéo à 85 % du plafond mensuel      [Voir coûts →]│  │
│  └─────────────────────────────────────────────────────────────┘  │
│                                                                     │
│  📈 Performance de la semaine (par canal)     🏆 Top contenu       │
│  [ graphique multi-lignes ]                   "Les 5 erreurs..."   │
│                                                12,4k vues · 8,2 % eng.│
└───────────────────────────────────────────────────────────────────┘
```

## 7.4 Calendrier éditorial

```
┌───────────────────────────────────────────────────────────────────┐
│  Calendrier éditorial — ATLAS FINANCE          [+ Nouveau sujet]  │
│  [◀ Sem 36]        Semaine du 7 au 13 septembre 2026    [Sem 38 ▶]│
├─────────┬─────────┬─────────┬─────────┬─────────┬─────────┬──────┤
│  Lun 7  │ Mar 8   │ Mer 9   │ Jeu 10  │ Ven 11  │ Sam 12  │Dim 13│
├─────────┼─────────┼─────────┼─────────┼─────────┼─────────┼──────┤
│ 🎥 YT   │ 📱 Short│ 🎥 YT   │ 📱 Short│ 📰 Blog │         │📧 NL │
│ "Inflat.│ x3      │ "Guide  │ x2      │ "Analyse│         │Hebdo │
│ -ion..."│ ✅publié│ ISR"    │ 🕓 en   │ marché" │         │🕓prêt│
│ ✅ publié│         │ 🕓 montage│ génération│ ✅publié│         │      │
├─────────┴─────────┴─────────┴─────────┴─────────┴─────────┴──────┤
│  Légende : ✅ Publié · 🕓 En production · ⚠️ Bloqué · 📝 Brouillon │
│  Filtres : [Canal ▾] [Langue ▾] [Statut ▾] [Agent responsable ▾]  │
└───────────────────────────────────────────────────────────────────┘
```

Cliquer sur un contenu ouvre une **fiche contenu** unique montrant tout le pipeline pour ce contenu (sujet → script → assets → montage → publication → performance), avec le détail de quel agent a produit quoi et à quel coût — traçabilité directement issue du format de log défini en `06-automatisation.md` §6.8.

## 7.5 Médiathèque

```
┌───────────────────────────────────────────────────────────────────┐
│  Médiathèque — ATLAS FINANCE          🔍 Rechercher   [Filtres ▾] │
├───────────────────────────────────────────────────────────────────┤
│  Onglets : [Tous] [Vidéos] [Images] [Voix] [Musique] [Réutilisables]│
│                                                                     │
│  ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐ ┌────────┐          │
│  │[thumb] │ │[thumb] │ │[thumb] │ │[thumb] │ │[thumb] │          │
│  │Vidéo    │ │Image    │ │Vidéo    │ │Voix FR  │ │Image    │          │
│  │master   │ │miniature│ │clip B-  │ │12,4 Mo  │ │illustr. │          │
│  │16:9     │ │YT       │ │roll     │ │         │ │blog     │          │
│  │FLUX•RunwaY│ │Ideogram │ │Pika     │ │11Labs   │ │FLUX     │          │
│  └────────┘ └────────┘ └────────┘ └────────┘ └────────┘          │
│                                                                     │
│  Chaque asset affiche : modèle générateur, coût, licence,          │
│  contenu(s) parent(s), langue, statut d'usage (utilisé/orphelin)   │
└───────────────────────────────────────────────────────────────────┘
```

🟡 La bibliothèque de « réutilisables » (B-roll générique, decor kits par marque) est le levier direct de baisse de coût mentionné en `04-workflows.md` §4.2 — l'interface doit rendre la réutilisation plus rapide que la régénération.

## 7.6 Suivi des publications

```
┌───────────────────────────────────────────────────────────────────┐
│  Suivi des publications                                            │
├──────────┬────────────┬──────────┬─────────┬───────────┬─────────┤
│ Contenu  │ Canal      │ Statut   │ Publié  │ Vues 24h  │ Actions │
├──────────┼────────────┼──────────┼─────────┼───────────┼─────────┤
│ "Inflat."│ YouTube    │ ✅ Publié│ 07/09   │ 3 204     │ Voir ↗  │
│ "Inflat."│ Shorts     │ ✅ Publié│ 07/09   │ 18 900    │ Voir ↗  │
│ "Inflat."│ TikTok     │ ⚠️ Échec │ —       │ —         │ Relancer│
│ "Inflat."│ LinkedIn   │ 🕓 File  │ prévu 08/09 14h        │ —       │
└──────────┴────────────┴──────────┴─────────┴───────────┴─────────┘
```

## 7.7 Analytics

- **Vue par contenu** : rétention, engagement, conversion, comparé à la moyenne de la marque.
- **Vue par format/sujet/hook** : ce qui alimente la boucle d'apprentissage (`04-workflows.md` §4.6) — présentée comme des recommandations actionnables, pas seulement des courbes (« Les vidéos avec un hook-question dans les 3 premières secondes ont +34 % de rétention sur cette marque, sur 18 contenus comparables »).
- **Vue comparative multi-marques** (réservée aux rôles Admin holding) : permet d'arbitrer l'allocation de ressources entre marques.

## 7.8 Coûts & Revenus (FinOps + monétisation)

```
┌───────────────────────────────────────────────────────────────────┐
│  Coûts & Revenus — ATLAS FINANCE              Mois en cours       │
├───────────────────────────────────────────────────────────────────┤
│  Coût par poste                    │  Revenus par levier           │
│  Génération vidéo   ████████ 61 %  │  Affiliation      ▓▓▓▓ 40 %   │
│  Génération image   ███ 14 %       │  Sponsoring       ▓▓▓ 32 %    │
│  LLM (texte)         ██ 9 %        │  Abonnements      ▓▓ 20 %     │
│  Voix off            ██ 8 %        │  Autres           ▓ 8 %       │
│  Infra/orchestration █ 5 %         │                                │
│  Autres              █ 3 %         │                                │
│                                                                      │
│  Coût moyen / contenu : 7,40 €     │  Marge nette du mois : +1 240 €│
│  Budget mensuel : 2 400 € (78 % utilisé)                            │
└───────────────────────────────────────────────────────────────────┘
```

Détail des leviers de revenus en `08-modele-economique.md`.

## 7.9 Performance des agents

```
┌───────────────────────────────────────────────────────────────────┐
│  Performance des agents — Tous canaux                              │
├──────────────────────┬──────────┬───────────┬─────────┬──────────┤
│ Agent                │ Exécutions│ Taux succès│ Coût moy│ Score qual│
├──────────────────────┼──────────┼───────────┼─────────┼──────────┤
│ Fact-checker         │ 58       │ 96 %      │ 0,12 €  │ —        │
│ Réalisateur vidéo    │ 214      │ 91 %      │ 1,38 €  │ 0,84     │
│ Monteur              │ 58       │ 98 %      │ 0,04 €  │ 0,89     │
│ Responsable qualité  │ 340      │ —         │ 0,03 €  │ (juge)   │
└──────────────────────┴──────────┴───────────┴─────────┴──────────┘
```

Cet écran permet de repérer **où concentrer l'amélioration des prompts/templates** (§04 boucle d'apprentissage) : un agent à faible taux de succès ou coût anormalement élevé est le prochain candidat à optimiser.

## 7.10 Paramètres de marque (configuration de la charte éditoriale)

Formulaire structuré alimentant directement le JSON de charte éditoriale consommé par les agents (schéma détaillé en `10-documentation-technique.md`) :

- Identité : nom, univers visuel, palette, voix de marque (référence audio ElevenLabs).
- Ligne éditoriale : sujets prioritaires, sujets interdits, sujets « sensibles » nécessitant validation humaine.
- Canaux actifs et comptes connectés (OAuth par plateforme).
- Langues actives.
- Budgets (plafonds par poste, par jour/mois).
- Seuils de qualité (score minimal avant blocage automatique).
- Partenariats de monétisation actifs.

## 7.11 Rôles et vues associées (RBAC — détail technique en `10-documentation-technique.md`)

| Rôle | Accès |
|---|---|
| Admin holding | Toutes les marques, vue comparative, paramètres globaux, facturation |
| Directeur de marque | Sa marque uniquement, tous les écrans, validation des exceptions |
| Éditeur | Calendrier, médiathèque, pas d'accès aux coûts/paramètres de facturation |
| Analyste | Analytics et performance des agents en lecture seule |
| Lecture seule (ex. : membre du conseil de la holding) | Tableau de bord et analytics uniquement |

---
← [Automatisation](06-automatisation.md) · Suivant → [Modèle économique](08-modele-economique.md)
