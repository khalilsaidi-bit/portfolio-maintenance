# Pronostic et PHM

> **État :** rédigé (version 1) · **Responsable :** à attribuer

Le PHM (*Prognostics and Health Management*, gestion de la santé et pronostic) regroupe les méthodes qui évaluent l'état de santé d'un système, en prévoient l'évolution et en déduisent des décisions de maintenance. Cette section distingue des tâches souvent confondues, présente le processus PHM et compare les approches de pronostic.

## 6.1 Quatre tâches à ne pas confondre

| Tâche | Question | Résultat | Données nécessaires |
|---|---|---|---|
| Détection | Le système s'écarte-t-il de son fonctionnement normal ? | Alarme oui / non, score d'anomalie | Données de fonctionnement normal (les données de défaut ne sont pas indispensables) |
| Diagnostic | Quel défaut, où, et de quelle gravité ? | Mode de défaillance, composant, sévérité | Exemples étiquetés de chaque défaut, ou modèle physique |
| Pronostic | Comment l'état va-t-il évoluer ? | Trajectoire future de la dégradation | Historiques de dégradation |
| Estimation de la RUL | Combien de temps avant la défaillance ? | Durée de vie résiduelle, avec un intervalle de confiance | Trajectoires **jusqu'à la défaillance** (*run-to-failure*), ou modèle de dégradation |

L'ISO 13381-1:2015 définit le pronostic comme l'estimation du temps avant défaillance et du risque associé, pour un ou plusieurs modes de défaillance existants ou à venir. La **RUL** (*Remaining Useful Life*) est donc la durée entre l'instant présent et la défaillance, sachant l'état actuel et les conditions d'utilisation futures.

Le choix de la tâche dépend des données disponibles. Un jeu de données sans trajectoire jusqu'à la défaillance permet la détection et le diagnostic, pas l'estimation de la RUL.

## 6.2 Le processus PHM


<figure class="fig" id="fig-phm"><svg viewBox="0 0 680 135" role="img" aria-label="Processus PHM en sept modules" xmlns="http://www.w3.org/2000/svg"><defs><marker id="ar" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path class="arh" d="M0,0 L10,5 L0,10 z"/></marker></defs><rect class="bx" x="6" y="30" width="84" height="50" rx="4"/><text class="tb" x="48" y="59" text-anchor="middle">Acquisition</text><line class="arw" x1="90" y1="55" x2="102" y2="55" marker-end="url(#ar)"/><rect class="bx" x="102" y="30" width="84" height="50" rx="4"/><text class="tb" x="144" y="59" text-anchor="middle">Traitement</text><line class="arw" x1="186" y1="55" x2="198" y2="55" marker-end="url(#ar)"/><rect class="bx acc" x="198" y="30" width="84" height="50" rx="4"/><text class="tb" x="240" y="59" text-anchor="middle">Détection</text><line class="arw" x1="282" y1="55" x2="294" y2="55" marker-end="url(#ar)"/><rect class="bx acc" x="294" y="30" width="84" height="50" rx="4"/><text class="tb" x="336" y="59" text-anchor="middle">Diagnostic</text><line class="arw" x1="378" y1="55" x2="390" y2="55" marker-end="url(#ar)"/><rect class="bx acc" x="390" y="30" width="84" height="50" rx="4"/><text class="tb" x="432" y="59" text-anchor="middle">Pronostic</text><line class="arw" x1="474" y1="55" x2="486" y2="55" marker-end="url(#ar)"/><rect class="bx" x="486" y="30" width="84" height="50" rx="4"/><text class="tb" x="528" y="51.5" text-anchor="middle">Aide à la</text><text class="tb" x="528" y="66.5" text-anchor="middle">décision</text><line class="arw" x1="570" y1="55" x2="582" y2="55" marker-end="url(#ar)"/><rect class="bx" x="582" y="30" width="84" height="50" rx="4"/><text class="tb" x="624" y="59" text-anchor="middle">IHM</text><text class="ts" x="48" y="100" text-anchor="middle">DA</text><text class="ts" x="144" y="100" text-anchor="middle">DM</text><text class="ts" x="240" y="100" text-anchor="middle">SD</text><text class="ts" x="336" y="100" text-anchor="middle">HA</text><text class="ts" x="432" y="100" text-anchor="middle">PA</text><text class="ts" x="528" y="100" text-anchor="middle">AG</text><text class="tm" x="340" y="122" text-anchor="middle">ISO 13374 / OSA-CBM : DA acquisition, DM manipulation, SD détection d'état, HA évaluation de santé, PA pronostic, AG avis</text></svg><figcaption>Figure 6.1 — Les sept modules du processus PHM présentés en cours, et leur correspondance avec les blocs de traitement de l'ISO 13374 et de l'architecture OSA-CBM. La présentation (IHM) est transverse dans l'ISO 13374.</figcaption></figure>


