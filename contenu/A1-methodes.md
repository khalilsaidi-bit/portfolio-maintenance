# Carte des méthodes

Toutes les méthodes du portfolio, classées par famille : à quoi sert chacune, ce qu'il lui faut, ce qu'elle produit, et où la trouver.

## Analyse des risques et des défaillances

| Méthode | Question traitée | Démarche | Entrées | Sorties | Où |
|---|---|---|---|---|---|
| Analyse fonctionnelle | Que doit faire le système ? | Descendante | Cahier des charges, plans | Fonctions, décomposition | [Section 2](#sdf) |
| APR | Quels dangers existent ? | Inductive | Description du système | Situations dangereuses | [Section 2](#sdf) |
| AMDEC | Quels modes de défaillance sont critiques ? | Inductive (cause → effet) | Décomposition, retour d'expérience | Criticité C = F × G × D, actions | [Section 2](#sdf), [PRJ-01](#projet-1) |
| Arbre de défaillances | Comment l'événement redouté peut-il arriver ? | Déductive (effet → causes) | Événement redouté, logique du système | Coupes minimales, probabilité | [Section 2](#sdf) |
| Ishikawa, 5 pourquoi | Quelle est la cause racine ? | Qualitative | Problème observé | Causes classées | [Section 4](#lean) |
| Pareto | Quelles causes pèsent le plus ? | Quantitative | Historique de la GMAO | Causes prioritaires | [Section 4](#lean) |

## Évaluation quantitative de la SdF

| Méthode | Question traitée | Entrées | Sorties | Où |
|---|---|---|---|---|
| Indicateurs MTBF, MTTR, disponibilité | Quelle est la performance actuelle ? | Temps de fonctionnement et d'arrêt | MUT, MDT, A | [Section 1](#maintenance) |
| Diagramme de succès (MDS) | Quelle fiabilité pour le système ? | Fiabilité des composants, architecture | R système | [Section 2](#sdf) |
| Espace des états (Markov) | Quelle disponibilité avec réparations ? | Taux λ et μ, graphe d'états | Probabilités d'états, A∞ | [Section 2](#sdf) |
| Kaplan-Meier, Nelson-Aalen | Quelle fiabilité, sans supposer de loi ? | Durées de vie, données censurées | R(t) empirique | [Section 2](#sdf) |
| Ajustement de Weibull (moindres carrés, maximum de vraisemblance) | Jeunesse, hasard ou usure ? | Durées de vie | β, η, MTTF | [Section 2](#sdf) |
| Approche bayésienne | Comment estimer avec peu de données ? | A priori et observations | Loi a posteriori | [Section 2](#sdf) |

## Choix et organisation de la maintenance

| Méthode | Question traitée | Sorties | Où |
|---|---|---|---|
| Typologie NF EN 13306 | Quel type de maintenance ? | Corrective, systématique, conditionnelle, prévisionnelle | [Section 1](#maintenance) |
| RCM | Quelle tâche pour chaque mode de défaillance ? | Plan de maintenance justifié | [Section 4](#lean) |
| TPM et 5S | Comment impliquer le terrain ? | Maintenance autonome, standards | [Section 4](#lean) |
| TRS (OEE) | Quelles pertes sur l'équipement ? | D × P × Q, six grandes pertes | [Section 4](#lean) |
| DMAIC (Lean Six Sigma) | Comment résoudre un problème chronique ? | Cause racine traitée, gain pérennisé | [Section 4](#lean) |
| GMAO | Comment organiser et tracer ? | Ordres de travail, historique, indicateurs | [Section 3](#maintenance40) |
| ISO 50001 (PDCA) | Comment améliorer la performance énergétique ? | IPÉ, situation énergétique de référence, plan d'actions | [Section 7](#iso50001) |

## Surveillance, diagnostic et pronostic

| Méthode | Tâche | Données | Sorties | Où |
|---|---|---|---|---|
| Analyse vibratoire (RMS, spectre, enveloppe) | Détection, diagnostic | Accélération, vitesse vibratoire | Sévérité (ISO 20816), défaut identifié | [Section 5](#predictive) |
| MCSA | Diagnostic | Courant moteur à haute fréquence | Raies caractéristiques | [Section 5](#predictive) |
| Thermographie, analyse d'huile, ultrasons | Détection | Température, particules, émission ultrasonore | Anomalie localisée | [Section 5](#predictive) |
| T² de Hotelling | Détection d'anomalies multivariée | Mesures de l'état normal | Score, seuil, alarmes | [PRJ-01](#projet-1) |
| Isolation Forest | Détection d'anomalies | Mesures de l'état normal | Score d'isolement | [PRJ-01](#projet-1) |
| Modèles de dégradation, similarité, réseaux récurrents | Pronostic, RUL | Historiques jusqu'à la défaillance | RUL et incertitude | [Section 6](#phm) |
| Modèles de survie (Cox, forêts aléatoires de survie) | Pronostic | Durées de vie et covariables | Fiabilité conditionnelle, RUL | [Section 6](#phm) |

Les tâches de surveillance ne sont pas interchangeables : la **détection** dit si quelque chose change, le **diagnostic** dit quoi, le **pronostic** dit quand. Chacune exige des données différentes (voir la [section 6](#phm)).
