# Maintenance 4.0 et GMAO 4.0

> **État :** rédigé (version 1) · **Responsable :** à attribuer

La maintenance 4.0 applique à la maintenance les technologies de l'Industrie 4.0 : capteurs connectés, traitement de grands volumes de données, intelligence artificielle et outils numériques d'intervention. Son objectif est de passer d'une maintenance qui réagit ou qui suit un calendrier à une maintenance qui **anticipe** à partir de l'état réel des équipements.

## 3.1 Contexte : l'Industrie 4.0

Le terme « Industrie 4.0 » vient du programme allemand de recommandations publié par l'acatech en 2013 [1]. Il désigne une production organisée autour de **systèmes cyber-physiques** (CPS) : des équipements physiques couplés à leur représentation numérique, qui communiquent entre eux et avec les systèmes de gestion.

Lee, Bagheri et Kao proposent une architecture des CPS en cinq niveaux, dite « 5C » [2] :

| Niveau | Rôle | Application en maintenance |
|---|---|---|
| Connexion | Acquérir des données fiables depuis les machines | Capteurs de vibration, de température, de courant ; automates |
| Conversion | Transformer les données en information | Indicateurs d'état, détection de dérive |
| Cyber | Comparer les machines entre elles et à leur historique | Parc de machines, jumeau numérique |
| Cognition | Diagnostiquer, prévoir, aider à décider | Pronostic de la durée de vie résiduelle, priorisation |
| Configuration | Agir en retour sur le système | Ajustement des consignes, replanification de la production |

## 3.2 Les briques technologiques

| Technologie | Définition | Apport à la maintenance | Point de vigilance |
|---|---|---|---|
| IoT industriel (IIoT) | Capteurs et équipements connectés en réseau | Mesure continue de l'état, sans ronde | Alimentation, robustesse, coût par point de mesure |
| Edge computing | Traitement au plus près de la machine | Calcul des indicateurs vibratoires sur place, faible latence | Puissance limitée, mise à jour du logiciel embarqué |
| Cloud et plateformes de données | Stockage et calcul centralisés | Historique long, comparaison entre sites | Dépendance au réseau, souveraineté des données |
| Big Data | Données en grands volumes, variées, produites rapidement | Corrélation entre process, état machine et qualité | Données hétérogènes, qualité et étiquetage |
| Intelligence artificielle | Apprentissage automatique sur les données | Détection d'anomalies, diagnostic, pronostic | Données de défaillance rares, explicabilité, fausses alarmes |
| Jumeau numérique | Modèle numérique synchronisé avec l'équipement réel | Tester des scénarios, estimer l'état non mesurable | Coût de modélisation, recalage [3] |
| Réalité augmentée | Superposition d'informations au monde réel | Guidage de l'intervention, assistance à distance | Ergonomie, acceptation par les techniciens |
| Mobilité | Tablettes et smartphones connectés à la GMAO | Saisie des comptes rendus sur le terrain | Couverture réseau dans l'usine |


