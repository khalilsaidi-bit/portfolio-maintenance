# Généralités sur la maintenance industrielle

> **État :** rédigé (version 1) · **Responsable :** à attribuer

La maintenance conditionne la disponibilité de l'outil de production, la sécurité des personnes et une part importante des coûts d'exploitation. Cette section pose le vocabulaire normalisé utilisé dans tout le portfolio, présente les grandes familles de maintenance et les indicateurs qui permettent de les piloter.

## 1.1 Définitions normalisées

La norme **NF EN 13306** (terminologie de la maintenance, version française de l'EN 13306:2017) définit la maintenance comme l'*ensemble de toutes les actions techniques, administratives et de management durant le cycle de vie d'un bien, destinées à le maintenir ou à le rétablir dans un état dans lequel il peut accomplir la fonction requise* [1].

Cette définition contient trois idées :

- **maintenir** : agir avant la défaillance (maintenance préventive) ;
- **rétablir** : agir après la défaillance (maintenance corrective) ;
- **fonction requise** : la maintenance se juge par rapport à une fonction attendue, pas par rapport à l'état « neuf » du bien.

| Terme | Définition (sens du cours et de NF EN 13306) | Exemple sur une pompe |
|---|---|---|
| Bien | Tout élément, composant, sous-système ou système que l'on peut considérer individuellement | Groupe motopompe, roulement, garniture mécanique |
| Fonction requise | Fonction ou ensemble de fonctions jugées nécessaires pour fournir un service donné | Débiter 50 m³/h sous 30 m de hauteur manométrique |
| Défaillance | **Événement** : perte de l'aptitude d'un bien à accomplir une fonction requise | Grippage du roulement |
| Panne | **État** d'un bien inapte à accomplir une fonction requise | La pompe est arrêtée après le grippage |
| Défaut | Écart d'une caractéristique par rapport à sa valeur spécifiée ; il n'empêche pas forcément la fonction | Balourd léger, fuite goutte à goutte |
| Dégradation | Évolution irréversible d'une ou plusieurs caractéristiques d'un bien | Usure progressive de l'impulseur |

La distinction **défaillance (événement) / panne (état)** est essentielle : la défaillance est un instant, la panne une durée. C'est elle qui permet de définir les temps de bon fonctionnement et d'arrêt utilisés au §1.5.

## 1.2 Historique

L'évolution de la maintenance est souvent décrite en générations successives, chacune ajoutant de nouvelles attentes sans supprimer les précédentes [2], [3].

| Période | Approche dominante | Ce qui change |
|---|---|---|
| Jusqu'aux années 1940 | Entretien et dépannage | On répare quand la machine casse. Machines simples, surdimensionnées. |
| Années 1950-1960 | Maintenance préventive systématique | Mécanisation et coût des arrêts : on remplace à intervalles fixes. Premiers plans de maintenance. |
| Années 1960-1970 | Fiabilité, aéronautique | Les études de United Airlines montrent que la plupart des défaillances ne dépendent pas de l'âge. Elles débouchent sur la RCM (Nowlan et Heap, 1978) [4]. |
| Années 1970-1980 | TPM au Japon, maintenance conditionnelle | Implication des opérateurs, mesure de l'état (analyse vibratoire, analyse d'huile). |
| Années 1980-2000 | GMAO, maintenance basée sur la fiabilité | L'informatisation de l'historique permet de calculer MTBF, MTTR et coûts par équipement. |
| Depuis les années 2010 | Maintenance 4.0, prédictive, PHM | Capteurs connectés, données massives et IA : on prévoit la défaillance et la durée de vie résiduelle (sections 3, 5 et 6). |

## 1.3 Types de maintenance


