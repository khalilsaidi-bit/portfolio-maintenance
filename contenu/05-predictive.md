# Maintenance prédictive

> **État :** rédigé (version 1) · **Responsable :** à attribuer

La maintenance prédictive (ou prévisionnelle) surveille l'état réel d'un équipement pour intervenir **au bon moment** : assez tôt pour éviter la défaillance, assez tard pour exploiter la durée de vie des composants. Elle repose sur une chaîne complète : capteurs, acquisition, traitement du signal, indicateurs d'état, décision.

## 5.1 Conditionnelle, prévisionnelle, prédictive

| Approche | Décision | Exemple |
|---|---|---|
| Conditionnelle | On intervient quand une mesure franchit un **seuil** | Vitesse vibratoire au-delà de la limite de la zone C |
| Prévisionnelle (prédictive) | On intervient selon une **prévision** de l'évolution de la dégradation | La tendance de l'indicateur atteindra le seuil dans environ trois semaines : on planifie l'arrêt |

Au sens de NF EN 13306, la maintenance prévisionnelle est une maintenance conditionnelle fondée sur une prévision. Dans les deux cas, le préalable est le même : la défaillance doit être **précédée d'une dégradation mesurable**.

## 5.2 La courbe P-F


<figure class="fig" id="fig-pf"><svg viewBox="0 0 640 300" role="img" aria-label="Courbe P-F" xmlns="http://www.w3.org/2000/svg"><defs><marker id="ar" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path class="arh" d="M0,0 L10,5 L0,10 z"/></marker></defs><line class="ax" x1="70" y1="240" x2="610" y2="240"/><line class="ax" x1="70" y1="30" x2="70" y2="240"/><text class="tm" x="610" y="274" text-anchor="end">Temps →</text><text class="tm" x="70" y="22" text-anchor="start">État de l'équipement</text><polyline class="c1 thick" points="70,40.1 72.7,40.1 75.4,40.1 78.1,40.1 80.9,40.1 83.6,40.1 86.3,40.1 89,40.1 91.7,40.1 94.4,40.1 97.1,40.1 99.8,40.1 102.6,40.1 105.3,40.1 108,40.1 110.7,40.2 113.4,40.2 116.1,40.2 118.8,40.2 121.6,40.2 124.3,40.2 127,40.2 129.7,40.2 132.4,40.2 135.1,40.3 137.8,40.3 140.6,40.3 143.3,40.3 146,40.3 148.7,40.3 151.4,40.4 154.1,40.4 156.8,40.4 159.5,40.4 162.3,40.5 165,40.5 167.7,40.5 170.4,40.5 173.1,40.6 175.8,40.6 178.5,40.6 181.3,40.7 184,40.7 186.7,40.7 189.4,40.8 192.1,40.8 194.8,40.9 197.5,40.9 200.3,41 203,41 205.7,41.1 208.4,41.2 211.1,41.2 213.8,41.3 216.5,41.4 219.2,41.4 222,41.5 224.7,41.6 227.4,41.7 230.1,41.8 232.8,41.9 235.5,42 238.2,42.1 241,42.2 243.7,42.3 246.4,42.5 249.1,42.6 251.8,42.8 254.5,42.9 257.2,43.1 259.9,43.3 262.7,43.4 265.4,43.6 268.1,43.8 270.8,44 273.5,44.3 276.2,44.5 278.9,44.7 281.7,45 284.4,45.3 287.1,45.6 289.8,45.9 292.5,46.2 295.2,46.6 297.9,46.9 300.7,47.3 303.4,47.7 306.1,48.1 308.8,48.5 311.5,49 314.2,49.5 316.9,50 319.6,50.5 322.4,51.1 325.1,51.7 327.8,52.3 330.5,53 333.2,53.7 335.9,54.4 338.6,55.1 341.4,55.9 344.1,56.7 346.8,57.6 349.5,58.5 352.2,59.4 354.9,60.4 357.6,61.5 360.4,62.5 363.1,63.7 365.8,64.8 368.5,66 371.2,67.3 373.9,68.6 376.6,70 379.3,71.4 382.1,72.9 384.8,74.4 387.5,76 390.2,77.7 392.9,79.4 395.6,81.1 398.3,82.9 401.1,84.8 403.8,86.7 406.5,88.7 409.2,90.7 411.9,92.8 414.6,94.9 417.3,97.1 420.1,99.3 422.8,101.6 425.5,103.9 428.2,106.3 430.9,108.7 433.6,111.2 436.3,113.6 439,116.1 441.8,118.7 444.5,121.2 447.2,123.8 449.9,126.4 452.6,129 455.3,131.6 458,134.3 460.8,136.9 463.5,139.5 466.2,142.1 468.9,144.7 471.6,147.3 474.3,149.9 477,152.4 479.7,155 482.5,157.5 485.2,159.9 487.9,162.4 490.6,164.7 493.3,167.1 496,169.4 498.7,171.6 501.5,173.9 504.2,176 506.9,178.1 509.6,180.2 512.3,182.2 515,184.1 517.7,186 520.5,187.9 523.2,189.7 525.9,191.4 528.6,193.1 531.3,194.7 534,196.2 536.7,197.8 539.4,199.2 542.2,200.6 544.9,202 547.6,203.2 550.3,204.5 553,205.7 555.7,206.8 558.4,207.9 561.2,209 563.9,210 566.6,211 569.3,211.9 572,212.8 574.7,213.6 577.4,214.4 580.2,215.2 582.9,215.9 585.6,216.6 588.3,217.3 591,218 593.7,218.6 596.4,219.1 599.1,219.7 601.9,220.2 604.6,220.7 607.3,221.2 610,221.7"/><circle class="dotP" cx="318.4" cy="50.3" r="6"/><circle class="dotF" cx="556" cy="206.9" r="6"/><text class="tb" x="328.4" y="40.3" text-anchor="start">P : la dégradation devient détectable</text><text class="tb" x="546" y="228.9" text-anchor="end">F : défaillance fonctionnelle</text><circle class="dot2" cx="372.4" cy="67.9" r="4"/><text class="ts" x="364.4" y="71.9" text-anchor="end">vibration, ultrasons</text><circle class="dot2" cx="415.6" cy="95.7" r="4"/><text class="ts" x="407.6" y="99.7" text-anchor="end">analyse d'huile</text><circle class="dot2" cx="453.4" cy="129.8" r="4"/><text class="ts" x="445.4" y="133.8" text-anchor="end">thermographie</text><circle class="dot2" cx="496.6" cy="169.9" r="4"/><text class="ts" x="488.6" y="173.9" text-anchor="end">bruit audible</text><circle class="dot2" cx="529" cy="193.3" r="4"/><text class="ts" x="521" y="197.3" text-anchor="end">échauffement au toucher</text><line class="dim" x1="318.4" y1="262" x2="556" y2="262" marker-start="url(#ar)" marker-end="url(#ar)"/><text class="t" x="437.2" y="278" text-anchor="middle">intervalle P-F : temps disponible pour planifier l'intervention</text></svg><figcaption>Figure 5.1 — Courbe P-F, schéma de principe d'après Moubray. L'ordre des techniques est indicatif : il dépend du mode de défaillance surveillé.</figcaption></figure>