<figure class="fig" id="fig-archi"><svg viewBox="0 0 680 190" role="img" aria-label="Architecture d'une chaîne de maintenance 4.0" xmlns="http://www.w3.org/2000/svg"><defs><marker id="ar" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path class="arh" d="M0,0 L10,5 L0,10 z"/></marker></defs><rect class="bx" x="10" y="40" width="96" height="56" rx="4"/><text class="tb" x="58" y="64.5" text-anchor="middle">Capteurs</text><text class="tb" x="58" y="79.5" text-anchor="middle">IIoT</text><text class="ts" x="58" y="114" text-anchor="middle">vibration, T°, courant</text><line class="arw" x1="106" y1="68" x2="122" y2="68" marker-end="url(#ar)"/><rect class="bx" x="122" y="40" width="96" height="56" rx="4"/><text class="tb" x="170" y="64.5" text-anchor="middle">Passerelle</text><text class="tb" x="170" y="79.5" text-anchor="middle">edge</text><text class="ts" x="170" y="114" text-anchor="middle">filtrage, indicateurs</text><line class="arw" x1="218" y1="68" x2="234" y2="68" marker-end="url(#ar)"/><rect class="bx" x="234" y="40" width="96" height="56" rx="4"/><text class="tb" x="282" y="64.5" text-anchor="middle">Plateforme</text><text class="tb" x="282" y="79.5" text-anchor="middle">de données</text><text class="ts" x="282" y="114" text-anchor="middle">historique, cloud</text><line class="arw" x1="330" y1="68" x2="346" y2="68" marker-end="url(#ar)"/><rect class="bx acc" x="346" y="40" width="96" height="56" rx="4"/><text class="tb" x="394" y="64.5" text-anchor="middle">Analyse</text><text class="tb" x="394" y="79.5" text-anchor="middle">IA, jumeau</text><text class="ts" x="394" y="114" text-anchor="middle">diagnostic, pronostic</text><line class="arw" x1="442" y1="68" x2="458" y2="68" marker-end="url(#ar)"/><rect class="bx acc" x="458" y="40" width="96" height="56" rx="4"/><text class="tb" x="506" y="64.5" text-anchor="middle">GMAO 4.0</text><text class="tb" x="506" y="79.5" text-anchor="middle">OT, stocks</text><text class="ts" x="506" y="114" text-anchor="middle">planification</text><line class="arw" x1="554" y1="68" x2="570" y2="68" marker-end="url(#ar)"/><rect class="bx" x="570" y="40" width="96" height="56" rx="4"/><text class="tb" x="618" y="64.5" text-anchor="middle">Intervention</text><text class="tb" x="618" y="79.5" text-anchor="middle">terrain</text><text class="ts" x="618" y="114" text-anchor="middle">mobile, réalité augm.</text><path class="arw dash" d="M634,124 V160 H58 V100" marker-end="url(#ar)"/><text class="tm" x="346" y="178" text-anchor="middle">retour d'expérience : comptes rendus d'intervention, causes de défaillance, mise à jour des modèles</text></svg><figcaption>Figure 3.1 — Chaîne de valeur de la maintenance 4.0, du capteur à l'intervention. La boucle de retour d'expérience alimente les modèles et l'historique de la GMAO.</figcaption></figure>


## 3.3 La GMAO

La **GMAO** (gestion de la maintenance assistée par ordinateur) est le logiciel qui organise l'activité de maintenance. Ses fonctions de base sont :

- **Gestion du patrimoine** : arborescence des équipements (site, ligne, machine, sous-ensemble, composant), fiches techniques, documentation.
- **Gestion des interventions** : demandes d'intervention, ordres de travail (OT), comptes rendus, historique des pannes.
- **Maintenance préventive** : gammes, échéanciers, déclenchement automatique des OT.
- **Pièces de rechange et achats** : stocks, seuils de réapprovisionnement, fournisseurs.
- **Ressources** : planning des techniciens, habilitations, sous-traitance.
- **Coûts et indicateurs** : coût par équipement, MTBF, MTTR, disponibilité, taux de préventif.

### De la GMAO à la GMAO 4.0

| Aspect | GMAO traditionnelle | GMAO 4.0 |
|---|---|---|
| Saisie des données | Manuelle, souvent après l'intervention | Automatique depuis les capteurs et les automates ; saisie mobile sur le terrain |
| Déclenchement du préventif | Calendrier ou compteur | État mesuré et prévision de dégradation |
| Analyse | Rapports périodiques sur l'historique | Tableaux de bord en temps réel, alertes, modèles prédictifs |
| Intégration | Isolée ou liée à l'ERP | Connectée à l'ERP, au MES, aux plateformes IoT |
| Accès | Poste fixe | Web, mobile, réalité augmentée |
| Rôle | Enregistrer et planifier | Aider à décider |

Les supports du cours présentent plusieurs GMAO du marché francophone (Optimaint, DIMO Maint, Diamaint 4.0, Actumaint, Managemaint) et un tableau comparatif. La feuille de route cite aussi SAP (module de gestion de la maintenance de son ERP), Fiix et UpKeep, deux GMAO en mode SaaS. Le choix d'une GMAO se fait sur le périmètre fonctionnel, l'intégration au système d'information existant, la facilité d'usage pour les techniciens, le coût total et l'accompagnement de l'éditeur.