<figure class="fig" id="fig-types"><svg viewBox="0 0 680 270" role="img" aria-label="Arbre des types de maintenance" xmlns="http://www.w3.org/2000/svg"><defs><marker id="ar" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path class="arh" d="M0,0 L10,5 L0,10 z"/></marker></defs><rect class="bx strong" x="260" y="10" width="160" height="34" rx="4"/><text class="tb" x="340" y="31" text-anchor="middle">Maintenance</text><rect class="bx acc" x="90" y="80" width="180" height="34" rx="4"/><text class="tb" x="180" y="101" text-anchor="middle">Préventive</text><rect class="bx sig" x="410" y="80" width="180" height="34" rx="4"/><text class="tb" x="500" y="101" text-anchor="middle">Corrective</text><path class="ln" d="M340,44 V62 H180 V80 M340,62 H500 V80"/><rect class="bx" x="10" y="150" width="160" height="40" rx="4"/><text class="t" x="90" y="166.5" text-anchor="middle">Systématique</text><text class="t" x="90" y="181.5" text-anchor="middle">(échéancier)</text><rect class="bx" x="190" y="150" width="160" height="40" rx="4"/><text class="t" x="270" y="166.5" text-anchor="middle">Conditionnelle</text><text class="t" x="270" y="181.5" text-anchor="middle">(état mesuré)</text><rect class="bx" x="390" y="150" width="130" height="40" rx="4"/><text class="t" x="455" y="174" text-anchor="middle">Différée</text><rect class="bx" x="530" y="150" width="130" height="40" rx="4"/><text class="t" x="595" y="174" text-anchor="middle">Immédiate</text><path class="ln" d="M180,114 V132 H90 V150 M180,132 H270 V150 M500,114 V132 H455 V150 M500,132 H595 V150"/><rect class="bx acc" x="190" y="220" width="160" height="40" rx="4"/><text class="t" x="270" y="236.5" text-anchor="middle">Prévisionnelle</text><text class="t" x="270" y="251.5" text-anchor="middle">(prédictive)</text><path class="ln" d="M270,190 V220"/><rect class="bx dash" x="390" y="220" width="270" height="40" rx="4"/><text class="tm" x="525" y="236.5" text-anchor="middle">Actions : palliative (dépannage provisoire)</text><text class="tm" x="525" y="251.5" text-anchor="middle">ou curative (réparation définitive)</text><path class="ln dash" d="M455,190 V220 M595,190 V220"/></svg><figcaption>Figure 1.1 — Typologie de la maintenance selon NF EN 13306. La maintenance prévisionnelle est une forme de maintenance conditionnelle fondée sur une prévision de l'évolution de la dégradation. Les termes palliatif et curatif sont ceux du cours et de la pratique française.</figcaption></figure>


### Maintenance corrective

La maintenance corrective est *exécutée après détection d'une panne et destinée à remettre un bien dans un état dans lequel il peut accomplir une fonction requise* [1]. Elle peut être :

