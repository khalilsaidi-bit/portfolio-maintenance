# Lean Maintenance : TPM, 5S, RCM, Lean Six Sigma

> **État :** rédigé (version 1) · **Responsable :** à attribuer

La Lean Maintenance applique à la maintenance les principes du Lean : supprimer ce qui n'apporte pas de valeur, standardiser, impliquer les personnes et améliorer en continu. Elle s'appuie sur quatre démarches complémentaires : les **5S** pour l'ordre et la propreté, la **TPM** pour l'efficacité des équipements, la **RCM** pour le choix rationnel des tâches de maintenance et le **Lean Six Sigma** pour la résolution de problèmes à partir des données.

## 4.1 Les gaspillages en maintenance

Le Lean classe les gaspillages (*muda*) en sept familles. Elles se traduisent directement dans un service maintenance :

| Gaspillage | Exemple en maintenance |
|---|---|
| Attente | Technicien qui attend une pièce, une consignation, l'arrêt de la machine |
| Déplacements inutiles | Allers-retours au magasin, outillage mal rangé |
| Transport | Pièces de rechange stockées loin du lieu d'intervention |
| Stocks excessifs | Pièces dormantes, doublons dans le magasin |
| Surtraitement | Préventif trop fréquent, sur des équipements non critiques |
| Défauts | Intervention mal faite à refaire, remontage incorrect |
| Surproduction | Rapports et données saisis que personne n'exploite |

## 4.2 Les 5S

| Étape | Mot japonais | Traduction | Action concrète en atelier |
|---|---|---|---|
| 1 | Seiri | Trier | Éliminer les outils et les pièces inutiles du poste |
| 2 | Seiton | Ranger | Une place pour chaque chose ; tableaux d'outils, marquage au sol |
| 3 | Seiso | Nettoyer | Nettoyer pour inspecter : une fuite se voit sur une machine propre |
| 4 | Seiketsu | Standardiser | Formaliser les règles : photos du poste de référence, check-lists |
| 5 | Shitsuke | Respecter, faire durer | Audits réguliers, affichage des résultats |

Les 5S sont le **socle de la TPM** : on ne peut pas confier l'inspection d'une machine à un opérateur si cette machine est sale et encombrée.

## 4.3 La TPM (Total Productive Maintenance)

La TPM a été développée au Japon dans les années 1970 et formalisée par Seiichi Nakajima au sein du JIPM (Japan Institute of Plant Maintenance) [1]. Elle vise l'**efficacité globale des équipements** en impliquant tout le personnel, de la direction aux opérateurs. Son ambition se résume par « zéro panne, zéro défaut, zéro accident ».


<figure class="fig" id="fig-tpm"><svg viewBox="0 0 680 285" role="img" aria-label="Temple de la TPM à huit piliers" xmlns="http://www.w3.org/2000/svg"><defs><marker id="ar" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path class="arh" d="M0,0 L10,5 L0,10 z"/></marker></defs><path class="roof" d="M20,70 L340,10 L660,70 z"/><text class="tb" x="340" y="52" text-anchor="middle">Zéro panne · zéro défaut · zéro accident</text><rect class="bx acc" x="28" y="80" width="70" height="150" rx="4"/><text class="ts" x="63" y="151.5" text-anchor="middle">Maintenance</text><text class="ts" x="63" y="166.5" text-anchor="middle">autonome</text><rect class="bx acc" x="108" y="80" width="70" height="150" rx="4"/><text class="ts" x="143" y="151.5" text-anchor="middle">Amélioration</text><text class="ts" x="143" y="166.5" text-anchor="middle">ciblée</text><rect class="bx acc" x="188" y="80" width="70" height="150" rx="4"/><text class="ts" x="223" y="151.5" text-anchor="middle">Maintenance</text><text class="ts" x="223" y="166.5" text-anchor="middle">planifiée</text><rect class="bx acc" x="268" y="80" width="70" height="150" rx="4"/><text class="ts" x="303" y="151.5" text-anchor="middle">Maintenance</text><text class="ts" x="303" y="166.5" text-anchor="middle">de la qualité</text><rect class="bx acc" x="348" y="80" width="70" height="150" rx="4"/><text class="ts" x="383" y="159" text-anchor="middle">Formation</text><rect class="bx acc" x="428" y="80" width="70" height="150" rx="4"/><text class="ts" x="463" y="151.5" text-anchor="middle">Maîtrise de la</text><text class="ts" x="463" y="166.5" text-anchor="middle">conception</text><rect class="bx acc" x="508" y="80" width="70" height="150" rx="4"/><text class="ts" x="543" y="151.5" text-anchor="middle">TPM dans les</text><text class="ts" x="543" y="166.5" text-anchor="middle">bureaux</text><rect class="bx acc" x="588" y="80" width="70" height="150" rx="4"/><text class="ts" x="623" y="151.5" text-anchor="middle">Sécurité,</text><text class="ts" x="623" y="166.5" text-anchor="middle">environnement</text><rect class="bx strong" x="20" y="240" width="640" height="34" rx="4"/><text class="tb" x="340" y="261" text-anchor="middle">Socle : 5S et implication de tout le personnel</text></svg><figcaption>Figure 4.1 — Les huit piliers de la TPM tels que structurés par le JIPM, reposant sur les 5S.</figcaption></figure>