### Les indicateurs pilotés par la GMAO

| Indicateur | Calcul | Ce qu'il révèle |
|---|---|---|
| Disponibilité | MUT / (MUT + MDT) | Aptitude du parc à produire |
| MTBF par équipement | Temps de fonctionnement / nombre de défaillances | Équipements les moins fiables (Pareto) |
| MTTR | Temps de réparation / nombre d'interventions | Efficacité des interventions, logistique |
| Taux de préventif | Heures de préventif / heures totales de maintenance | Maturité de la politique de maintenance |
| Respect du planning | OT préventifs réalisés à temps / OT planifiés | Capacité de l'équipe à tenir le plan |
| Coût de maintenance | Coût annuel / valeur de remplacement du parc | Effort économique, à comparer dans le temps |

Ces indicateurs sont normalisés par la NF EN 15341 (voir section 1).

## 3.4 Étude de cas : l'usine Schneider Electric du Vaudreuil

Le site Schneider Electric du Vaudreuil (Normandie) a été transformé en vitrine de l'industrie du futur à partir de 2017, avec les offres EcoStruxure du groupe [4]. Les faits suivants sont ceux annoncés par l'entreprise :

| Élément | Information publiée |
|---|---|
| Technologies déployées | Maintenance prédictive IIoT (EcoStruxure Asset Advisor) ; réalité augmentée pour les opérateurs de maintenance (EcoStruxure Augmented Operator Advisor) ; tableau de bord de la consommation d'énergie rapportée au niveau de production |
| Résultat annoncé pour la maintenance | Gain de productivité de 2 à 7 % grâce à l'outil de réalité augmentée, selon le responsable du site |
| Retour sur investissement | Attendu en moins de deux ans pour la plupart des technologies (prévision, pas mesure) |
| Accompagnement | Plus de 800 heures de formation en 2017 |
| Reconnaissance | « Advanced Lighthouse » du Forum économique mondial en 2018, puis « Sustainability Lighthouse » en 2022 [5] |

Pour la reconnaissance de 2022, Schneider Electric annonce sur ce site une baisse de 25 % de la consommation d'énergie et des émissions de CO₂, et de 64 % de la consommation d'eau [5]. Ces chiffres proviennent de l'entreprise elle-même et n'ont pas été vérifiés de manière indépendante.

**Enseignements.** La technologie ne suffit pas : le projet associe des capteurs, une plateforme de données, des outils pour le terrain et un effort de formation important. Les gains annoncés pour la maintenance sont modestes et précis (2 à 7 %), plus crédibles que des promesses générales.

## 3.5 Bénéfices et limites

Des études de cabinets de conseil annoncent des gains importants de la maintenance prédictive. McKinsey (2017) estime qu'elle réduit les arrêts machine de 30 à 50 % et allonge la durée de vie des machines de 20 à 40 % [6]. Ces ordres de grandeur concernent des programmes matures et ne garantissent pas un résultat sur un site donné.

Les principaux freins sont les suivants :

- **Qualité des données** : historique de GMAO incomplet, causes de panne mal renseignées, capteurs mal installés.
- **Rareté des défaillances** : un équipement critique bien entretenu tombe rarement en panne, ce qui limite les exemples pour l'apprentissage.
- **Fausses alarmes** : trop d'alertes injustifiées font perdre confiance aux équipes et annulent les gains.
- **Cybersécurité** : connecter les machines expose le réseau industriel.
- **Interopérabilité** : protocoles et formats différents entre les machines, les automates et les logiciels.
- **Compétences** : il faut faire travailler ensemble la maintenance, l'informatique industrielle et la science des données.

## Vidéos et ressources

Sélection de l'équipe pour approfondir cette partie. Les vidéos appartiennent à leurs auteurs et s'ouvrent sur YouTube.

