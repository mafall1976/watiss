# 11. Améliorations futures
*Rôle simulé : R&D.*

← [Documentation technique](10-documentation-technique.md) · [Retour au sommaire](README.md)

---

Fonctionnalités volontairement **hors périmètre** du plan de développement (`09-plan-developpement.md`) mais à garder en radar, classées par horizon. Aucune n'est un engagement — ce sont des pistes à réévaluer à chaque revue trimestrielle (`09-plan-developpement.md` §9.6) à la lumière de la maturité réelle atteinte.

## 11.1 Moyen terme (après la Version Entreprise, si la traction le justifie)

- **Personnages IA récurrents par marque** (avatar visuel/vocal cohérent d'un contenu à l'autre) pour renforcer la reconnaissance de marque au-delà du style visuel/voix déjà prévu.
- **Doublage vidéo automatisé** (synchronisation labiale multilingue) pour republier un contenu vidéo existant dans une nouvelle langue sans repasser par tout le pipeline de production.
- **Personnalisation d'audience** : variantes de titre/miniature testées en A/B automatique par l'Expert SEO/Analyste de données, au-delà de l'apprentissage global déjà prévu en `04-workflows.md` §4.6.
- **Studio de collaboration humaine enrichi** : édition fine post-génération directement dans le dashboard (retouche de script, régénération ciblée d'un seul plan) plutôt que rejet/régénération complète.
- **Extension à de nouveaux formats** : contenus interactifs (quiz, sondages natifs), livestreams assistés par IA (préparation de plan de live, réponses suggérées en temps réel).
- **Marketplace de templates de prompts** entre les différentes marques du portefeuille (accélère le lancement d'une nouvelle marque en réutilisant les meilleurs templates validés ailleurs).

## 11.2 Long terme (dépend fortement de l'évolution du marché et de la réglementation)

- **Ouverture de la Couche 2 en SaaS B2B** (licence de YARKAT MEDIA OS à d'autres éditeurs) — déjà identifiée comme option stratégique en `01-vision-strategique.md` §1.3 et `08-modele-economique.md` §8.1, à activer seulement si le socle technique est stable et documenté sans dépendance à des personnes clés (critère §09 §9.4).
- **Produit data/API** (levier 10, `08-modele-economique.md`) : exposer en marque blanche les insights de tendances agrégés à travers le portefeuille de marques, à condition que le volume de données soit suffisant pour être statistiquement significatif.
- **Extension linguistique au-delà de FR/EN/ES/AR**, pilotée par les signaux de l'Analyste des tendances plutôt que par anticipation.
- **Certification/label de transparence IA propre à la plateforme**, anticipant un renforcement réglementaire probable (AI Act et équivalents) plutôt que de le subir — la traçabilité posée dès `06-automatisation.md` §6.8 et `10-documentation-technique.md` §10.7 est la fondation technique de cette option.
- **Agent de veille concurrentielle dédié** : un 16ᵉ agent qui analyserait en continu la stratégie de contenu des concurrents directs de chaque marque (formats, sujets, fréquence) — non retenu dans les 15 agents initiaux (`03-agents-ia.md`) pour ne pas complexifier le MVP, mais pertinent une fois le portefeuille établi.
- **Gouvernance éditoriale assistée par comité** : à mesure que le nombre de marques croît, un mécanisme d'arbitrage inter-marques (allocation de budget, priorisation de sujets transverses à la holding) pourrait dépasser la capacité d'un Directeur éditorial par marque et nécessiter une couche de coordination supplémentaire.

## 11.3 Pistes explicitement écartées pour l'instant (et pourquoi)

| Piste | Raison de la mise à l'écart |
|---|---|
| Publication 100 % automatique sans aucun garde-fou humain, même sur les sujets sensibles | Risque réputationnel jugé structurellement trop élevé (`01-vision-strategique.md` §1.5) — ce n'est pas une limitation technique temporaire, c'est un choix de gouvernance durable |
| Génération de voix/visages de personnes réelles sans consentement explicite | Risque juridique et éthique majeur (droit à l'image, deepfake) — hors du cadre de ce projet quelle que soit la maturité technique atteinte |
| Dépendance à un unique fournisseur de modèle génératif | Contredit le principe d'architecture découplée (`02-architecture-systeme.md` §2.1) — la diversification des fournisseurs reste un principe permanent, pas une étape transitoire |

---
← [Documentation technique](10-documentation-technique.md) · [Retour au sommaire](README.md)