| Module | Rôle |
|---|---|
| Acquisition | Capteurs, cartes d'acquisition, fichiers de mesure |
| Traitement | Nettoyage, synchronisation, extraction d'indicateurs (temporels, fréquentiels, temps-fréquence) |
| Détection | Comparaison avec le comportement normal, génération d'alarmes |
| Diagnostic | Localisation et identification du défaut |
| Pronostic | Prévision de l'évolution de l'état de santé et estimation de la RUL |
| Aide à la décision | Choix de l'action et de son moment, selon le risque, le coût et les ressources disponibles |
| Interface homme-machine | Restitution des résultats aux opérateurs et à la maintenance |

Ce découpage correspond à l'architecture normalisée par l'**ISO 13374** (traitement des données de surveillance) et à son implémentation ouverte OSA-CBM portée par l'organisation MIMOSA [1].

## 6.3 Les approches de pronostic

| Approche | Principe | Exemples de méthodes | Avantages | Limites |
|---|---|---|---|---|
| Fondée sur un modèle physique | Équations du mécanisme de dégradation, recalées sur les mesures | Loi de Paris (propagation de fissure), modèles d'usure, modèles électrochimiques de batterie | Interprétable, extrapole hors des données observées | Modèle souvent inconnu ou trop coûteux pour un système complexe |
| Guidée par les données | Apprendre la dégradation à partir d'historiques | Régression, réseaux de neurones (LSTM, CNN), similarité de trajectoires, modèles de survie | Pas besoin de modèle physique, s'adapte aux systèmes complexes | Exige beaucoup d'historiques jusqu'à la défaillance ; extrapolation fragile |
| Hybride | Combiner un modèle physique et l'apprentissage | Filtre particulaire sur un modèle physique, réseau de neurones informé par la physique | Tire parti des deux mondes | Plus complexe à développer et à valider |

Le cours présente aussi des outils stochastiques et statistiques : modèles de Markov cachés, réseaux bayésiens dynamiques, filtres de Kalman et particulaire, analyse de tendance [2].

## 6.4 Indicateur de santé et RUL