- **immédiate** : effectuée sans délai après la détection de la panne ;
- **différée** : retardée selon des règles données (attente de pièces, d'un arrêt de production).

Selon la nature de l'action, on distingue le **dépannage palliatif**, provisoire, qui permet de reprendre la production, et la **réparation curative**, définitive.

### Maintenance préventive

La maintenance préventive est *exécutée à des intervalles prédéterminés ou selon des critères prescrits, et destinée à réduire la probabilité de défaillance ou la dégradation du fonctionnement d'un bien* [1].

- **Systématique** (prédéterminée) : exécutée selon un échéancier en temps ou en unités d'usage (heures de marche, cycles, kilomètres), sans contrôle préalable de l'état.
- **Conditionnelle** : fondée sur la surveillance du fonctionnement du bien et des paramètres significatifs de ce fonctionnement. L'intervention est déclenchée quand un paramètre franchit un seuil.
- **Prévisionnelle** (prédictive) : maintenance conditionnelle exécutée en suivant une **prévision** extrapolée de l'analyse et de l'évaluation des paramètres significatifs de la dégradation [1]. Elle est développée dans les sections 5 et 6.

### Comparaison des stratégies

| Stratégie | Déclenchement | Avantages | Limites | Coût | Quand l'utiliser |
|---|---|---|---|---|---|
| Corrective | La panne | Aucun coût de préparation ; pièces utilisées jusqu'au bout | Arrêts imprévus, dommages secondaires, risques de sécurité | Faible à l'avance, élevé à la panne | Équipement non critique, redondé, à défaillance sans conséquence grave |
| Préventive systématique | Une échéance | Simple à planifier ; adaptée aux exigences réglementaires | Pièces remplacées trop tôt ou trop tard ; inutile si la défaillance est aléatoire | Moyen, régulier | Usure liée à l'âge (β > 1), coût de défaillance élevé, surveillance d'état impossible |
| Conditionnelle | Un seuil sur une mesure | Intervention seulement si nécessaire ; durée de vie des pièces mieux exploitée | Capteurs, instrumentation et compétences ; seuils à régler | Investissement initial, puis faible | Dégradation progressive mesurable (vibration, température, huile) |
| Prévisionnelle | Une prévision de dégradation | Planification à l'avance des arrêts et des pièces | Données d'historique nécessaires, modèles à valider, incertitude | Élevé au départ | Équipement critique, coûteux, avec un mécanisme de dégradation observable |

Aucune stratégie n'est meilleure dans l'absolu : un même atelier les combine selon la criticité de chaque équipement. C'est l'objet des méthodes de choix (AMDEC en section 2, RCM en section 4).

## 1.4 Niveaux de maintenance

La norme **NF X60-000** (2016, *Maintenance industrielle — Fonction maintenance*) classe les interventions en cinq niveaux, de la plus simple à la plus complexe [5].

| Niveau | Nature des actions | Intervenant type | Exemple |
|---|---|---|---|
| 1 | Actions simples, sans outillage spécifique, prévues dans la documentation | Opérateur | Contrôle visuel, appoint d'huile, nettoyage |
| 2 | Actions simples avec procédures et outillage courant | Technicien habilité | Remplacement d'un fusible, graissage, réglage |
| 3 | Opérations complexes, diagnostic, réparation par échange de composants | Technicien qualifié | Remplacement d'un roulement, diagnostic d'un défaut |
| 4 | Travaux importants nécessitant une maîtrise technique et des équipements spécifiques | Équipe spécialisée | Révision d'une pompe en atelier, rebobinage d'un moteur |
| 5 | Rénovation, reconstruction, travaux confiés au constructeur | Constructeur ou spécialiste | Reconstruction d'une machine, modernisation |

## 1.5 Indicateurs de fiabilité, de maintenabilité et de disponibilité


<figure class="fig" id="fig-temps"><svg viewBox="0 0 680 230" role="img" aria-label="Diagramme des temps de fonctionnement et de panne" xmlns="http://www.w3.org/2000/svg"><defs><marker id="ar" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path class="arh" d="M0,0 L10,5 L0,10 z"/></marker></defs><rect class="fa" x="40" y="70" width="160" height="34"/><rect class="fs" x="200" y="70" width="50" height="34"/><rect class="fa" x="250" y="70" width="180" height="34"/><rect class="fs" x="430" y="70" width="40" height="34"/><rect class="fa" x="470" y="70" width="170" height="34"/><line class="ax" x1="40" y1="104" x2="650" y2="104" marker-end="url(#ar)"/><text class="t" x="120" y="92" text-anchor="middle">Fonctionnement</text><text class="t" x="340" y="92" text-anchor="middle">Fonctionnement</text><text class="t" x="555" y="92" text-anchor="middle">Fonctionnement</text><text class="tm" x="225" y="62" text-anchor="middle">Panne</text><text class="tm" x="450" y="62" text-anchor="middle">Panne</text><line class="dim" x1="250" y1="140" x2="430" y2="140" marker-start="url(#ar)" marker-end="url(#ar)"/><text class="t" x="340" y="134" text-anchor="middle">UT : temps de bon fonctionnement</text><line class="dim" x1="430" y1="175" x2="470" y2="175" marker-start="url(#ar)" marker-end="url(#ar)"/><text class="t" x="450" y="169" text-anchor="middle">DT</text><line class="dim" x1="200" y1="210" x2="430" y2="210" marker-start="url(#ar)" marker-end="url(#ar)"/><text class="t" x="315" y="204" text-anchor="middle">TBF : temps entre deux défaillances</text></svg><figcaption>Figure 1.2 — Décomposition temporelle utilisée pour les indicateurs MUT, MDT, MTBF et MTTR (d'après les définitions du cours et de la norme X 60-500). Sur l'historique : MUT est la moyenne des UT, MDT la moyenne des DT (attente et logistique comprises), MTBF = MUT + MDT ; le MTTR ne compte que la réparation active.</figcaption></figure>


Sur un historique de *n* défaillances, on calcule :

```
MUT  = Σ UT / n                         temps moyen de bon fonctionnement
MDT  = Σ DT / n                         temps moyen d'indisponibilité
MTBF = MUT + MDT                        temps moyen entre défaillances
MTTR = Σ temps de réparation / n        temps moyen de réparation
λ    ≈ 1 / MUT    (taux de défaillance, si λ constant)
μ    ≈ 1 / MTTR   (taux de réparation, si μ constant)
A    = MUT / (MUT + MDT)                disponibilité opérationnelle
```

Dans la pratique, on écrit souvent **A = MTBF / (MTBF + MTTR)**, en confondant MTBF et MUT et en négligeant les temps d'attente. C'est acceptable quand les réparations sont courtes devant le temps de fonctionnement, mais il faut l'indiquer.

**Exemple (TD1, exercice 7).** Un moteur est réparé trois fois dans l'année : après 98 jours (10 h de réparation), puis 100 jours (9 h), puis 105 jours (11 h).

```
MUT = (98 + 100 + 105) / 3 = 101 jours = 2 424 h
MDT = (10 + 9 + 11) / 3 = 10 h
A   = 2 424 / (2 424 + 10) ≈ 0,9959, soit 99,6 %
```

Le moteur est disponible 99,6 % du temps. Le levier d'amélioration est la fréquence des défaillances (remplacement préventif des balais) plutôt que la durée des réparations.

### Le coût de la maintenance

Le **coût direct** comprend la main-d'œuvre, les pièces, la sous-traitance et l'outillage. Le **coût indirect** (ou coût de défaillance) comprend la production perdue, les rebuts, les pénalités et les dommages secondaires. Il est souvent bien supérieur au coût direct. Le coût global est la somme des deux.


<figure class="fig" id="fig-cout"><svg viewBox="0 0 640 290" role="img" aria-label="Courbe de coût total de maintenance" xmlns="http://www.w3.org/2000/svg"><defs><marker id="ar" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path class="arh" d="M0,0 L10,5 L0,10 z"/></marker></defs><line class="ax" x1="70" y1="240" x2="610" y2="240"/><line class="ax" x1="70" y1="30" x2="70" y2="240"/><text class="tm" x="70" y="256" text-anchor="middle">faible</text><text class="tm" x="610" y="256" text-anchor="middle">élevé</text><text class="tm" x="610" y="274" text-anchor="end">Effort de maintenance préventive →</text><text class="tm" x="70" y="22" text-anchor="start">Coût</text><polyline class="c1" points="70,225.7 79.2,225.6 88.3,225.3 97.5,224.8 106.6,224.3 115.8,223.7 124.9,222.9 134.1,222.1 143.2,221.2 152.4,220.2 161.5,219.1 170.7,218 179.8,216.8 189,215.5 198.1,214.1 207.3,212.7 216.4,211.1 225.6,209.6 234.7,207.9 243.9,206.2 253.1,204.4 262.2,202.6 271.4,200.7 280.5,198.7 289.7,196.7 298.8,194.6 308,192.5 317.1,190.3 326.3,188 335.4,185.7 344.6,183.4 353.7,180.9 362.9,178.5 372,175.9 381.2,173.3 390.3,170.7 399.5,168 408.6,165.2 417.8,162.4 426.9,159.6 436.1,156.7 445.3,153.7 454.4,150.7 463.6,147.6 472.7,144.5 481.9,141.4 491,138.2 500.2,134.9 509.3,131.6 518.5,128.2 527.6,124.8 536.8,121.4 545.9,117.9 555.1,114.3 564.2,110.7 573.4,107.1 582.5,103.4 591.7,99.7 600.8,95.9 610,92"/><polyline class="c2" points="70,53.9 79.2,63.4 88.3,72.5 97.5,81.1 106.6,89.2 115.8,96.9 124.9,104.2 134.1,111.2 143.2,117.7 152.4,123.9 161.5,129.8 170.7,135.4 179.8,140.6 189,145.6 198.1,150.4 207.3,154.8 216.4,159.1 225.6,163.1 234.7,166.9 243.9,170.5 253.1,173.9 262.2,177.2 271.4,180.2 280.5,183.1 289.7,185.9 298.8,188.5 308,191 317.1,193.3 326.3,195.5 335.4,197.6 344.6,199.6 353.7,201.5 362.9,203.3 372,204.9 381.2,206.5 390.3,208.1 399.5,209.5 408.6,210.8 417.8,212.1 426.9,213.4 436.1,214.5 445.3,215.6 454.4,216.6 463.6,217.6 472.7,218.5 481.9,219.4 491,220.3 500.2,221.1 509.3,221.8 518.5,222.5 527.6,223.2 536.8,223.8 545.9,224.4 555.1,225 564.2,225.5 573.4,226 582.5,226.5 591.7,227 600.8,227.4 610,227.8"/><polyline class="c3 thick" points="70,39.5 79.2,49 88.3,57.8 97.5,65.9 106.6,73.5 115.8,80.6 124.9,87.2 134.1,93.3 143.2,98.9 152.4,104.1 161.5,108.9 170.7,113.3 179.8,117.4 189,121.1 198.1,124.4 207.3,127.5 216.4,130.2 225.6,132.7 234.7,134.8 243.9,136.7 253.1,138.4 262.2,139.8 271.4,140.9 280.5,141.9 289.7,142.6 298.8,143.1 308,143.5 317.1,143.6 326.3,143.5 335.4,143.3 344.6,142.9 353.7,142.4 362.9,141.7 372,140.9 381.2,139.9 390.3,138.7 399.5,137.5 408.6,136.1 417.8,134.6 426.9,132.9 436.1,131.2 445.3,129.3 454.4,127.3 463.6,125.3 472.7,123.1 481.9,120.8 491,118.4 500.2,115.9 509.3,113.4 518.5,110.7 527.6,108 536.8,105.2 545.9,102.3 555.1,99.3 564.2,96.3 573.4,93.1 582.5,89.9 591.7,86.6 600.8,83.3 610,79.9"/><line class="dim dash" x1="317.1" y1="143.6" x2="317.1" y2="240"/><circle class="dot" cx="317.1" cy="143.6" r="5"/><text class="tb" x="317.1" y="131.6" text-anchor="middle">optimum économique</text><text class="t" x="599.2" y="84" text-anchor="end">coût du préventif</text><text class="t" x="91.6" y="66.5" text-anchor="start">coût des défaillances</text><text class="tb" x="529" y="95.2" text-anchor="end">coût total</text></svg><figcaption>Figure 1.3 — Schéma de principe : le coût des défaillances (pertes de production, réparations) baisse quand l'effort préventif augmente, le coût du préventif monte. Le coût total passe par un optimum. Courbes qualitatives, sans valeurs réelles.</figcaption></figure>


Les indicateurs de performance de la maintenance sont normalisés par la **NF EN 15341** (2019, amendée en 2022) [6]. On y trouve notamment des ratios de coûts de maintenance rapportés à la valeur de remplacement des équipements, la part de préventif dans les heures de maintenance et des indicateurs de disponibilité.

## 1.6 Capabilité machine

Une machine bien maintenue doit aussi produire des pièces conformes. La capabilité machine compare la dispersion du procédé à l'intervalle de tolérance IT = TS − TI :

```
Cm  = IT / (6 σ)                                capabilité intrinsèque
Cmk = min(TS − m, m − TI) / (3 σ)              capabilité tenant compte du centrage
```

où *m* est la moyenne et *σ* l'écart-type mesurés sur un échantillon de production. Le seuil d'acceptation est fixé par l'entreprise ou par son client : une valeur courante est Cm ≥ 1,33. Une baisse progressive du Cmk peut signaler une dégradation (jeu, usure d'outil, dérive thermique). C'est donc aussi un indicateur de surveillance pour la maintenance.

## 1.7 Normes et référentiels

| Référence | Titre et objet | Usage dans le portfolio |
|---|---|---|
| NF EN 13306 | Maintenance — Terminologie de la maintenance (EN 13306:2017) [1] | Vocabulaire, types de maintenance |
| NF X60-000 (2016) | Maintenance industrielle — Fonction maintenance [5] | Organisation, niveaux de maintenance |
| NF EN 15341 (2019 + A1:2022) | Maintenance — Indicateurs de performance clés [6] | Pilotage par indicateurs |
| ISO 55000:2024 | Gestion d'actifs — Vocabulaire, aperçu général et principes (2ᵉ édition) [7] | Vision « cycle de vie » des actifs |
| ISO 55001:2024 | Gestion d'actifs — Exigences pour un système de management | Certification d'un système de gestion d'actifs |
| X 60-500 | Terminologie relative à la fiabilité, la maintenabilité et la disponibilité (citée dans le cours) | Définitions MTBF, MTTR |

L'**ISO 55000** dépasse la maintenance : elle traite de la gestion des actifs physiques sur tout leur cycle de vie (acquisition, exploitation, maintenance, renouvellement), en alignant les décisions techniques sur les objectifs de l'organisation et en arbitrant entre coûts, risques et performance [7].

En Tunisie, l'organisme national de normalisation est l'INNORPI. Avant de citer une norme dans un document contractuel, il faut vérifier l'existence d'une version homologuée nationale.

## Références

<ol class="refs">
<li>[1] AFNOR, <i>NF EN 13306 — Maintenance — Terminologie de la maintenance</i>, version française de l'EN 13306:2017, La Plaine Saint-Denis : AFNOR.</li>
<li>[2] J. Moubray, <i>Reliability-Centred Maintenance</i>, 2ᵉ éd. Oxford : Butterworth-Heinemann, 1997.</li>
<li>[3] F. Ben Hmida, <i>Maintenance industrielle — Chap. 1 : Concepts de base sur la maintenance</i>, support de cours, 2024.</li>
<li>[4] F. S. Nowlan et H. F. Heap, « Reliability-Centered Maintenance », U.S. Department of Defense, rapport AD-A066579, 1978.</li>
<li>[5] AFNOR, <i>NF X60-000 — Maintenance industrielle — Fonction maintenance</i>, avril 2016.</li>
<li>[6] AFNOR, <i>NF EN 15341 — Maintenance — Indicateurs de performance clés pour la maintenance</i>, 2019, amendement A1, 2022.</li>
<li>[7] ISO, <i>ISO 55000:2024 — Asset management — Vocabulary, overview and principles</i>, 2ᵉ éd., Genève : ISO, 2024. [En ligne]. Disponible : https://www.iso.org/standard/83053.html</li>
</ol>