Le point **P** est l'instant à partir duquel la dégradation devient détectable. Le point **F** est la défaillance fonctionnelle. L'**intervalle P-F** est le temps dont on dispose pour réagir [1]. Deux règles en découlent :

- **Plus la technique détecte tôt, plus l'intervalle P-F est long.** La vibration et les ultrasons voient souvent une détérioration de roulement bien avant l'échauffement.
- **La périodicité d'inspection doit être nettement inférieure à l'intervalle P-F.** Moubray recommande souvent la moitié de cet intervalle, pour être sûr d'observer au moins une fois la dégradation avant F et de disposer encore du temps nécessaire pour intervenir.

Avec une surveillance continue par capteurs connectés, la question de la périodicité disparaît. Le problème devient alors le **réglage des seuils** et la gestion des fausses alarmes.

## 5.3 Techniques de surveillance

| Technique | Grandeur mesurée | Défauts détectés | Atouts | Limites | Norme de référence |
|---|---|---|---|---|---|
| Analyse vibratoire | Accélération, vitesse, déplacement | Balourd, désalignement, desserrage, roulements, engrenages, cavitation | Très riche, détection précoce, normalisée | Capteur sur la machine, interprétation experte | ISO 20816 (sévérité) |
| Thermographie infrarouge | Température de surface | Échauffements électriques, frottements, défauts d'isolation thermique | Sans contact, rapide sur un grand parc | Émissivité à maîtriser, mesure en surface seulement | ISO 18434-1 |
| Analyse d'huile | Particules d'usure, viscosité, eau, acidité | Usure interne, contamination, dégradation du lubrifiant | Voit l'usure interne, indique la cause | Prélèvement, délai de laboratoire | — |
| Ultrasons | Émission haute fréquence (20 à 100 kHz) | Fuites d'air ou de gaz, défaut de lubrification, décharges électriques | Très précoce, simple à utiliser | Mesure surtout qualitative | — |
| Analyse du courant moteur (MCSA) | Spectre du courant statorique | Barres rotoriques cassées, excentricité, défauts de charge, certains défauts mécaniques | Mesure dans l'armoire électrique, non intrusive | Signatures faibles, dépendantes de la charge | — |
| Paramètres process | Débit, pression, puissance, rendement | Encrassement, usure hydraulique, fuites | Données déjà disponibles dans l'automate | Moins spécifique, influencé par le process | — |