<figure class="fig" id="fig-rul"><svg viewBox="0 0 640 290" role="img" aria-label="Principe de l'estimation de la RUL" xmlns="http://www.w3.org/2000/svg"><defs><marker id="ar" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path class="arh" d="M0,0 L10,5 L0,10 z"/></marker></defs><line class="gr" x1="70" x2="610" y1="240" y2="240"/><line class="gr" x1="70" x2="610" y1="140" y2="140"/><line class="gr" x1="70" x2="610" y1="40" y2="40"/><line class="ax" x1="70" y1="240" x2="610" y2="240"/><line class="ax" x1="70" y1="30" x2="70" y2="240"/><text class="tm" x="70" y="256" text-anchor="middle">0</text><text class="tm" x="205" y="256" text-anchor="middle">25</text><text class="tm" x="340" y="256" text-anchor="middle">50</text><text class="tm" x="475" y="256" text-anchor="middle">75</text><text class="tm" x="610" y="256" text-anchor="middle">100</text><text class="tm" x="64" y="244" text-anchor="end">0</text><text class="tm" x="64" y="144" text-anchor="end">0,5</text><text class="tm" x="64" y="44" text-anchor="end">1</text><text class="tm" x="610" y="274" text-anchor="end">Temps (cycles)</text><text class="tm" x="70" y="22" text-anchor="start">Indicateur de santé</text><polygon class="band" points="394,170.1 399.4,173.9 404.8,177.8 410.2,181.8 415.6,185.8 421,189.9 426.4,194.1 431.8,198.4 437.2,202.8 442.6,207.3 448,211.9 453.4,216.5 458.8,221.2 464.2,226 469.6,230.9 475,235.9 480.4,241 485.8,246.1 491.2,251.3 496.6,256.7 502,262.1 507.4,267.6 512.8,273.1 518.2,278.8 523.6,284.6 529,290.4 534.4,296.3 539.8,302.3 545.2,308.4 550.6,314.6 556,320.9 561.4,327.2 566.8,333.7 572.2,340.2 577.6,346.8 583,353.5 588.4,360.3 593.8,367.2 599.2,374.2 604.6,381.2 610,388.4 610,452.4 604.6,443.6 599.2,435 593.8,426.4 588.4,417.9 583,409.5 577.6,401.2 572.2,393 566.8,384.9 561.4,376.8 556,368.9 550.6,361 545.2,353.2 539.8,345.5 534.4,337.9 529,330.4 523.6,323 518.2,315.6 512.8,308.3 507.4,301.2 502,294.1 496.6,287.1 491.2,280.1 485.8,273.3 480.4,266.6 475,259.9 469.6,253.3 464.2,246.8 458.8,240.4 453.4,234.1 448,227.9 442.6,221.7 437.2,215.6 431.8,209.6 426.4,203.7 421,197.9 415.6,192.2 410.2,186.6 404.8,181 399.4,175.5 394,170.1"/><line class="thr" x1="70" y1="150" x2="610" y2="150"/><text class="t" x="80.8" y="144" text-anchor="start">seuil de défaillance</text><polyline class="c3" points="70,35.1 75.4,46.2 80.8,39.1 86.2,41.6 91.6,41.5 97,41.2 102.4,45.9 107.8,42 113.2,44 118.6,34.4 124,42.5 129.4,44.5 134.8,45.1 140.2,46.8 145.6,48.7 151,48 156.4,47 161.8,49.8 167.2,48.1 172.6,52.1 178,52.9 183.4,50.6 188.8,54.5 194.2,58.6 199.6,59.4 205,59.4 210.4,57.8 215.8,65 221.2,66.8 226.6,65.9 232,72.5 237.4,73.2 242.8,72.6 248.2,75.7 253.6,79.3 259,80.3 264.4,91.3 269.8,84.7 275.2,92.2 280.6,96.7 286,94.9 291.4,96.8 296.8,102.6 302.2,107.2 307.6,107.8 313,111.2 318.4,111.1 323.8,116.1 329.2,121 334.6,122.4 340,129.2 345.4,134.7 350.8,134.9 356.2,138.9 361.6,144.8 367,150.3 372.4,152 377.8,162.8 383.2,159.5 388.6,164.4 394,174"/><polyline class="c1 dashed" points="394,170.1 399.4,174.7 404.8,179.4 410.2,184.2 415.6,189 421,193.9 426.4,198.9 431.8,204 437.2,209.2 442.6,214.5 448,219.9 453.4,225.3 458.8,230.8 464.2,236.4 469.6,242.1 475,247.9 480.4,253.8 485.8,259.7 491.2,265.7 496.6,271.9 502,278.1 507.4,284.4 512.8,290.7 518.2,297.2 523.6,303.8 529,310.4 534.4,317.1 539.8,323.9 545.2,330.8 550.6,337.8 556,344.9 561.4,352 566.8,359.3 572.2,366.6 577.6,374 583,381.5 588.4,389.1 593.8,396.8 599.2,404.6 604.6,412.4 610,420.4"/><line class="dim dash" x1="394" y1="240" x2="394" y2="30"/><line class="dim" x1="394" y1="216" x2="394" y2="216" marker-start="url(#ar)" marker-end="url(#ar)"/><text class="tb" x="394" y="208" text-anchor="middle">RUL estimée</text><text class="tm" x="388" y="40" text-anchor="end">instant présent</text><text class="t" x="178" y="76" text-anchor="start">mesures</text><text class="t" x="599.2" y="108" text-anchor="end">prévision et incertitude</text></svg><figcaption>Figure 6.2 — Principe de l'estimation de la durée de vie résiduelle (RUL) : l'indicateur de santé est extrapolé jusqu'au seuil, avec une bande d'incertitude qui s'élargit avec l'horizon. Données synthétiques générées pour l'illustration.</figcaption></figure>