| Pilier | Contenu |
|---|---|
| Maintenance autonome | Les opérateurs prennent en charge le nettoyage, l'inspection, la lubrification et les petits réglages (niveaux 1 et 2) |
| Amélioration ciblée (*kaizen*) | Groupes de travail sur les pertes principales |
| Maintenance planifiée | Préventif, conditionnel et prévisionnel menés par le service maintenance |
| Maintenance de la qualité | Maîtriser les conditions machine qui garantissent zéro défaut |
| Formation | Développer les compétences techniques des opérateurs et des techniciens |
| Maîtrise de la conception | Intégrer le retour d'expérience dans les nouveaux équipements (maintenabilité) |
| TPM dans les bureaux | Appliquer la démarche aux services support (achats, magasin, méthodes) |
| Sécurité et environnement | Zéro accident, zéro pollution |

### La maintenance autonome en sept étapes

Le JIPM décrit le déploiement de la maintenance autonome en sept étapes progressives : (1) nettoyage initial, (2) suppression des sources de salissure et des zones difficiles d'accès, (3) standards provisoires de nettoyage et de lubrification, (4) inspection générale, (5) inspection autonome, (6) standardisation, (7) autogestion.

### Les six grandes pertes et le TRS

La TPM mesure l'efficacité d'un équipement par le **TRS** (taux de rendement synthétique, en anglais OEE pour *Overall Equipment Effectiveness*). Il agrège six grandes pertes en trois taux :

| Taux | Pertes associées | Calcul |
|---|---|---|
| Disponibilité D | 1. Pannes · 2. Changements de série et réglages | Temps de fonctionnement / temps requis |
| Performance P | 3. Micro-arrêts · 4. Ralentissements | (Temps de cycle théorique × pièces produites) / temps de fonctionnement |
| Qualité Q | 5. Rebuts et retouches · 6. Pertes au démarrage | Pièces bonnes / pièces produites |

```
TRS = D × P × Q
```