<ul class="res"><li><span><a href="https://www.youtube.com/watch?v=re6GWQRHU-g" target="_blank" rel="noopener">Qu'est-ce qu'une GMAO ? (La minute métier #3)</a> <span class="src">· vidéo, français</span></span></li><li><span><a href="https://www.youtube.com/watch?v=WhKFKDIjZP0" target="_blank" rel="noopener">C'est quoi la GMAO ? Définition, avantages et fonctionnalités</a> <span class="src">· vidéo, français</span></span></li><li><span><a href="https://www.youtube.com/watch?v=Ggeuc2m83uE" target="_blank" rel="noopener">Digital Twin for Predictive Maintenance</a> <span class="src">· vidéo, anglais</span></span></li><li><span><a href="https://www.youtube.com/watch?v=LDBE1P3pxMs" target="_blank" rel="noopener">Digital Twins and the Future of Industry 4.0</a> <span class="src">· vidéo, anglais</span></span></li><li class="doc"><span><a href="https://en.acatech.de/publication/recommendations-for-implementing-the-strategic-initiative-industrie-4-0-final-report-of-the-industrie-4-0-working-group/" target="_blank" rel="noopener">Rapport fondateur « Industrie 4.0 » (acatech, 2013)</a> <span class="src">· acatech</span></span></li><li class="doc"><span><a href="https://fr.wikipedia.org/wiki/Internet_industriel_des_objets" target="_blank" rel="noopener">Internet industriel des objets</a> <span class="src">· Wikipédia</span></span></li></ul>

## Références

<ol class="refs">
<li>[1] H. Kagermann, W. Wahlster et J. Helbig, <i>Recommendations for implementing the strategic initiative INDUSTRIE 4.0</i>, rapport final du groupe de travail Industrie 4.0. Francfort : acatech, avril 2013. <a class="reflink" href="https://en.acatech.de/publication/recommendations-for-implementing-the-strategic-initiative-industrie-4-0-final-report-of-the-industrie-4-0-working-group/" target="_blank" rel="noopener">acatech ↗</a></li>
<li>[2] J. Lee, B. Bagheri et H.-A. Kao, « A Cyber-Physical Systems architecture for Industry 4.0-based manufacturing systems », <i>Manufacturing Letters</i>, vol. 3, p. 18-23, 2015. <a class="reflink" href="https://doi.org/10.1016/j.mfglet.2014.12.001" target="_blank" rel="noopener">DOI ↗</a></li>
<li>[3] F. Tao, H. Zhang, A. Liu et A. Y. C. Nee, « Digital Twin in Industry: State-of-the-Art », <i>IEEE Trans. Ind. Informat.</i>, vol. 15, n° 4, p. 2405-2415, 2019. <a class="reflink" href="https://doi.org/10.1109/TII.2018.2873186" target="_blank" rel="noopener">DOI ↗</a></li>
<li>[4] Schneider Electric, « Schneider Electric transforme son site du Vaudreuil en vitrine de l'Industrie du Futur grâce à ses offres EcoStruxure for Industry », communiqué de presse, 3 avr. 2018. <a class="reflink" href="https://www.se.com/ww/fr/about-us/newsroom/news/press-releases/Schneider-Electric-transforme-son-site-du-Vaudreuil-en-Vitrine-de-l%E2%80%99Industrie-du-Futur-gr%C3%A2ce-%C3%A0-ses-offres-EcoStruxure-for-Industry-5ac34a942d40ce13495f6e07" target="_blank" rel="noopener">Schneider Electric ↗</a></li>
<li>[5] Schneider Electric, « New recognition for Schneider Electric from World Economic Forum », communiqué de presse, mars 2022. <a class="reflink" href="https://www.se.com/ww/en/about-us/newsroom/news/press-releases/new-recognition-for-schneider-electric-from-world-economic-forum-62441e75d32cd17e7b1f0ab4" target="_blank" rel="noopener">Schneider Electric ↗</a></li>
<li>[6] McKinsey &amp; Company, « Manufacturing: Analytics unleashes productivity and profitability », 2017. <a class="reflink" href="https://www.google.com/search?q=McKinsey%20Manufacturing%3A%20Analytics%20unleashes%20productivity%20and%20profitability%202017" target="_blank" rel="noopener">Rechercher ↗</a></li>
<li>[7] F. Ben Hmida, <i>Maintenance industrielle — Chap. 2 : Maintenance 4.0</i>, support de cours, 2024. <span class="refnote">(document de cours, non publié en ligne)</span></li>
</ol>