La démarche guidée par les données suit généralement quatre étapes [3] :

1. **Construire un indicateur de santé** (HI) qui évolue de façon monotone avec la dégradation : RMS vibratoire, combinaison d'indicateurs, sortie d'un modèle.
2. **Définir un seuil de défaillance**, par la physique, une norme ou l'historique.
3. **Modéliser l'évolution** de l'indicateur : modèle exponentiel, processus de Wiener, régression, réseau récurrent.
4. **Extrapoler jusqu'au seuil** et quantifier l'incertitude, qui s'élargit avec l'horizon de prévision.

Les scripts fournis avec le cours illustrent plusieurs de ces méthodes : extrapolation d'une tendance vibratoire (`reliability_analysis.m`), modèles de Cox et forêts aléatoires de survie (`RUL_Cox_RSF.m`, `RUL_ML_RSF.m`). La Predictive Maintenance Toolbox de MATLAB propose des modèles de similarité, de dégradation (`exponentialDegradationModel`, `linearDegradationModel`) et de survie.

## 6.5 Évaluer un pronostic

| Métrique | Définition | Intérêt |
|---|---|---|
| RMSE | √(moyenne des (RUL prédite − RUL vraie)²) | Erreur moyenne en cycles ou en heures |
| Fonction de score asymétrique | s = Σ (e^(−d/13) − 1) si d < 0 ; Σ (e^(d/10) − 1) si d ≥ 0, avec d = RUL prédite − RUL vraie | Pénalise davantage les prédictions **tardives** (d > 0), plus dangereuses ; utilisée pour le jeu C-MAPSS [4] |
| Horizon de pronostic | Temps avant la défaillance à partir duquel les prédictions restent dans une bande d'erreur acceptable | Indique le délai d'anticipation réel |
| Performance α-λ | Proportion des instants où la prédiction est dans ±α % de la RUL vraie | Juge la précision au fil du temps [5] |

Une erreur de pronostic n'a pas le même coût dans les deux sens. Prévoir trop tard conduit à la panne ; prévoir trop tôt conduit à remplacer une pièce encore bonne. Le choix de la métrique doit refléter ce coût.

## 6.6 Jeux de données de référence

| Jeu de données | Origine | Nature | Tâche permise |
|---|---|---|---|
| C-MAPSS (FD001 à FD004) | NASA, simulation de turboréacteurs [4] | Séries multivariées simulées, jusqu'à la défaillance | RUL |
| N-CMAPSS | NASA, ETH Zurich, PARC (2021) | Simulation en conditions de vol réelles | RUL |
| FEMTO / PRONOSTIA | Institut FEMTO-ST, Besançon [6] | 17 essais accélérés de roulements, vibration et température | RUL de roulements |
| IMS Bearings | Université de Cincinnati, via la NASA | Essais de roulements jusqu'à la défaillance | Détection, RUL |
| Paderborn (KAt) | Université de Paderborn [7] | Courant moteur et vibration, défauts artificiels et réels | Diagnostic |
| Électropompe centrifuge | Université de Twente, Marine néerlandaise (2024) | Courant, tension et vibration, nombreux défauts implantés | Détection, diagnostic (projet PRJ-01) |
| Batteries Li-ion | NASA PCoE | Cycles de charge et décharge, vieillissement | Pronostic de l'état de santé |