<figure class="fig" id="fig-trs"><svg viewBox="0 0 680 270" role="img" aria-label="Cascade des pertes du TRS" xmlns="http://www.w3.org/2000/svg"><defs><marker id="ar" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path class="arh" d="M0,0 L10,5 L0,10 z"/></marker></defs><line class="gr" x1="70" x2="630" y1="230" y2="230"/><line class="gr" x1="70" x2="630" y1="177.5" y2="177.5"/><line class="gr" x1="70" x2="630" y1="125" y2="125"/><line class="gr" x1="70" x2="630" y1="72.5" y2="72.5"/><line class="gr" x1="70" x2="630" y1="20" y2="20"/><line class="ax" x1="70" y1="230" x2="630" y2="230"/><line class="ax" x1="70" y1="20" x2="70" y2="230"/><text class="tm" x="64" y="234" text-anchor="end">0</text><text class="tm" x="64" y="181.5" text-anchor="end">25</text><text class="tm" x="64" y="129" text-anchor="end">50</text><text class="tm" x="64" y="76.5" text-anchor="end">75</text><text class="tm" x="64" y="24" text-anchor="end">100</text><text class="tm" x="70" y="12" text-anchor="start">% du temps requis</text><rect class="bar1" x="90.2" y="20" width="71.7" height="210" rx="3"/><text class="tbw" x="126" y="38" text-anchor="middle">100,0 %</text><text class="tm" x="126" y="246" text-anchor="middle">Temps requis</text><rect class="bar1" x="202.2" y="41" width="71.7" height="189" rx="3"/><rect class="loss" x="202.2" y="20" width="71.7" height="21"/><text class="ts" x="238" y="14" text-anchor="middle">− disponibilité</text><text class="tbw" x="238" y="59" text-anchor="middle">90,0 %</text><text class="tm" x="238" y="246" text-anchor="middle">Temps de fonct.</text><rect class="bar1" x="314.2" y="50.5" width="71.7" height="179.5" rx="3"/><rect class="loss" x="314.2" y="41" width="71.7" height="9.5"/><text class="ts" x="350" y="35" text-anchor="middle">− performance</text><text class="tbw" x="350" y="68.5" text-anchor="middle">85,5 %</text><text class="tm" x="350" y="246" text-anchor="middle">Temps net</text><rect class="bar3" x="426.2" y="52.2" width="71.7" height="177.8" rx="3"/><rect class="loss" x="426.2" y="50.5" width="71.7" height="1.8"/><text class="ts" x="462" y="44.5" text-anchor="middle">− qualité</text><text class="tbw" x="462" y="70.2" text-anchor="middle">84,6 %</text><text class="tm" x="462" y="246" text-anchor="middle">Temps utile = TRS</text><text class="tb" x="523.6" y="51.5" text-anchor="start">TRS = D × P × Q</text><text class="t" x="523.6" y="76.7" text-anchor="start">= 0,90 × 0,95 × 0,99</text><text class="tb" x="523.6" y="101.9" text-anchor="start">≈ 84,6 %</text></svg><figcaption>Figure 4.2 — Décomposition du TRS en cascade de pertes. Exemple chiffré fictif : disponibilité 90 %, performance 95 %, qualité 99 %.</figcaption></figure>


Dans l'exemple de la figure, chacun des trois taux semble bon pris isolément, mais le TRS n'atteint que 84,6 %. Comme c'est un produit de trois termes, une baisse modeste sur chacun suffit à faire chuter le TRS. En France, les indicateurs TRS, TRG et TRE sont définis par la norme NF E60-182.

## 4.4 La RCM (Reliability-Centred Maintenance)

La RCM, ou maintenance basée sur la fiabilité, est née dans l'aviation civile. Le rapport de Nowlan et Heap (1978) a montré que le remplacement systématique à âge fixe était inefficace pour la majorité des composants, dont la probabilité de défaillance ne dépend pas de l'âge [2].

### Les six profils de défaillance

| Profil | Forme du taux de défaillance | Part des composants (United Airlines) |
|---|---|---|
| A | Baignoire : jeunesse, puis constant, puis usure | ≈ 4 % |
| B | Constant ou légèrement croissant, puis usure marquée | ≈ 2 % |
| C | Croissance lente et régulière, sans zone d'usure nette | ≈ 5 % |
| D | Faible au départ, puis montée rapide vers un palier constant | ≈ 7 % |
| E | Constant (aléatoire) à tout âge | ≈ 14 % |
| F | Jeunesse élevée, puis constant | ≈ 68 % |

Seuls les profils A et B (environ 6 %) ont une zone d'usure franche, où un remplacement à âge fixe se justifie. Ces pourcentages portent sur des composants d'avions et ne se transposent pas tels quels à une usine. La leçon reste valable : **il faut connaître le mode de défaillance avant de choisir la tâche**.

### Les sept questions de la RCM

La norme SAE JA1011 définit les critères d'un processus RCM autour de sept questions [3] :

1. Quelles sont les fonctions de l'équipement et les performances attendues ?
2. De quelles manières peut-il ne pas remplir ses fonctions (défaillances fonctionnelles) ?
3. Quelles sont les causes de chaque défaillance fonctionnelle (modes de défaillance) ?
4. Que se passe-t-il quand chaque défaillance survient (effets) ?
5. En quoi chaque défaillance est-elle importante (conséquences) ?
6. Que peut-on faire pour prévenir ou prédire chaque défaillance (tâches proactives et périodicité) ?
7. Que faire si aucune tâche proactive adaptée n'est trouvée (actions par défaut) ?

