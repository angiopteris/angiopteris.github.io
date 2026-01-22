---
layout: post
title: Récap'IA – Octobre 2025
tags: [Mistral, Open Source, Agentic, Actualités, ComfyUI]
---

Mistral annonce devstral2 montrant une stratégie payante sur l'industrialisation de l'écriture de code.
Devstral2 offre des modifications fill-in-the-middle dans un répertoire de code basé sur une instruction en language naturel. Rivalisant avec les modèles frontiers comme Sonnet4.5, pas encore Opus4.5. 
Sur OpenRouter Devstral2 a une version payante et une version gratuite mistralai/devstral-2512:free (Deprecating 27 janvier 2026)

"Devstral 2 is a state-of-the-art open-source model by Mistral AI specializing in agentic coding. It is a 123B-parameter dense transformer model supporting a 256K context window. Devstral 2 supports exploring codebases and orchestrating changes across multiple files while maintaining architecture-level context. It tracks framework dependencies, detects failures, and retries with corrections—solving challenges like bug fixing and modernizing legacy systems. The model can be fine-tuned to prioritize specific languages or optimize for large enterprise codebases. It is available under a modified MIT license."

<!--more-->

## Mistral AI Studio : Un outil pour industrialiser l’IA

**Mistral AI** a présenté *Mistral AI Studio*, une plateforme destinée aux entreprises souhaitant passer de la phase d’expérimentation à celle de la production dans leurs projets d’intelligence artificielle.

Selon l’entreprise, la plupart des équipes disposent déjà de modèles performants et de cas d’usage clairs, mais peinent à les déployer durablement. Les obstacles concernent surtout le suivi des performances, la traçabilité des versions, la collecte de retours utilisateurs et la conformité aux exigences de sécurité et de gouvernance.

**Mistral AI Studio** vise à fournir une couche d’infrastructure commune pour ces besoins.  

La plateforme s’articule autour de trois composantes principales :

- **Observability** : un ensemble d’outils pour inspecter les interactions entre modèles, mesurer la qualité des sorties et relier les résultats aux versions de prompts et de modèles.  
- **Agent Runtime** : un environnement d’exécution des agents IA, avec gestion des workflows complexes et traçabilité intégrée.  
- **AI Registry** : un registre central pour les modèles, jeux de données et agents, assurant versioning, contrôle d’accès et auditabilité.

L’objectif affiché est d’offrir aux équipes IA les mêmes garanties de fiabilité, de gouvernance et de supervision que celles habituellement attendues des systèmes logiciels critiques.  
Mistral AI positionne ainsi Studio comme un outil d’**industrialisation de l’IA**, plutôt qu’un simple environnement d’expérimentation.


## Modèles génératifs 3D