Le cadre général de la surveillance des machines est donné par l'**ISO 17359:2018** (*Condition monitoring and diagnostics of machines — General guidelines*), qui décrit la démarche : choix des équipements, des modes de défaillance, des techniques et des seuils.

## 5.4 Analyse vibratoire

### Grandeurs et indicateurs

| Indicateur | Définition | Sensible à |
|---|---|---|
| Valeur efficace (RMS) | √(moyenne de x²) | Énergie globale : balourd, désalignement |
| Valeur crête | max \|x\| | Chocs |
| Facteur de crête | crête / RMS | Chocs périodiques des débuts de défaut de roulement |
| Kurtosis | E[(x − m)⁴] / σ⁴ ; vaut 3 pour un signal gaussien | Impulsivité : défaut de roulement localisé |
| Spectre (FFT) | Amplitude en fonction de la fréquence | Identification du défaut par sa fréquence |
| Spectre d'enveloppe | Spectre du signal démodulé autour d'une résonance | Fréquences de défaut de roulement masquées dans le spectre brut [2] |

La **vitesse** vibratoire (mm/s) est la grandeur des normes de sévérité, pour les fréquences de 10 Hz à 1 kHz environ. L'**accélération** (g ou m/s²) est préférée pour les hautes fréquences (roulements, engrenages). Le **déplacement** (µm) sert aux basses vitesses et aux paliers lisses.

### Fréquences caractéristiques des défauts

Avec *f_r* la fréquence de rotation de l'arbre :

| Défaut | Signature spectrale typique |
|---|---|
| Balourd | Pic à 1 × f_r, radial, en phase stable |
| Désalignement | Pics à 1 × et 2 × f_r, composante axiale importante |
| Desserrage, jeu mécanique | Nombreuses harmoniques de f_r, parfois sous-harmoniques (½ f_r) |
| Passage des aubes de pompe | Z × f_r, où Z est le nombre d'aubes de l'impulseur |
| Cavitation | Bruit large bande en haute fréquence, aléatoire |
| Engrènement | z × f_r (nombre de dents), avec des bandes latérales à la rotation de chaque roue |
| Défaut électrique de moteur asynchrone | 2 × f_s (deux fois la fréquence du réseau) |
| Roulement | Fréquences BPFO, BPFI, BSF, FTF ci-dessous |

Pour un roulement de *n* éléments roulants, de diamètre *d*, de diamètre primitif *D* et d'angle de contact *φ* :

```
FTF  = (f_r / 2) · (1 − (d/D) cos φ)                 cage
BPFO = (n · f_r / 2) · (1 − (d/D) cos φ)             bague extérieure
BPFI = (n · f_r / 2) · (1 + (d/D) cos φ)             bague intérieure
BSF  = (D · f_r / (2d)) · (1 − ((d/D) cos φ)²)        élément roulant
```

### Évaluation de la sévérité : ISO 20816-3

L'**ISO 20816-3:2022** (qui remplace l'ISO 10816-3) évalue la vibration des machines industrielles de plus de 15 kW à partir de la vitesse vibratoire efficace mesurée sur les paliers. Les limites dépendent de la puissance et du type de support.