Les questions 2 à 4 correspondent à une AMDEC (section 2). La RCM ajoute la logique de décision des questions 5 à 7.

### Les types de tâches

| Tâche | Principe | Condition d'application |
|---|---|---|
| Tâche selon l'état (conditionnelle) | Mesurer un paramètre et intervenir avant la défaillance | Dégradation détectable, intervalle P-F suffisant (section 5) |
| Restauration programmée | Remettre en état à âge fixe | Usure liée à l'âge (profils A, B), âge de défaillance prévisible |
| Remplacement programmé | Remplacer à âge fixe | Idem, quand la remise en état est impossible ou trop chère |
| Recherche de défaillance cachée | Tester périodiquement une fonction de secours | Dispositifs de sécurité qui ne fonctionnent qu'en cas de besoin |
| Fonctionnement jusqu'à la défaillance | Ne rien faire de préventif | Conséquences acceptables, coût du préventif supérieur au gain |
| Modification | Reconcevoir | Conséquence sur la sécurité sans tâche efficace |

## 4.5 Lean Six Sigma

Le Six Sigma vise à réduire la variabilité des processus à l'aide de méthodes statistiques. Associé au Lean, il fournit une démarche structurée de résolution de problèmes, le **DMAIC** :

| Phase | Objectif | Application à un problème de pannes répétitives | Outils |
|---|---|---|---|
| Define (définir) | Formuler le problème et le périmètre | « Le convoyeur 3 cumule 40 h d'arrêt par mois » (exemple) | Charte de projet, SIPOC |
| Measure (mesurer) | Mesurer la situation actuelle de façon fiable | Extraire l'historique de la GMAO ; MTBF, MTTR, TRS | Relevés, vérification du système de mesure |
| Analyze (analyser) | Trouver les causes racines | Pareto des causes, analyse des modes de défaillance | Pareto, Ishikawa, 5 pourquoi, AMDEC |
| Improve (améliorer) | Tester et déployer des solutions | Modifier le graissage, changer de fournisseur de courroies | Plan d'expériences, SMED, *poka-yoke* |
| Control (maîtriser) | Pérenniser le gain | Mettre à jour la gamme préventive, suivre les indicateurs | Cartes de contrôle, standards, audits |

## 4.6 Comparaison et intégration

| Critère | TPM | RCM | Lean Six Sigma |
|---|---|---|---|
| Point de départ | L'équipement et ses pertes | La fonction et ses modes de défaillance | Un problème mesurable |
| Acteurs clés | Opérateurs et maintenance | Groupe pluridisciplinaire d'experts | Équipe projet (ceintures vertes, noires) |
| Résultat principal | Hausse du TRS, maintenance autonome | Plan de maintenance justifié tâche par tâche | Réduction d'une cause de variabilité |
| Horizon | Démarche culturelle sur plusieurs années | Étude par système, mise à jour périodique | Projets de quelques mois |
| Limite | Lourd à déployer, demande l'adhésion de tous | Coûteux en temps d'analyse | Nécessite des données fiables |

Ces démarches se combinent. Les 5S et la TPM créent les conditions de terrain. La RCM décide **quelles** tâches réaliser sur les équipements critiques. Le Lean Six Sigma traite les problèmes chroniques qui résistent. La maintenance 4.0 (sections 3 et 5) fournit les données qui rendent la RCM et le DMAIC plus précis.

## 4.7 Exemples d'optimisation

- **Pareto des arrêts** : classer les causes d'arrêt de la GMAO par durée cumulée. En général, quelques causes concentrent l'essentiel des pertes et deviennent les sujets prioritaires d'amélioration ciblée.
- **SMED** (changement rapide d'outil) : séparer les opérations réalisables machine en marche de celles qui exigent l'arrêt, pour réduire la perte n° 2 du TRS.
- **Leçons ponctuelles (OPL)** : fiches d'une page qui transmettent un savoir-faire précis (point de graissage, contrôle d'une courroie) aux opérateurs.
- **Étiquetage des anomalies** : les opérateurs signalent les anomalies par une étiquette sur la machine ; leur traitement est suivi en réunion courte.
- **Rationalisation du préventif** : supprimer les tâches sans effet démontré, identifiées par la RCM, et réaffecter le temps libéré à la surveillance conditionnelle.