Les jeux C-MAPSS sont simulés : ils sont excellents pour comparer des algorithmes, mais un résultat obtenu sur ces données ne démontre pas la performance sur une machine réelle.

## 6.7 Applications dans l'aéronautique et l'énergie

- **Aéronautique** : surveillance des moteurs d'avion à partir de paramètres de vol, pronostic des roulements et des boîtes de transmission d'hélicoptères. C'est le secteur qui a fait naître la RCM et une grande partie des méthodes PHM.
- **Éolien** : pronostic des roulements et des multiplicateurs, où un remplacement exige une grue et une fenêtre météo. L'exemple MathWorks de pronostic d'un roulement d'éolienne à grande vitesse est fourni avec le cours.
- **Électronique de puissance** : vieillissement des IGBT, des MOSFET et des condensateurs dans les onduleurs photovoltaïques et les convertisseurs (jeux de données de vieillissement accéléré de la NASA).
- **Stockage d'énergie** : estimation de l'état de santé et de la durée de vie des batteries.

## 6.8 Limites et enjeux

- **Rareté des trajectoires jusqu'à la défaillance** sur des équipements réels : on les laisse rarement aller jusqu'à la panne.
- **Conditions d'utilisation futures inconnues** : la RUL dépend de la charge à venir.
- **Quantification de l'incertitude** : une RUL sans intervalle de confiance est peu exploitable pour décider.
- **Transfert** d'un équipement, d'un site ou d'une condition à l'autre.
- **Explicabilité** : les équipes de maintenance doivent comprendre pourquoi un modèle alerte [8].

## Références

<ol class="refs">
<li>[1] ISO, <i>ISO 13374 — Condition monitoring and diagnostics of machines — Data processing, communication and presentation</i>, parties 1 à 4. Genève : ISO.</li>
<li>[2] F. Ben Hmida, <i>Maintenance industrielle — Chap. 4 : Maintenance prédictive (partie PHM)</i>, support de cours, 2024.</li>
<li>[3] Y. Lei, N. Li, L. Guo, N. Li, T. Yan et J. Lin, « Machinery health prognostics: A systematic review from data acquisition to RUL prediction », <i>Mech. Syst. Signal Process.</i>, vol. 104, p. 799-834, 2018.</li>
<li>[4] A. Saxena, K. Goebel, D. Simon et N. Eklund, « Damage propagation modeling for aircraft engine run-to-failure simulation », dans <i>Proc. Int. Conf. Prognostics and Health Management (PHM08)</i>, Denver, CO, 2008.</li>
<li>[5] A. Saxena, J. Celaya, B. Saha, S. Saha et K. Goebel, « Metrics for offline evaluation of prognostic performance », <i>Int. J. Prognostics Health Manag.</i>, vol. 1, n° 1, 2010.</li>
<li>[6] P. Nectoux <i>et al.</i>, « PRONOSTIA: An experimental platform for bearings accelerated degradation tests », dans <i>Proc. IEEE Int. Conf. Prognostics and Health Management</i>, Denver, CO, 2012.</li>
<li>[7] C. Lessmeier, J. K. Kimotho, D. Zimmer et W. Sextro, « Condition monitoring of bearing damage in electromechanical drive systems by using motor current signals of electric motors: A benchmark data set for data-driven classification », dans <i>Proc. European Conf. PHM Society</i>, Bilbao, 2016.</li>
<li>[8] A. K. S. Jardine, D. Lin et D. Banjevic, « A review on machinery diagnostics and prognostics implementing condition-based maintenance », <i>Mech. Syst. Signal Process.</i>, vol. 20, n° 7, p. 1483-1510, 2006.</li>
<li>[9] ISO, <i>ISO 13381-1:2015 — Condition monitoring and diagnostics of machines — Prognostics — Part 1: General guidelines</i>. Genève : ISO, 2015.</li>
</ol>