<figure class="fig" id="fig-zones"><svg viewBox="0 0 680 250" role="img" aria-label="Zones d'évaluation vibratoire ISO 20816-3" xmlns="http://www.w3.org/2000/svg"><defs><marker id="ar" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path class="arh" d="M0,0 L10,5 L0,10 z"/></marker></defs><rect class="zA" x="151" y="28" width="56.3" height="30" rx="2"/><text class="tz" x="179.2" y="48" text-anchor="middle">A</text><rect class="zB" x="209.3" y="28" width="56.3" height="30" rx="2"/><text class="tz" x="237.5" y="48" text-anchor="middle">B</text><rect class="zC" x="267.7" y="28" width="68.8" height="30" rx="2"/><text class="tz" x="302.1" y="48" text-anchor="middle">C</text><rect class="zD" x="338.5" y="28" width="310.5" height="30" rx="2"/><text class="tz" x="493.8" y="48" text-anchor="middle">D</text><text class="t" x="140" y="48" text-anchor="end">Groupe 2, rigide</text><rect class="zA" x="151" y="72" width="93.8" height="30" rx="2"/><text class="tz" x="197.9" y="92" text-anchor="middle">A</text><rect class="zB" x="246.8" y="72" width="89.7" height="30" rx="2"/><text class="tz" x="291.7" y="92" text-anchor="middle">B</text><rect class="zC" x="338.5" y="72" width="106.3" height="30" rx="2"/><text class="tz" x="391.7" y="92" text-anchor="middle">C</text><rect class="zD" x="446.8" y="72" width="202.2" height="30" rx="2"/><text class="tz" x="547.9" y="92" text-anchor="middle">D</text><text class="t" x="140" y="92" text-anchor="end">Groupe 2, souple</text><rect class="zA" x="151" y="116" width="93.8" height="30" rx="2"/><text class="tz" x="197.9" y="136" text-anchor="middle">A</text><rect class="zB" x="246.8" y="116" width="89.7" height="30" rx="2"/><text class="tz" x="291.7" y="136" text-anchor="middle">B</text><rect class="zC" x="338.5" y="116" width="106.3" height="30" rx="2"/><text class="tz" x="391.7" y="136" text-anchor="middle">C</text><rect class="zD" x="446.8" y="116" width="202.2" height="30" rx="2"/><text class="tz" x="547.9" y="136" text-anchor="middle">D</text><text class="t" x="140" y="136" text-anchor="end">Groupe 1, rigide</text><rect class="zA" x="151" y="160" width="143.8" height="30" rx="2"/><text class="tz" x="222.9" y="180" text-anchor="middle">A</text><rect class="zB" x="296.8" y="160" width="148" height="30" rx="2"/><text class="tz" x="370.8" y="180" text-anchor="middle">B</text><rect class="zC" x="446.8" y="160" width="160.5" height="30" rx="2"/><text class="tz" x="527.1" y="180" text-anchor="middle">C</text><rect class="zD" x="609.3" y="160" width="39.7" height="30" rx="2"/><text class="tz" x="629.2" y="180" text-anchor="middle">D</text><text class="t" x="140" y="180" text-anchor="end">Groupe 1, souple</text><text class="tm" x="150" y="222" text-anchor="middle">0</text><text class="tm" x="233.3" y="222" text-anchor="middle">2</text><text class="tm" x="316.7" y="222" text-anchor="middle">4</text><text class="tm" x="400" y="222" text-anchor="middle">6</text><text class="tm" x="483.3" y="222" text-anchor="middle">8</text><text class="tm" x="566.7" y="222" text-anchor="middle">10</text><text class="tm" x="650" y="222" text-anchor="middle">12</text><text class="tm" x="650" y="240" text-anchor="end">vitesse vibratoire efficace (mm/s RMS)</text></svg><figcaption>Figure 5.2 — Limites des zones A à D de la norme ISO 20816-3 (machines industrielles de plus de 15 kW). Groupe 1 : plus de 300 kW ; groupe 2 : 15 à 300 kW. A : machine neuve ; B : fonctionnement illimité acceptable ; C : fonctionnement limité ; D : risque de dommage.</figcaption></figure>