## Vidéos et ressources

Sélection de l'équipe pour approfondir cette partie. Les vidéos appartiennent à leurs auteurs et s'ouvrent sur YouTube.

<ul class="res"><li><span><a href="https://www.youtube.com/watch?v=RkLtIa4a51Y" target="_blank" rel="noopener">Les 8 piliers de la TPM</a> <span class="src">· vidéo, français</span></span></li><li><span><a href="https://www.youtube.com/watch?v=2CHdmonBjx0" target="_blank" rel="noopener">The 8 Pillars of Total Productive Maintenance (TPM)</a> <span class="src">· vidéo, anglais</span></span></li><li><span><a href="https://www.youtube.com/watch?v=HBn8_vOpTYE" target="_blank" rel="noopener">Initiation au TRS (OEE), partie 2</a> <span class="src">· vidéo, français</span></span></li><li><span><a href="https://www.youtube.com/watch?v=gKnp29p0G98" target="_blank" rel="noopener">Calculating OEE: Availability, Performance + Quality</a> <span class="src">· vidéo, anglais</span></span></li><li><span><a href="https://www.youtube.com/watch?v=Nf_DjH9RX1Y" target="_blank" rel="noopener">5S Methodology Explained</a> <span class="src">· vidéo, anglais</span></span></li><li><span><a href="https://www.youtube.com/watch?v=tNYiCOGuuNA" target="_blank" rel="noopener">The Philosophy of Reliability Centered Maintenance</a> <span class="src">· vidéo, anglais</span></span></li><li><span><a href="https://www.youtube.com/watch?v=YQ8QD9hX-f0" target="_blank" rel="noopener">Comprendre la méthodologie DMAIC</a> <span class="src">· vidéo, français</span></span></li><li><span><a href="https://www.youtube.com/watch?v=Niyn3AZAgfE" target="_blank" rel="noopener">Lean Six Sigma : 10 minutes pour comprendre toute la méthodologie</a> <span class="src">· vidéo, français</span></span></li></ul>

## Références

<ol class="refs">
<li>[1] S. Nakajima, <i>Introduction to TPM: Total Productive Maintenance</i>. Cambridge, MA : Productivity Press, 1988. <a class="reflink" href="https://scholar.google.com/scholar?q=Nakajima%20Introduction%20to%20TPM%20Total%20Productive%20Maintenance" target="_blank" rel="noopener">Google Scholar ↗</a></li>
<li>[2] F. S. Nowlan et H. F. Heap, « Reliability-Centered Maintenance », U.S. Department of Defense, rapport AD-A066579, 1978. <a class="reflink" href="https://scholar.google.com/scholar?q=Nowlan%20Heap%20Reliability-Centered%20Maintenance%201978" target="_blank" rel="noopener">Google Scholar ↗</a></li>
<li>[3] SAE International, <i>SAE JA1011 — Evaluation Criteria for Reliability-Centered Maintenance (RCM) Processes</i>, révision d’août 2009. <a class="reflink" href="https://saemobilus.sae.org/standards/ja1011_200908-evaluation-criteria-reliability-centered-maintenance-rcm-processes" target="_blank" rel="noopener">SAE ↗</a></li>
<li>[4] J. Moubray, <i>Reliability-Centred Maintenance</i>, 2ᵉ éd. Oxford : Butterworth-Heinemann, 1997. <a class="reflink" href="https://scholar.google.com/scholar?q=Moubray%20Reliability-Centred%20Maintenance" target="_blank" rel="noopener">Google Scholar ↗</a></li>
<li>[5] F. Ben Hmida, <i>Maintenance industrielle — Chap. 3 : Lean Maintenance</i>, support de cours, 2024. <span class="refnote">(document de cours, non publié en ligne)</span></li>
<li>[6] J.-F. Barbet, « Tour d'horizon des méthodes d'optimisation de maintenance », formation OMF, INSA, 2021. <span class="refnote">(document de formation, non publié en ligne)</span></li>
</ol>