![De loin, c'est pas mal, et quand on zoom ?](/images/octobre2025-seed3D-image.png "seed3D avec textures")
![On enleve les textures](/images/october2025-seed3D-bench.png "seed3D sans textures")


C'est tout sur la 3D ?
Il semblerait que non, de nouvelles méthodes se penchent sur l'articulation des modèles 3D.
![Articulation 3D](/images/october2025-freeart3D-articulatedshapes.png "Articulation 3D")

Comparaison des performances des modèles 3D génératifs

<iframe width="560" height="315" src="https://www.youtube-nocookie.com/embed/QV8TcUg8eNA?si=0hM-U5NjPz0BWuwi&amp;start=84" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" referrerpolicy="strict-origin-when-cross-origin" allowfullscreen></iframe>

## L'information en 2025

Comment trouver l'information dans une masse de données toujours plus grande ?
Est-ce qu'utiliser des outils de recherches IA pour faire de la recherche d'information devient incontournable ?

## Anthropic est en tête avec Claude Sonnet 4.5, et un écosystème en expansion

Comment anthropic tourne son écosystème autour de Claude en force majeur de son développement.

Une politique de gestion de la données offrant une latitude plus grande sur l'utilisation des données utilisateurs dans l'entraînement des prochaines générations de modèles.

En 2023, Anthropic propose les artefacts comme une moyen de générer des fichiers (texte, html, autres) afin de faciliter l'interface entre réponses et usages des utilisateurs.
En 2024, Anthropic lance Claude Sonnet, une version de Claude optimisée pour les agents autonomes, avec des capacités de planification et d'exécution de tâches complexes.
En 2025, Anthropic va plus loin dans son outil claude, en proposant des fonctionnalités avancées pour l'intégration et la gestion des données.

Lancement de Claude Desktop, et claude CLI afin d'augmenter le nombre de scénarios d'utilisation et gagner des parts de marché. 

La tendance est claire :
- Intégration d'outils et création d'un ecosystème permettant de gérer des flux de travail complexes.
- Générer des données de meilleure qualité pour l'entraînement des modèles futurs.

Anthropic continue d'améliorer son modèle Claude, avec une version Claude Sonnet 4.5 qui reste en tête des benchmarks.

Il semblerait que la création d'un écosystème intégrant plusieurs outils soit un facteur clé de succès pour les laboratoires d'IA commerciale.
Grâce à l'hybridation thinking/non-thinking et des fonctionnalités intégré.

"AI model rankings: Claude Sonnet 4.5 (#1) claims the crown with a groundbreaking 77.2% SWE-bench score—the highest benchmark—at accessible $3/$15 pricing with a free tier. Best-in-class autonomous agent capabilities make it the most complete package." source: [https://blog.logrocket.com/ai-dev-tool-power-rankings-oct-2025/?utm_source=chatgpt.com](https://blog.logrocket.com/ai-dev-tool-power-rankings-oct-2025/?utm_source=chatgpt.com)


## plus de données, plus de filtres ?

![Quantité de données générées par les LLM](/images/october2025-epoch-data-insights-output-length.png "Quantité de données générées par les LLM") (https://epoch.ai/data-insights/output-length)

Les modèles génèrent de plus en plus de données, et les performances augmentent avec la quantité de données générées. Toutefois, comme de de nombreuses études l'ont montré, la qualité des données est essentielle, ainsi il faut sélectionner les données les plus pertinentes pour l'entraînement des modèles.

Reddit poursuit Perplexity pour "scraping à l'échelle industrielle" Reddit a intenté une importante action en justice accusant Perplexity AI et plusieurs sous-traitants de scraping de collecter systématiquement des posts/commentaires Reddit pour l'entraînement de modèles sans autorisation. Implications : Les batailles de licences de données s'intensifient. Les plateformes veulent le contrôle ; les laboratoires d'IA veulent des données d'entraînement. source : [https://www.reddit.com/r/AI_enterprise/comments/1om50xi/ai_news_october_2025_roundup/](https://www.reddit.com/r/AI_enterprise/comments/1om50xi/ai_news_october_2025_roundup/)

Les laboratoires d'IA développent des moyens de filtrer et sélectionner parmis des quantités massives de données.
Demain sera-t-il fait d'un océan d'informations ou seul les IA pourront naviguer ? affaire à suivre...


## OpenAI dévoile ChatGPT Atlas

Disponible sur MacOS (Windows prochainement), OpenAI concurrence Google Chrome avec un moteur de recherche intégré au package ChatGPT.

<iframe
  width="560"
  height="315"
  src="https://player.vimeo.com/video/1129227761?h=94755e8733"
  frameborder="0"
  allow="autoplay; fullscreen; picture-in-picture"
  allowfullscreen>
</iframe>


## Les sorties sur Ollama

**gpt-oss-safeguard** est un modèle open source conçu pour le raisonnement sur la sécurité (modération, conformité, etc.).
Disponible en plusieurs tailles :
- 20B : GPU 16 Go
- 120B : GPU H100

Atouts :

Analyse et applique vos politiques de sécurité
Raisonnement explicite et ajustable (rapide ou approfondi)
Licence Apache 2.0 libre et commerciale.

**Qwen3-VL** : modèle vision-langage avancé
Qwen3-VL est un nouveau modèle vision-langage VLM de la famille Qwen. Il combine compréhension visuelle, textuelle et raisonnement multimodal.

Tailles disponibles : de 2B à 235B paramètres (versions locales et cloud).


Agent visuel : comprend et interagit avec des interfaces (boutons, outils, tâches).
Texte: performances comparables au grand modèle Qwen3-235B.
Génération de code visuel : transforme images/vidéos en HTML, CSS, JS, etc.
Contexte long : jusqu’à 1 million de tokens (livres, longues vidéos).

Raisonnement multimodal
Reconnaissance visuelle étendue (objets, personnages, produits, etc.).
OCR multilingue (32 langues)