| Groupe et support | A / B | B / C | C / D |
|---|---|---|---|
| Groupe 2 (15 à 300 kW), rigide | 1,4 | 2,8 | 4,5 |
| Groupe 2, souple | 2,3 | 4,5 | 7,1 |
| Groupe 1 (plus de 300 kW), rigide | 2,3 | 4,5 | 7,1 |
| Groupe 1, souple | 3,5 | 7,1 | 11,0 |

*Valeurs en mm/s RMS, à vérifier sur le texte de la norme avant tout usage contractuel.* Ces zones jugent la sévérité globale. Elles ne disent pas **quel** défaut est en cause : c'est le rôle de l'analyse spectrale.

## 5.5 Analyse de la signature du courant moteur (MCSA)

Un défaut mécanique ou électrique d'un moteur asynchrone module le couple ou l'entrefer, et donc le courant absorbé. Avec *f_s* la fréquence d'alimentation et *g* le glissement :

```
Barres rotoriques cassées   f = (1 ± 2k·g) · f_s
Excentricité, roulements    raies latérales f_s ± k · f_caractéristique
```

L'intérêt industriel est fort : le courant se mesure dans l'armoire électrique avec une pince ou un transformateur de courant, sans intervenir sur la machine [3]. La difficulté vient des amplitudes, de quelques dixièmes de pour cent du fondamental, et de leur dépendance à la charge et au variateur de vitesse. C'est le point étudié par le projet PRJ-01, qui compare courant et vibration sur une électropompe.

## 5.6 Chaîne d'acquisition et de traitement


<figure class="fig" id="fig-chaine"><svg viewBox="0 0 680 110" role="img" aria-label="Chaîne de surveillance d'un équipement" xmlns="http://www.w3.org/2000/svg"><defs><marker id="ar" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path class="arh" d="M0,0 L10,5 L0,10 z"/></marker></defs><rect class="bx" x="10" y="30" width="96" height="56" rx="4"/><text class="t" x="58" y="62" text-anchor="middle">Capteur</text><line class="arw" x1="106" y1="58" x2="122" y2="58" marker-end="url(#ar)"/><rect class="bx" x="122" y="30" width="96" height="56" rx="4"/><text class="t" x="170" y="54.5" text-anchor="middle">Conditionnement</text><text class="t" x="170" y="69.5" text-anchor="middle">anti-repliement</text><line class="arw" x1="218" y1="58" x2="234" y2="58" marker-end="url(#ar)"/><rect class="bx" x="234" y="30" width="96" height="56" rx="4"/><text class="t" x="282" y="54.5" text-anchor="middle">Numérisation</text><text class="t" x="282" y="69.5" text-anchor="middle">fe > 2 fmax</text><line class="arw" x1="330" y1="58" x2="346" y2="58" marker-end="url(#ar)"/><rect class="bx" x="346" y="30" width="96" height="56" rx="4"/><text class="t" x="394" y="54.5" text-anchor="middle">Traitement</text><text class="t" x="394" y="69.5" text-anchor="middle">FFT, enveloppe</text><line class="arw" x1="442" y1="58" x2="458" y2="58" marker-end="url(#ar)"/><rect class="bx acc" x="458" y="30" width="96" height="56" rx="4"/><text class="t" x="506" y="54.5" text-anchor="middle">Indicateurs</text><text class="t" x="506" y="69.5" text-anchor="middle">RMS, kurtosis</text><line class="arw" x1="554" y1="58" x2="570" y2="58" marker-end="url(#ar)"/><rect class="bx acc" x="570" y="30" width="96" height="56" rx="4"/><text class="t" x="618" y="54.5" text-anchor="middle">Décision</text><text class="t" x="618" y="69.5" text-anchor="middle">seuil, modèle</text></svg><figcaption>Figure 5.3 — Chaîne de surveillance, du signal brut à la décision.</figcaption></figure>


| Paramètre | Règle | Conséquence |
|---|---|---|
| Fréquence d'échantillonnage f_e | Théorème de Shannon : f_e > 2 f_max ; en pratique, les analyseurs prennent f_e = 2,56 f_max | En dessous, repliement spectral : des fréquences fantômes apparaissent |
| Filtre anti-repliement | Filtre passe-bas analogique avant le convertisseur | Indispensable : on ne corrige pas le repliement après coup |
| Résolution spectrale | Δf = f_e / N (N : nombre de points) | Il faut une acquisition longue pour séparer des raies proches (bandes latérales) |
| Fenêtrage | Fenêtre de Hann pour l'analyse de raies | Limite les fuites spectrales |
| Fixation du capteur | Goujon, plutôt qu'aimant ou pointe de touche | Une mauvaise fixation réduit la bande passante utile |

## 5.7 Outils d'analyse

| Outil | Ce qu'il apporte | Usage dans le portfolio |
|---|---|---|
| MATLAB + Signal Processing Toolbox | FFT, filtrage, spectre d'enveloppe (`pspectrum`, `envspectrum`) | Vérification croisée des indicateurs |
| MATLAB Predictive Maintenance Toolbox | Diagnostic Feature Designer, classement des indicateurs, modèles de RUL | Guide de formation du cours |
| Python : NumPy, SciPy, pandas | Calcul scientifique, signaux, tableaux de données | Chaîne principale du projet PRJ-01 |
| Python : scikit-learn | Classification, détection d'anomalies, validation croisée | Modèles de référence |
| TensorFlow ou PyTorch | Réseaux de neurones (CNN, LSTM) | Seulement si un gain est démontré par rapport aux modèles simples |
| Power BI | Tableaux de bord d'indicateurs | Restitution aux équipes maintenance |

## 5.8 Limites des données industrielles

| Problème | Description | Parade |
|---|---|---|
| Déséquilibre des classes | Beaucoup de données saines, peu de défaillances | Métriques adaptées (F1, rappel), pondération des classes, détection entraînée sur l'état sain |
| Fuite de données | Des fenêtres d'un même enregistrement se retrouvent à la fois en apprentissage et en test | Séparer par enregistrement, par machine ou par période |
| Conditions variables | La vitesse et la charge modifient les signaux autant qu'un défaut | Normaliser par la vitesse (analyse d'ordre), tester sur des conditions non vues |
| Défauts implantés | En laboratoire, les défauts sont créés artificiellement | Prudence sur la transposition au terrain ; valider sur des dégradations réelles si possible |
| Étiquettes peu fiables | Causes de panne mal renseignées dans la GMAO | Revue des historiques avec les techniciens |
| Dérive des capteurs | Un capteur vieillit ou se décale | Contrôle de cohérence, redondance, étalonnage |

## 5.9 Intérêt économique

Le guide des bonnes pratiques d'exploitation et de maintenance du Département de l'Énergie américain (programme FEMP) estime que la maintenance prédictive permet une économie de 8 à 12 % par rapport à un programme préventif, et de 30 à 40 % par rapport à une maintenance purement corrective [4]. Ce sont des ordres de grandeur issus de retours d'expérience variés : un projet doit établir son propre bilan à partir des coûts de défaillance réels du site.

## Références

<ol class="refs">
<li>[1] J. Moubray, <i>Reliability-Centred Maintenance</i>, 2ᵉ éd. Oxford : Butterworth-Heinemann, 1997.</li>
<li>[2] R. B. Randall et J. Antoni, « Rolling element bearing diagnostics — A tutorial », <i>Mech. Syst. Signal Process.</i>, vol. 25, n° 2, p. 485-520, 2011.</li>
<li>[3] W. T. Thomson et M. Fenger, « Current signature analysis to detect induction motor faults », <i>IEEE Ind. Appl. Mag.</i>, vol. 7, n° 4, p. 26-34, 2001.</li>
<li>[4] G. P. Sullivan, R. Pugh, A. P. Melendez et W. D. Hunt, <i>Operations &amp; Maintenance Best Practices — A Guide to Achieving Operational Efficiency</i>, Release 3.0, U.S. DOE, Federal Energy Management Program, 2010.</li>
<li>[5] ISO, <i>ISO 20816-3:2022 — Mechanical vibration — Measurement and evaluation of machine vibration — Part 3: Industrial machines with a power rating above 15 kW and operating speeds between 120 r/min and 30 000 r/min</i>. Genève : ISO, 2022.</li>
<li>[6] ISO, <i>ISO 17359:2018 — Condition monitoring and diagnostics of machines — General guidelines</i>. Genève : ISO, 2018.</li>
<li>[7] F. Ben Hmida, <i>Maintenance industrielle — Chap. 4 : Maintenance prédictive</i>, support de cours, ENSIT, 2024.</li>
</ol>
