# Sûreté de fonctionnement et indices FMDS

> **État :** rédigé (version 1) · **Responsable :** à attribuer

La sûreté de fonctionnement (SdF) est l'aptitude d'un système à accomplir sa mission dans des conditions données, avec un niveau de confiance justifié. On la résume souvent comme la « science des défaillances » [1] : on les connaît, on les évalue, on les prévoit et on les maîtrise. Cette section en présente les quatre composantes (FMDS), les lois de probabilité qui les décrivent, les méthodes d'analyse et l'estimation à partir de données réelles.

## 2.1 Les composantes FMDS

| Composante | Définition | Grandeur | Indicateur moyen | Question posée |
|---|---|---|---|---|
| **F**iabilité | Aptitude d'un bien à accomplir une fonction requise, dans des conditions données, durant un intervalle de temps donné | R(t) = P(pas de défaillance sur [0, t]) | MTTF, MUT | Combien de temps avant la prochaine défaillance ? |
| **M**aintenabilité | Aptitude d'un bien à être maintenu ou rétabli dans un état où il peut accomplir sa fonction, quand la maintenance est réalisée dans des conditions données | M(t) = P(réparation terminée avant t) | MTTR | En combien de temps remet-on en service ? |
| **D**isponibilité | Aptitude d'un bien à être en état d'accomplir une fonction requise à un instant donné | A(t) = P(en état de marche à t) | A∞ = MUT / (MUT + MDT) | Est-il prêt quand on en a besoin ? |
| **S**écurité | Aptitude à éviter de faire apparaître des événements critiques ou catastrophiques | S(t) = P(pas d'événement critique sur [0, t]) | Fréquence d'événements redoutés | Risque-t-il de blesser ou de polluer ? |

Ces composantes sont liées : la disponibilité dépend à la fois de la fiabilité (fréquence des pannes) et de la maintenabilité (durée des remises en service). Améliorer la fiabilité en ajoutant des composants redondants peut dégrader la maintenabilité (plus de pièces à contrôler) et le coût. Le vocabulaire international est fixé par l'IEC 60050-192 (*Vocabulaire électrotechnique — Sûreté de fonctionnement*).

## 2.2 Classification des défaillances

| Critère | Classes |
|---|---|
| Vitesse d'apparition | Progressive (prévisible par surveillance) ; soudaine (non prévisible) |
| Degré | Partielle (fonction dégradée) ; complète (fonction perdue) |
| Combinaison des deux | **Catalectique** : soudaine et complète ; **par dégradation** : progressive et partielle |
| Cause | Primaire (faiblesse propre au bien) ; seconde (due à une autre défaillance) ; de commande (mauvaise sollicitation) |
| Date d'apparition | Précoce (jeunesse) ; aléatoire (vie utile) ; d'usure (vieillissement) |
| Gravité des effets | Mineure ; significative ; critique ; catastrophique |

Le **mode de défaillance** est la manière dont une défaillance se manifeste (fuite, blocage, absence de signal, dérive). Il ne faut pas le confondre avec sa **cause** (usure, corrosion, surcharge) ni avec son **effet** (arrêt de ligne, pollution).

## 2.3 Fiabilité : grandeurs et relations

Soit *T* la durée de vie d'un bien, variable aléatoire positive.

```
F(t) = P(T ≤ t)                    fonction de répartition (probabilité de défaillance)
R(t) = 1 − F(t)                    fiabilité
f(t) = dF/dt = −dR/dt              densité de probabilité
λ(t) = f(t) / R(t)                 taux de défaillance instantané
R(t) = exp( −∫₀ᵗ λ(u) du )
MTTF = E[T] = ∫₀^∞ R(t) dt
```

Le taux de défaillance λ(t)·dt est la probabilité qu'un bien qui a survécu jusqu'à *t* tombe en panne entre *t* et *t + dt*. Son évolution dans le temps donne la courbe en baignoire.


<figure class="fig" id="fig-baignoire"><svg viewBox="0 0 640 280" role="img" aria-label="Courbe en baignoire" xmlns="http://www.w3.org/2000/svg"><defs><marker id="ar" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path class="arh" d="M0,0 L10,5 L0,10 z"/></marker></defs><line class="ax" x1="70" y1="230" x2="610" y2="230"/><line class="ax" x1="70" y1="30" x2="70" y2="230"/><text class="tm" x="610" y="264" text-anchor="end">Temps t →</text><text class="tm" x="70" y="22" text-anchor="start">Taux de défaillance λ(t)</text><line class="dim dash" x1="178" y1="230" x2="178" y2="30"/><line class="dim dash" x1="448" y1="230" x2="448" y2="30"/><polyline class="c1 thick" points="72.7,49.6 75.4,60.7 78.1,70.8 80.8,80.1 83.5,88.7 86.2,96.5 88.9,103.8 91.6,110.5 94.3,116.6 97,122.2 99.7,127.4 102.4,132.2 105.1,136.6 107.8,140.6 110.5,144.3 113.2,147.7 115.9,150.8 118.6,153.7 121.3,156.3 124,158.8 126.7,161 129.4,163 132.1,164.9 134.8,166.6 137.5,168.2 140.2,169.6 142.9,171 145.6,172.2 148.3,173.3 151,174.3 153.7,175.2 156.4,176.1 159.1,176.9 161.8,177.6 164.5,178.2 167.2,178.8 169.9,179.3 172.6,179.8 175.3,180.3 178,180.7 180.7,181 183.4,181.3 186.1,181.6 188.8,181.9 191.5,182.1 194.2,182.3 196.9,182.5 199.6,182.6 202.3,182.7 205,182.8 207.7,182.9 210.4,183 213.1,183 215.8,183.1 218.5,183.1 221.2,183.1 223.9,183.1 226.6,183.1 229.3,183 232,183 234.7,182.9 237.4,182.9 240.1,182.8 242.8,182.7 245.5,182.6 248.2,182.5 250.9,182.4 253.6,182.2 256.3,182.1 259,182 261.7,181.8 264.4,181.6 267.1,181.5 269.8,181.3 272.5,181.1 275.2,180.9 277.9,180.7 280.6,180.5 283.3,180.3 286,180 288.7,179.8 291.4,179.5 294.1,179.3 296.8,179 299.5,178.7 302.2,178.4 304.9,178.1 307.6,177.8 310.3,177.5 313,177.1 315.7,176.8 318.4,176.4 321.1,176.1 323.8,175.7 326.5,175.3 329.2,174.9 331.9,174.5 334.6,174 337.3,173.6 340,173.1 342.7,172.6 345.4,172.2 348.1,171.6 350.8,171.1 353.5,170.6 356.2,170 358.9,169.4 361.6,168.8 364.3,168.2 367,167.6 369.7,166.9 372.4,166.2 375.1,165.5 377.8,164.8 380.5,164.1 383.2,163.3 385.9,162.5 388.6,161.7 391.3,160.9 394,160 396.7,159.1 399.4,158.2 402.1,157.2 404.8,156.2 407.5,155.2 410.2,154.1 412.9,153.1 415.6,151.9 418.3,150.8 421,149.6 423.7,148.4 426.4,147.1 429.1,145.8 431.8,144.4 434.5,143 437.2,141.6 439.9,140.1 442.6,138.6 445.3,137 448,135.4 450.7,133.7 453.4,132 456.1,130.2 458.8,128.3 461.5,126.4 464.2,124.5 466.9,122.4 469.6,120.3 472.3,118.2 475,115.9 477.7,113.6 480.4,111.3 483.1,108.8 485.8,106.3 488.5,103.7 491.2,101 493.9,98.2 496.6,95.4 499.3,92.4 502,89.4 504.7,86.3 507.4,83 510.1,79.7 512.8,76.2 515.5,72.7 518.2,69 520.9,65.2 523.6,61.3 526.3,57.3 529,53.1 531.7,48.8 534.4,44.4 537.1,39.8 539.8,38.3 542.5,38.3 545.2,38.3 547.9,38.3 550.6,38.3 553.3,38.3 556,38.3 558.7,38.3 561.4,38.3 564.1,38.3 566.8,38.3 569.5,38.3 572.2,38.3 574.9,38.3 577.6,38.3 580.3,38.3 583,38.3 585.7,38.3 588.4,38.3 591.1,38.3 593.8,38.3 596.5,38.3 599.2,38.3 601.9,38.3 604.6,38.3 607.3,38.3 610,38.3"/><text class="tb" x="124" y="43.3" text-anchor="middle">Jeunesse</text><text class="tm" x="124" y="60" text-anchor="middle">λ décroissant, β < 1</text><text class="tb" x="313" y="43.3" text-anchor="middle">Vie utile (maturité)</text><text class="tm" x="313" y="60" text-anchor="middle">λ ≈ constant, β ≈ 1</text><text class="tb" x="529" y="43.3" text-anchor="middle">Vieillissement</text><text class="tm" x="529" y="60" text-anchor="middle">λ croissant, β > 1</text></svg><figcaption>Figure 2.1 — Courbe en baignoire du taux de défaillance (forme qualitative). Chaque zone correspond à un paramètre de forme β de la loi de Weibull et appelle une politique de maintenance différente.</figcaption></figure>


### Les lois usuelles

| Loi | R(t) | λ(t) | MTTF | Domaine d'emploi |
|---|---|---|---|---|
| Exponentielle | exp(−λt) | λ constant | 1/λ | Composants électroniques en vie utile, défaillances aléatoires |
| Weibull (β, η) | exp(−(t/η)^β) | (β/η)(t/η)^(β−1) | η·Γ(1 + 1/β) | Mécanique : fatigue, usure ; s'adapte aux trois zones de la baignoire |
| Normale (m, σ) | 1 − Φ((t − m)/σ) | croissant | m | Usure avec dispersion symétrique |
| Log-normale | 1 − Φ((ln t − μ)/σ) | croît puis décroît | exp(μ + σ²/2) | Temps de réparation, fatigue |

La loi de Weibull est la plus utilisée en maintenance, car son paramètre de forme β indique la phase de vie :

- **β < 1** : défaillances de jeunesse. Remplacer préventivement aggrave la situation : on réintroduit des pièces neuves fragiles.
- **β = 1** : taux constant (loi exponentielle). Le remplacement systématique est inutile, car la pièce ne « vieillit » pas.
- **β > 1** : usure. Le remplacement systématique ou conditionnel devient pertinent.


<figure class="fig" id="fig-weibull"><svg viewBox="0 0 680 270" role="img" aria-label="Fiabilité et taux de défaillance de Weibull pour trois valeurs de beta" xmlns="http://www.w3.org/2000/svg"><defs><marker id="ar" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path class="arh" d="M0,0 L10,5 L0,10 z"/></marker></defs><line class="gr" x1="60" x2="310" y1="220" y2="220"/><line class="gr" x1="60" x2="310" y1="125" y2="125"/><line class="gr" x1="60" x2="310" y1="30" y2="30"/><line class="ax" x1="60" y1="220" x2="310" y2="220"/><line class="ax" x1="60" y1="30" x2="60" y2="220"/><text class="tm" x="60" y="236" text-anchor="middle">0</text><text class="tm" x="160" y="236" text-anchor="middle">1</text><text class="tm" x="260" y="236" text-anchor="middle">2</text><text class="tm" x="54" y="224" text-anchor="end">0</text><text class="tm" x="54" y="129" text-anchor="end">0,5</text><text class="tm" x="54" y="34" text-anchor="end">1</text><text class="tm" x="310" y="254" text-anchor="end">t / η</text><text class="tm" x="60" y="22" text-anchor="start">R(t)</text><line class="gr" x1="390" x2="640" y1="220" y2="220"/><line class="gr" x1="390" x2="640" y1="156.7" y2="156.7"/><line class="gr" x1="390" x2="640" y1="93.3" y2="93.3"/><line class="gr" x1="390" x2="640" y1="30" y2="30"/><line class="ax" x1="390" y1="220" x2="640" y2="220"/><line class="ax" x1="390" y1="30" x2="390" y2="220"/><text class="tm" x="390" y="236" text-anchor="middle">0</text><text class="tm" x="490" y="236" text-anchor="middle">1</text><text class="tm" x="590" y="236" text-anchor="middle">2</text><text class="tm" x="384" y="224" text-anchor="end">0</text><text class="tm" x="384" y="160.7" text-anchor="end">1</text><text class="tm" x="384" y="97.3" text-anchor="end">2</text><text class="tm" x="384" y="34" text-anchor="end">3</text><text class="tm" x="640" y="254" text-anchor="end">t / η</text><text class="tm" x="390" y="22" text-anchor="start">λ(t) · η</text><polyline class="c2 dashed" points="60.1,35.9 61.4,50.9 62.6,58.4 63.9,63.9 65.1,68.5 66.4,72.4 67.6,75.9 68.9,79 70.1,81.8 71.4,84.4 72.7,86.9 73.9,89.2 75.2,91.3 76.4,93.3 77.7,95.2 78.9,97 80.2,98.8 81.4,100.4 82.7,102 84,103.5 85.2,105 86.5,106.4 87.7,107.8 89,109.1 90.2,110.4 91.5,111.6 92.8,112.8 94,114 95.3,115.1 96.5,116.2 97.8,117.2 99,118.3 100.3,119.3 101.5,120.3 102.8,121.2 104.1,122.2 105.3,123.1 106.6,124 107.8,124.8 109.1,125.7 110.3,126.5 111.6,127.4 112.8,128.2 114.1,128.9 115.4,129.7 116.6,130.5 117.9,131.2 119.1,131.9 120.4,132.6 121.6,133.3 122.9,134 124.1,134.7 125.4,135.4 126.7,136 127.9,136.7 129.2,137.3 130.4,137.9 131.7,138.5 132.9,139.1 134.2,139.7 135.4,140.3 136.7,140.9 138,141.4 139.2,142 140.5,142.5 141.7,143.1 143,143.6 144.2,144.1 145.5,144.6 146.7,145.1 148,145.6 149.3,146.1 150.5,146.6 151.8,147.1 153,147.6 154.3,148 155.5,148.5 156.8,149 158.1,149.4 159.3,149.9 160.6,150.3 161.8,150.7 163.1,151.2 164.3,151.6 165.6,152 166.8,152.4 168.1,152.8 169.4,153.2 170.6,153.6 171.9,154 173.1,154.4 174.4,154.8 175.6,155.2 176.9,155.6 178.1,155.9 179.4,156.3 180.7,156.7 181.9,157 183.2,157.4 184.4,157.7 185.7,158.1 186.9,158.4 188.2,158.8 189.4,159.1 190.7,159.4 192,159.8 193.2,160.1 194.5,160.4 195.7,160.7 197,161.1 198.2,161.4 199.5,161.7 200.7,162 202,162.3 203.3,162.6 204.5,162.9 205.8,163.2 207,163.5 208.3,163.8 209.5,164.1 210.8,164.4 212,164.6 213.3,164.9 214.6,165.2 215.8,165.5 217.1,165.7 218.3,166 219.6,166.3 220.8,166.5 222.1,166.8 223.4,167.1 224.6,167.3 225.9,167.6 227.1,167.8 228.4,168.1 229.6,168.3 230.9,168.6 232.1,168.8 233.4,169.1 234.7,169.3 235.9,169.6 237.2,169.8 238.4,170 239.7,170.3 240.9,170.5 242.2,170.7 243.4,171 244.7,171.2 246,171.4 247.2,171.6 248.5,171.9 249.7,172.1 251,172.3 252.2,172.5 253.5,172.7 254.7,172.9 256,173.1 257.3,173.4 258.5,173.6 259.8,173.8 261,174 262.3,174.2 263.5,174.4 264.8,174.6 266,174.8 267.3,175 268.6,175.2 269.8,175.4 271.1,175.6 272.3,175.7 273.6,175.9 274.8,176.1 276.1,176.3 277.3,176.5 278.6,176.7 279.9,176.9 281.1,177.1 282.4,177.2 283.6,177.4 284.9,177.6 286.1,177.8 287.4,177.9 288.7,178.1 289.9,178.3 291.2,178.5 292.4,178.6 293.7,178.8 294.9,179 296.2,179.1 297.4,179.3 298.7,179.5 300,179.6 301.2,179.8 302.5,180 303.7,180.1 305,180.3 306.2,180.4 307.5,180.6 308.7,180.8 310,180.9"/><polyline class="c2 dashed" points="393.9,59 395.1,80.1 396.4,94.6 397.6,105.4 398.9,113.8 400.1,120.6 401.4,126.2 402.7,131 403.9,135.1 405.2,138.7 406.4,141.9 407.7,144.7 408.9,147.2 410.2,149.5 411.4,151.6 412.7,153.5 414,155.3 415.2,156.9 416.5,158.5 417.7,159.9 419,161.2 420.2,162.4 421.5,163.6 422.8,164.7 424,165.7 425.3,166.7 426.5,167.6 427.8,168.5 429,169.3 430.3,170.1 431.5,170.9 432.8,171.6 434.1,172.3 435.3,173 436.6,173.6 437.8,174.2 439.1,174.8 440.3,175.4 441.6,175.9 442.8,176.4 444.1,176.9 445.4,177.4 446.6,177.9 447.9,178.4 449.1,178.8 450.4,179.2 451.6,179.7 452.9,180.1 454.1,180.5 455.4,180.8 456.7,181.2 457.9,181.6 459.2,181.9 460.4,182.3 461.7,182.6 462.9,182.9 464.2,183.2 465.4,183.5 466.7,183.8 468,184.1 469.2,184.4 470.5,184.7 471.7,185 473,185.2 474.2,185.5 475.5,185.8 476.7,186 478,186.2 479.3,186.5 480.5,186.7 481.8,186.9 483,187.2 484.3,187.4 485.5,187.6 486.8,187.8 488.1,188 489.3,188.2 490.6,188.4 491.8,188.6 493.1,188.8 494.3,189 495.6,189.2 496.8,189.4 498.1,189.5 499.4,189.7 500.6,189.9 501.9,190.1 503.1,190.2 504.4,190.4 505.6,190.6 506.9,190.7 508.1,190.9 509.4,191 510.7,191.2 511.9,191.3 513.2,191.5 514.4,191.6 515.7,191.8 516.9,191.9 518.2,192 519.4,192.2 520.7,192.3 522,192.4 523.2,192.6 524.5,192.7 525.7,192.8 527,192.9 528.2,193.1 529.5,193.2 530.7,193.3 532,193.4 533.3,193.5 534.5,193.7 535.8,193.8 537,193.9 538.3,194 539.5,194.1 540.8,194.2 542,194.3 543.3,194.4 544.6,194.5 545.8,194.6 547.1,194.7 548.3,194.8 549.6,194.9 550.8,195 552.1,195.1 553.4,195.2 554.6,195.3 555.9,195.4 557.1,195.5 558.4,195.6 559.6,195.7 560.9,195.8 562.1,195.9 563.4,196 564.7,196 565.9,196.1 567.2,196.2 568.4,196.3 569.7,196.4 570.9,196.5 572.2,196.5 573.4,196.6 574.7,196.7 576,196.8 577.2,196.9 578.5,196.9 579.7,197 581,197.1 582.2,197.2 583.5,197.2 584.7,197.3 586,197.4 587.3,197.5 588.5,197.5 589.8,197.6 591,197.7 592.3,197.7 593.5,197.8 594.8,197.9 596,197.9 597.3,198 598.6,198.1 599.8,198.1 601.1,198.2 602.3,198.3 603.6,198.3 604.8,198.4 606.1,198.5 607.3,198.5 608.6,198.6 609.9,198.6 611.1,198.7 612.4,198.8 613.6,198.8 614.9,198.9 616.1,198.9 617.4,199 618.7,199.1 619.9,199.1 621.2,199.2 622.4,199.2 623.7,199.3 624.9,199.3 626.2,199.4 627.4,199.4 628.7,199.5 630,199.6 631.2,199.6 632.5,199.7 633.7,199.7 635,199.8 636.2,199.8 637.5,199.9 638.7,199.9 640,200"/><polyline class="c3" points="60.1,30.2 61.4,32.6 62.6,34.9 63.9,37.2 65.1,39.5 66.4,41.7 67.6,44 68.9,46.2 70.1,48.3 71.4,50.5 72.7,52.6 73.9,54.7 75.2,56.7 76.4,58.8 77.7,60.8 78.9,62.8 80.2,64.7 81.4,66.7 82.7,68.6 84,70.5 85.2,72.3 86.5,74.2 87.7,76 89,77.8 90.2,79.6 91.5,81.3 92.8,83.1 94,84.8 95.3,86.5 96.5,88.1 97.8,89.8 99,91.4 100.3,93 101.5,94.6 102.8,96.2 104.1,97.7 105.3,99.2 106.6,100.7 107.8,102.2 109.1,103.7 110.3,105.1 111.6,106.6 112.8,108 114.1,109.4 115.4,110.8 116.6,112.1 117.9,113.5 119.1,114.8 120.4,116.1 121.6,117.4 122.9,118.7 124.1,120 125.4,121.2 126.7,122.4 127.9,123.7 129.2,124.9 130.4,126 131.7,127.2 132.9,128.4 134.2,129.5 135.4,130.7 136.7,131.8 138,132.9 139.2,134 140.5,135 141.7,136.1 143,137.1 144.2,138.2 145.5,139.2 146.7,140.2 148,141.2 149.3,142.2 150.5,143.1 151.8,144.1 153,145.1 154.3,146 155.5,146.9 156.8,147.8 158.1,148.7 159.3,149.6 160.6,150.5 161.8,151.4 163.1,152.2 164.3,153.1 165.6,153.9 166.8,154.7 168.1,155.5 169.4,156.3 170.6,157.1 171.9,157.9 173.1,158.7 174.4,159.5 175.6,160.2 176.9,161 178.1,161.7 179.4,162.4 180.7,163.1 181.9,163.9 183.2,164.6 184.4,165.2 185.7,165.9 186.9,166.6 188.2,167.3 189.4,167.9 190.7,168.6 192,169.2 193.2,169.9 194.5,170.5 195.7,171.1 197,171.7 198.2,172.3 199.5,172.9 200.7,173.5 202,174.1 203.3,174.6 204.5,175.2 205.8,175.8 207,176.3 208.3,176.9 209.5,177.4 210.8,177.9 212,178.5 213.3,179 214.6,179.5 215.8,180 217.1,180.5 218.3,181 219.6,181.5 220.8,182 222.1,182.4 223.4,182.9 224.6,183.4 225.9,183.8 227.1,184.3 228.4,184.7 229.6,185.2 230.9,185.6 232.1,186 233.4,186.4 234.7,186.9 235.9,187.3 237.2,187.7 238.4,188.1 239.7,188.5 240.9,188.9 242.2,189.3 243.4,189.7 244.7,190 246,190.4 247.2,190.8 248.5,191.1 249.7,191.5 251,191.9 252.2,192.2 253.5,192.6 254.7,192.9 256,193.2 257.3,193.6 258.5,193.9 259.8,194.2 261,194.5 262.3,194.9 263.5,195.2 264.8,195.5 266,195.8 267.3,196.1 268.6,196.4 269.8,196.7 271.1,197 272.3,197.3 273.6,197.6 274.8,197.8 276.1,198.1 277.3,198.4 278.6,198.7 279.9,198.9 281.1,199.2 282.4,199.4 283.6,199.7 284.9,200 286.1,200.2 287.4,200.4 288.7,200.7 289.9,200.9 291.2,201.2 292.4,201.4 293.7,201.6 294.9,201.9 296.2,202.1 297.4,202.3 298.7,202.5 300,202.8 301.2,203 302.5,203.2 303.7,203.4 305,203.6 306.2,203.8 307.5,204 308.7,204.2 310,204.4"/><polyline class="c3" points="390.1,156.7 391.4,156.7 392.6,156.7 393.9,156.7 395.1,156.7 396.4,156.7 397.6,156.7 398.9,156.7 400.1,156.7 401.4,156.7 402.7,156.7 403.9,156.7 405.2,156.7 406.4,156.7 407.7,156.7 408.9,156.7 410.2,156.7 411.4,156.7 412.7,156.7 414,156.7 415.2,156.7 416.5,156.7 417.7,156.7 419,156.7 420.2,156.7 421.5,156.7 422.8,156.7 424,156.7 425.3,156.7 426.5,156.7 427.8,156.7 429,156.7 430.3,156.7 431.5,156.7 432.8,156.7 434.1,156.7 435.3,156.7 436.6,156.7 437.8,156.7 439.1,156.7 440.3,156.7 441.6,156.7 442.8,156.7 444.1,156.7 445.4,156.7 446.6,156.7 447.9,156.7 449.1,156.7 450.4,156.7 451.6,156.7 452.9,156.7 454.1,156.7 455.4,156.7 456.7,156.7 457.9,156.7 459.2,156.7 460.4,156.7 461.7,156.7 462.9,156.7 464.2,156.7 465.4,156.7 466.7,156.7 468,156.7 469.2,156.7 470.5,156.7 471.7,156.7 473,156.7 474.2,156.7 475.5,156.7 476.7,156.7 478,156.7 479.3,156.7 480.5,156.7 481.8,156.7 483,156.7 484.3,156.7 485.5,156.7 486.8,156.7 488.1,156.7 489.3,156.7 490.6,156.7 491.8,156.7 493.1,156.7 494.3,156.7 495.6,156.7 496.8,156.7 498.1,156.7 499.4,156.7 500.6,156.7 501.9,156.7 503.1,156.7 504.4,156.7 505.6,156.7 506.9,156.7 508.1,156.7 509.4,156.7 510.7,156.7 511.9,156.7 513.2,156.7 514.4,156.7 515.7,156.7 516.9,156.7 518.2,156.7 519.4,156.7 520.7,156.7 522,156.7 523.2,156.7 524.5,156.7 525.7,156.7 527,156.7 528.2,156.7 529.5,156.7 530.7,156.7 532,156.7 533.3,156.7 534.5,156.7 535.8,156.7 537,156.7 538.3,156.7 539.5,156.7 540.8,156.7 542,156.7 543.3,156.7 544.6,156.7 545.8,156.7 547.1,156.7 548.3,156.7 549.6,156.7 550.8,156.7 552.1,156.7 553.4,156.7 554.6,156.7 555.9,156.7 557.1,156.7 558.4,156.7 559.6,156.7 560.9,156.7 562.1,156.7 563.4,156.7 564.7,156.7 565.9,156.7 567.2,156.7 568.4,156.7 569.7,156.7 570.9,156.7 572.2,156.7 573.4,156.7 574.7,156.7 576,156.7 577.2,156.7 578.5,156.7 579.7,156.7 581,156.7 582.2,156.7 583.5,156.7 584.7,156.7 586,156.7 587.3,156.7 588.5,156.7 589.8,156.7 591,156.7 592.3,156.7 593.5,156.7 594.8,156.7 596,156.7 597.3,156.7 598.6,156.7 599.8,156.7 601.1,156.7 602.3,156.7 603.6,156.7 604.8,156.7 606.1,156.7 607.3,156.7 608.6,156.7 609.9,156.7 611.1,156.7 612.4,156.7 613.6,156.7 614.9,156.7 616.1,156.7 617.4,156.7 618.7,156.7 619.9,156.7 621.2,156.7 622.4,156.7 623.7,156.7 624.9,156.7 626.2,156.7 627.4,156.7 628.7,156.7 630,156.7 631.2,156.7 632.5,156.7 633.7,156.7 635,156.7 636.2,156.7 637.5,156.7 638.7,156.7 640,156.7"/><polyline class="c1" points="60.1,30 61.4,30 62.6,30 63.9,30 65.1,30 66.4,30 67.6,30.1 68.9,30.1 70.1,30.2 71.4,30.3 72.7,30.4 73.9,30.5 75.2,30.7 76.4,30.8 77.7,31 78.9,31.3 80.2,31.6 81.4,31.9 82.7,32.2 84,32.6 85.2,33 86.5,33.5 87.7,34 89,34.6 90.2,35.2 91.5,35.8 92.8,36.6 94,37.3 95.3,38.2 96.5,39 97.8,40 99,41 100.3,42 101.5,43.1 102.8,44.3 104.1,45.6 105.3,46.9 106.6,48.2 107.8,49.7 109.1,51.2 110.3,52.7 111.6,54.4 112.8,56.1 114.1,57.8 115.4,59.6 116.6,61.5 117.9,63.5 119.1,65.5 120.4,67.5 121.6,69.7 122.9,71.8 124.1,74.1 125.4,76.4 126.7,78.7 127.9,81.1 129.2,83.5 130.4,86 131.7,88.5 132.9,91.1 134.2,93.7 135.4,96.3 136.7,99 138,101.7 139.2,104.4 140.5,107.2 141.7,109.9 143,112.7 144.2,115.5 145.5,118.3 146.7,121.1 148,123.9 149.3,126.7 150.5,129.5 151.8,132.3 153,135.1 154.3,137.8 155.5,140.6 156.8,143.3 158.1,146 159.3,148.6 160.6,151.3 161.8,153.9 163.1,156.4 164.3,159 165.6,161.4 166.8,163.9 168.1,166.3 169.4,168.6 170.6,170.9 171.9,173.1 173.1,175.3 174.4,177.4 175.6,179.5 176.9,181.5 178.1,183.5 179.4,185.4 180.7,187.2 181.9,189 183.2,190.7 184.4,192.3 185.7,193.9 186.9,195.4 188.2,196.9 189.4,198.3 190.7,199.6 192,200.9 193.2,202.1 194.5,203.3 195.7,204.4 197,205.5 198.2,206.5 199.5,207.4 200.7,208.3 202,209.2 203.3,210 204.5,210.7 205.8,211.4 207,212.1 208.3,212.7 209.5,213.3 210.8,213.8 212,214.3 213.3,214.8 214.6,215.3 215.8,215.7 217.1,216.1 218.3,216.4 219.6,216.7 220.8,217 222.1,217.3 223.4,217.6 224.6,217.8 225.9,218 227.1,218.2 228.4,218.4 229.6,218.6 230.9,218.7 232.1,218.8 233.4,219 234.7,219.1 235.9,219.2 237.2,219.3 238.4,219.4 239.7,219.4 240.9,219.5 242.2,219.6 243.4,219.6 244.7,219.7 246,219.7 247.2,219.7 248.5,219.8 249.7,219.8 251,219.8 252.2,219.8 253.5,219.9 254.7,219.9 256,219.9 257.3,219.9 258.5,219.9 259.8,219.9 261,219.9 262.3,220 263.5,220 264.8,220 266,220 267.3,220 268.6,220 269.8,220 271.1,220 272.3,220 273.6,220 274.8,220 276.1,220 277.3,220 278.6,220 279.9,220 281.1,220 282.4,220 283.6,220 284.9,220 286.1,220 287.4,220 288.7,220 289.9,220 291.2,220 292.4,220 293.7,220 294.9,220 296.2,220 297.4,220 298.7,220 300,220 301.2,220 302.5,220 303.7,220 305,220 306.2,220 307.5,220 308.7,220 310,220"/><polyline class="c1" points="390.1,220 391.4,220 392.6,219.9 393.9,219.7 395.1,219.5 396.4,219.2 397.6,218.9 398.9,218.5 400.1,218 401.4,217.5 402.7,217 403.9,216.3 405.2,215.6 406.4,214.9 407.7,214.1 408.9,213.2 410.2,212.3 411.4,211.3 412.7,210.2 414,209.1 415.2,207.9 416.5,206.7 417.7,205.4 419,204 420.2,202.6 421.5,201.2 422.8,199.6 424,198 425.3,196.4 426.5,194.7 427.8,192.9 429,191.1 430.3,189.2 431.5,187.2 432.8,185.2 434.1,183.1 435.3,181 436.6,178.8 437.8,176.6 439.1,174.2 440.3,171.9 441.6,169.4 442.8,166.9 444.1,164.4 445.4,161.8 446.6,159.1 447.9,156.4 449.1,153.6 450.4,150.7 451.6,147.8 452.9,144.9 454.1,141.8 455.4,138.7 456.7,135.6 457.9,132.4 459.2,129.1 460.4,125.8 461.7,122.4 462.9,118.9 464.2,115.4 465.4,111.8 466.7,108.2 468,104.5 469.2,100.8 470.5,97 471.7,93.1 473,89.2 474.2,85.2 475.5,81.1 476.7,77 478,72.8 479.3,68.6 480.5,64.3 481.8,60 483,55.6 484.3,51.1 485.5,46.6 486.8,42 488.1,37.3 489.3,32.6"/><text class="t" x="72" y="153.5" text-anchor="start">β = 0,5</text><text class="t" x="185" y="151.6" text-anchor="start">β = 1</text><text class="t" x="172" y="197.2" text-anchor="start">β = 3</text><text class="t" x="425" y="55.3" text-anchor="start">β = 0,5</text><text class="t" x="595" y="145.3" text-anchor="start">β = 1</text><text class="t" x="545" y="45.8" text-anchor="start">β = 3</text></svg><figcaption>Figure 2.2 — Loi de Weibull à deux paramètres : fiabilité R(t) et taux de défaillance λ(t) pour β = 0,5 (jeunesse), β = 1 (exponentielle) et β = 3 (usure). Courbes calculées, axes normalisés par η.</figcaption></figure>


**Exemple (TD1, exercice 2).** Douze transistors testés jusqu'à leur première défaillance totalisent 11 292 h. Avec une loi exponentielle, l'estimateur du maximum de vraisemblance donne :

```
λ̂ = n / Σ tᵢ = 12 / 11 292 ≈ 1,06·10⁻³ h⁻¹       MTTF = 1/λ̂ ≈ 941 h
P(défaillance entre 500 h et 800 h | survie à 500 h) = 1 − exp(−λ̂ · 300) ≈ 0,27
```

La probabilité est la même entre 1 000 h et 1 300 h : la loi exponentielle est **sans mémoire**, la probabilité de défaillance sur un intervalle ne dépend que de sa durée.

## 2.4 Maintenabilité

La maintenabilité M(t) est la probabilité qu'une intervention soit terminée avant *t*. Avec un taux de réparation μ constant, M(t) = 1 − exp(−μt) et MTTR = 1/μ. En pratique, les temps de réparation suivent souvent une loi log-normale : la plupart des interventions sont courtes, et quelques-unes sont très longues (attente de pièces, diagnostic difficile).

La maintenabilité se conçoit dès la conception : accessibilité, modularité, standardisation des pièces, aide au diagnostic, documentation. Elle s'améliore aussi en exploitation : stock de pièces critiques, formation, procédures et GMAO.

## 2.5 Disponibilité

La disponibilité instantanée A(t) tend, pour un bien réparable, vers la **disponibilité asymptotique** :

```
A∞ = MUT / (MUT + MDT) = μ / (λ + μ)        (λ et μ constants)
```

**Exemple (TD1, exercice 8).** Une machine indisponible à t = 0 a A(100 h) = 0,910 et A(200 h) = 0,932. Avec λ et μ constants et A(0) = 0 :

```
A(t) = A∞ (1 − e^(−(λ+μ)t))
A(200) / A(100) = 1 + e^(−100(λ+μ))  ⇒  e^(−100(λ+μ)) = 0,02418  ⇒  λ + μ = 0,0372 h⁻¹
A∞ = 0,910 / (1 − 0,02418) = 0,9325
μ = A∞ (λ + μ) = 0,0347 h⁻¹  ⇒  MTTR ≈ 28,8 h
λ = 0,0372 − 0,0347 = 0,00251 h⁻¹  ⇒  MTBF ≈ 398 h
```

## 2.6 Sécurité et criticité

La sécurité se traite par l'analyse des risques. Un **risque** combine la **gravité** d'un événement redouté et sa **probabilité** (ou fréquence) d'occurrence. La matrice de criticité classe les scénarios et fixe les priorités de traitement :

| Probabilité ↓ / Gravité → | Mineure | Significative | Critique | Catastrophique |
|---|---|---|---|---|
| Fréquente | Moyen | Élevé | Inacceptable | Inacceptable |
| Probable | Faible | Moyen | Élevé | Inacceptable |
| Occasionnelle | Faible | Moyen | Moyen | Élevé |
| Rare | Négligeable | Faible | Moyen | Moyen |

Les seuils de la matrice sont des choix de l'entreprise. Ils doivent être fixés avant l'analyse, pas ajustés après.

## 2.7 Méthodes d'analyse de la SdF

| Méthode | Démarche | Nature | Résultat | Référence |
|---|---|---|---|---|
| APR (analyse préliminaire des risques) | Inductive | Qualitative | Liste des dangers et des situations dangereuses | Cours, chap. 3 |
| AMDEC | Inductive : de la cause vers l'effet | Qualitative et semi-quantitative | Modes de défaillance hiérarchisés par criticité | IEC 60812:2018 |
| Arbre de défaillances / des causes | Déductive : de l'effet redouté vers les causes | Qualitative et quantitative | Coupes minimales, probabilité de l'événement redouté | IEC 61025 |
| Diagramme de succès (MDS) | Structurelle | Quantitative | Fiabilité du système à partir de ses composants | IEC 61078 |
| Espace des états (Markov) | Dynamique | Quantitative | Disponibilité avec réparations, redondance passive, dépendances | IEC 61165 |

### Diagramme de succès (MDS)


<figure class="fig" id="fig-rbd"><svg viewBox="0 0 680 255" role="img" aria-label="Diagrammes de fiabilité série et parallèle" xmlns="http://www.w3.org/2000/svg"><defs><marker id="ar" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path class="arh" d="M0,0 L10,5 L0,10 z"/></marker></defs><text class="tb" x="10" y="22" text-anchor="start">Série : le système fonctionne si tous les blocs fonctionnent</text><line class="ln" x1="20" y1="60" x2="60" y2="60"/><rect class="bx acc" x="60" y="42" width="70" height="36" rx="4"/><text class="tb" x="95" y="64" text-anchor="middle">A</text><line class="ln" x1="130" y1="60" x2="170" y2="60"/><rect class="bx acc" x="170" y="42" width="70" height="36" rx="4"/><text class="tb" x="205" y="64" text-anchor="middle">B</text><line class="ln" x1="240" y1="60" x2="280" y2="60"/><rect class="bx acc" x="280" y="42" width="70" height="36" rx="4"/><text class="tb" x="315" y="64" text-anchor="middle">C</text><line class="ln" x1="350" y1="60" x2="390" y2="60"/><text class="t" x="400" y="65" text-anchor="start">Rs = RA · RB · RC</text><text class="tb" x="10" y="122" text-anchor="start">Parallèle (redondance active) : il suffit qu'un bloc fonctionne</text><line class="ln" x1="20" y1="190" x2="70" y2="190"/><line class="ln" x1="70" y1="150" x2="70" y2="230"/><line class="ln" x1="240" y1="150" x2="240" y2="230"/><line class="ln" x1="240" y1="190" x2="290" y2="190"/><line class="ln" x1="70" y1="150" x2="120" y2="150"/><line class="ln" x1="190" y1="150" x2="240" y2="150"/><rect class="bx acc" x="120" y="134" width="70" height="32" rx="4"/><text class="tb" x="155" y="154" text-anchor="middle">A</text><line class="ln" x1="70" y1="190" x2="120" y2="190"/><line class="ln" x1="190" y1="190" x2="240" y2="190"/><rect class="bx acc" x="120" y="174" width="70" height="32" rx="4"/><text class="tb" x="155" y="194" text-anchor="middle">B</text><line class="ln" x1="70" y1="230" x2="120" y2="230"/><line class="ln" x1="190" y1="230" x2="240" y2="230"/><rect class="bx acc" x="120" y="214" width="70" height="32" rx="4"/><text class="tb" x="155" y="234" text-anchor="middle">C</text><text class="t" x="310" y="186" text-anchor="start">Rp = 1 − (1 − RA)(1 − RB)(1 − RC)</text><text class="tm" x="310" y="206" text-anchor="start">k parmi n identiques : R = Σ C(n,i) Rⁱ (1 − R)ⁿ⁻ⁱ, i ≥ k</text></svg><figcaption>Figure 2.4 — Diagrammes de succès (MDS) : montages série et parallèle, en supposant les composants indépendants.</figcaption></figure>


**Exemples (TD2).**

- Quatre sous-systèmes en série de MTTF 4 500, 3 200, 6 000 et 10 500 h : λₛ = Σ 1/MTTFᵢ ≈ 7,97·10⁻⁴ h⁻¹, soit MTTFₛ ≈ 1 255 h. La fiabilité à 5 000 h n'est que de 1,9 %. **Le système en série est moins fiable que son composant le plus faible.**
- Trois dispositifs en parallèle de fiabilité 0,75 : Rₚ = 1 − 0,25³ ≈ 0,984. Pour atteindre 0,999, il faut n ≥ ln(0,001) / ln(0,25) ≈ 4,98, soit **5 dispositifs**. Pour obtenir 0,99 avec 3 dispositifs, chacun doit avoir R ≥ 1 − 0,01^(1/3) ≈ 0,785.

Pour un diagramme ni série ni parallèle (pont), on utilise la méthode des **chemins de succès** et des **coupes minimales**, ou la **décomposition par probabilités totales** sur un composant pivot.

### Arbre de défaillances

L'arbre part de l'**événement redouté** et le décompose, par des portes logiques ET / OU, jusqu'aux **événements de base**. Une **coupe minimale** est un ensemble minimal d'événements de base dont la réalisation simultanée entraîne l'événement redouté. Pour des événements indépendants et rares :

```
P(sortie d'une porte ET) = Π P(eᵢ)
P(sortie d'une porte OU) = 1 − Π (1 − P(eᵢ)) ≈ Σ P(eᵢ)
```


<figure class="fig" id="fig-add"><svg viewBox="0 0 680 290" role="img" aria-label="Exemple d'arbre de défaillances d'une pompe" xmlns="http://www.w3.org/2000/svg"><defs><marker id="ar" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path class="arh" d="M0,0 L10,5 L0,10 z"/></marker></defs><rect class="bx strong" x="220" y="6" width="240" height="36" rx="4"/><text class="tb" x="340" y="20.5" text-anchor="middle">Événement redouté :</text><text class="tb" x="340" y="35.5" text-anchor="middle">la pompe ne débite pas</text><line class="ln" x1="340" y1="42" x2="340" y2="56"/><path class="gate" d="M324,86 Q340,70 356,86 Q354,64 340,54 Q326,64 324,86 z"/><text class="tg" x="360" y="78" text-anchor="start">OU</text><path class="ln" d="M340,86 V96 H170 V110 M340,96 H510 V110"/><rect class="bx" x="80" y="110" width="180" height="34" rx="4"/><text class="t" x="170" y="131" text-anchor="middle">Moteur à l'arrêt</text><rect class="bx" x="420" y="110" width="180" height="34" rx="4"/><text class="t" x="510" y="131" text-anchor="middle">Circuit obstrué</text><line class="ln" x1="170" y1="144" x2="170" y2="156"/><path class="gate" d="M154,186 Q170,170 186,186 Q184,164 170,154 Q156,164 154,186 z"/><text class="tg" x="190" y="178" text-anchor="start">OU</text><line class="ln" x1="510" y1="144" x2="510" y2="156"/><path class="gate" d="M494,186 V168 A16,16 0 0 1 526,168 V186 z"/><text class="tg" x="510" y="180" text-anchor="middle">ET</text><path class="ln" d="M170,186 V196 H95 V210 M170,196 H245 V210 M510,186 V196 H435 V210 M510,196 H585 V210"/><circle class="basic" cx="95" cy="246" r="36"/><text class="ts" x="95" y="243" text-anchor="middle">Perte</text><text class="ts" x="95" y="256" text-anchor="middle">alimentation</text><circle class="basic" cx="245" cy="246" r="36"/><text class="ts" x="245" y="243" text-anchor="middle">Défaut</text><text class="ts" x="245" y="256" text-anchor="middle">moteur</text><circle class="basic" cx="435" cy="246" r="36"/><text class="ts" x="435" y="243" text-anchor="middle">Filtre</text><text class="ts" x="435" y="256" text-anchor="middle">colmaté</text><circle class="basic" cx="585" cy="246" r="36"/><text class="ts" x="585" y="243" text-anchor="middle">Dérivation</text><text class="ts" x="585" y="256" text-anchor="middle">indisponible</text></svg><figcaption>Figure 2.5 — Arbre de défaillances d'une installation de pompage (exemple pédagogique). Coupes minimales : {perte d'alimentation}, {défaut moteur}, {filtre colmaté, dérivation indisponible}.</figcaption></figure>


Une coupe d'ordre 1, c'est-à-dire un seul événement de base, est un point faible unique. C'est la première cible des actions de fiabilisation (redondance, surveillance).

### AMDEC

L'AMDEC (analyse des modes de défaillance, de leurs effets et de leur criticité) recense, pour chaque composant, ses modes de défaillance, leurs causes, leurs effets et leurs moyens de détection, puis les hiérarchise. Elle est décrite par l'IEC 60812:2018 et par le guide pratique AFNOR [2], [3]. Les étapes sont les suivantes :

1. Constituer le groupe de travail (maintenance, production, méthodes) et définir le système et ses limites.
2. Réaliser l'**analyse fonctionnelle** : décomposer le système et lister les fonctions de chaque élément.
3. Pour chaque élément, identifier les modes de défaillance, leurs causes, leurs effets et la manière de les détecter.
4. Coter la **fréquence** F, la **gravité** G et la **non-détection** D (souvent sur une échelle de 1 à 4 ou de 1 à 10), puis calculer la criticité **C = F × G × D**.
5. Proposer des actions pour les modes dont la criticité dépasse le seuil retenu, puis recoter après action.

**Exemple pédagogique : extrait d'AMDEC d'une électropompe** (cotation de 1 à 4 ; les valeurs illustrent la méthode et devront être justifiées par un retour d'expérience réel).

| Élément | Mode | Cause | Effet | Détection actuelle | F | G | D | C |
|---|---|---|---|---|---|---|---|---|
| Roulement | Grippage | Défaut de lubrification | Arrêt de la pompe | Aucune (ronde visuelle) | 2 | 3 | 4 | 24 |
| Garniture mécanique | Fuite | Usure des faces | Perte de fluide, risque environnemental | Contrôle visuel hebdomadaire | 3 | 2 | 2 | 12 |
| Impulseur | Érosion | Cavitation | Baisse de débit | Mesure de débit | 2 | 2 | 3 | 12 |
| Moteur, stator | Court-circuit | Dégradation de l'isolant | Arrêt, déclenchement de la protection | Protection électrique | 1 | 4 | 3 | 12 |

La note D est celle qu'une surveillance conditionnelle fait baisser. Le projet PRJ-01 du portfolio cherche justement à mesurer cette détectabilité sur des données réelles.

### Méthode de l'espace des états (Markov)

Quand les réparations, les redondances passives ou les dépendances entre composants interviennent, on modélise le système par un **graphe d'états** dont les transitions sont pondérées par les taux λ et μ. En régime permanent, la **conservation des flux** donne, pour chaque état, flux entrant = flux sortant. On en déduit les probabilités d'état, la disponibilité asymptotique, puis MTBF, MUT et MTTR (TD3).


<figure class="fig" id="fig-markov"><svg viewBox="0 0 680 240" role="img" aria-label="Graphe de Markov à deux états et disponibilité instantanée" xmlns="http://www.w3.org/2000/svg"><defs><marker id="ar" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path class="arh" d="M0,0 L10,5 L0,10 z"/></marker></defs><circle class="state up" cx="70" cy="120" r="38"/><circle class="state dn" cx="250" cy="120" r="38"/><text class="tb" x="70" y="116" text-anchor="middle">État 1</text><text class="ts" x="70" y="133" text-anchor="middle">marche</text><text class="tb" x="250" y="116" text-anchor="middle">État 2</text><text class="ts" x="250" y="133" text-anchor="middle">panne</text><path class="arw" d="M100,96 Q160,60 220,96" marker-end="url(#ar)"/><path class="arw" d="M220,144 Q160,180 100,144" marker-end="url(#ar)"/><text class="tb" x="160" y="64" text-anchor="middle">λ</text><text class="tb" x="160" y="192" text-anchor="middle">μ</text><line class="gr" x1="380" x2="640" y1="200" y2="200"/><line class="gr" x1="380" x2="640" y1="115" y2="115"/><line class="gr" x1="380" x2="640" y1="30" y2="30"/><line class="ax" x1="380" y1="200" x2="640" y2="200"/><line class="ax" x1="380" y1="30" x2="380" y2="200"/><text class="tm" x="380" y="216" text-anchor="middle">0</text><text class="tm" x="466.7" y="216" text-anchor="middle">20</text><text class="tm" x="553.3" y="216" text-anchor="middle">40</text><text class="tm" x="640" y="216" text-anchor="middle">60</text><text class="tm" x="374" y="204" text-anchor="end">0,80</text><text class="tm" x="374" y="119" text-anchor="end">0,90</text><text class="tm" x="374" y="34" text-anchor="end">1,00</text><text class="tm" x="640" y="234" text-anchor="end">t (h)</text><text class="tm" x="380" y="22" text-anchor="start">A(t)</text><line class="dim dash" x1="380" y1="107.3" x2="640" y2="107.3"/><polyline class="c1 thick" points="380,30 382.2,34.2 384.4,38.1 386.6,41.8 388.7,45.4 390.9,48.7 393.1,51.9 395.3,54.9 397.5,57.7 399.7,60.4 401.8,62.9 404,65.3 406.2,67.6 408.4,69.7 410.6,71.7 412.8,73.6 415,75.5 417.1,77.2 419.3,78.8 421.5,80.3 423.7,81.8 425.9,83.2 428.1,84.5 430.3,85.7 432.4,86.9 434.6,88 436.8,89 439,90 441.2,90.9 443.4,91.8 445.5,92.6 447.7,93.4 449.9,94.2 452.1,94.9 454.3,95.5 456.5,96.2 458.7,96.8 460.8,97.3 463,97.9 465.2,98.4 467.4,98.9 469.6,99.3 471.8,99.7 473.9,100.2 476.1,100.5 478.3,100.9 480.5,101.2 482.7,101.6 484.9,101.9 487.1,102.2 489.2,102.4 491.4,102.7 493.6,103 495.8,103.2 498,103.4 500.2,103.6 502.4,103.8 504.5,104 506.7,104.2 508.9,104.3 511.1,104.5 513.3,104.7 515.5,104.8 517.6,104.9 519.8,105.1 522,105.2 524.2,105.3 526.4,105.4 528.6,105.5 530.8,105.6 532.9,105.7 535.1,105.8 537.3,105.8 539.5,105.9 541.7,106 543.9,106.1 546.1,106.1 548.2,106.2 550.4,106.3 552.6,106.3 554.8,106.4 557,106.4 559.2,106.5 561.3,106.5 563.5,106.5 565.7,106.6 567.9,106.6 570.1,106.7 572.3,106.7 574.5,106.7 576.6,106.7 578.8,106.8 581,106.8 583.2,106.8 585.4,106.9 587.6,106.9 589.7,106.9 591.9,106.9 594.1,106.9 596.3,107 598.5,107 600.7,107 602.9,107 605,107 607.2,107 609.4,107 611.6,107.1 613.8,107.1 616,107.1 618.2,107.1 620.3,107.1 622.5,107.1 624.7,107.1 626.9,107.1 629.1,107.1 631.3,107.1 633.4,107.1 635.6,107.2 637.8,107.2 640,107.2"/><text class="t" x="631.3" y="123.3" text-anchor="end">A∞ = μ/(λ+μ) ≈ 0,909</text></svg><figcaption>Figure 2.6 — Méthode de l'espace des états : graphe à deux états et disponibilité instantanée A(t) d'un composant réparable démarrant en marche, calculée pour λ = 0,01 h⁻¹ et μ = 0,1 h⁻¹ (valeurs d'illustration).</figcaption></figure>


## 2.8 Estimer les indices à partir des données

### Sources de données

| Source | Contenu | Points forts | Limites |
|---|---|---|---|
| Banques de données (OREDA, IEEE Std 500, MIL-HDBK-217, NPRD) | Taux de défaillance génériques par famille de matériel | Disponibles avant toute exploitation | Conditions d'usage différentes des vôtres |
| Essais de fiabilité | Durées de vie mesurées en laboratoire, éventuellement accélérées | Conditions maîtrisées | Coûteux ; extrapolation des essais accélérés |
| Retour d'expérience (REX) et GMAO | Historique réel des pannes et des réparations | Représentatif du site | Données incomplètes, **censurées** (équipements encore en service) |

Une donnée est **censurée à droite** quand le bien est encore en service à la fin de l'observation : on sait seulement que sa durée de vie dépasse le temps observé. Ignorer ces données biaise la fiabilité vers le bas.

### Méthodes non paramétriques

Elles ne supposent aucune loi. L'estimateur de **Kaplan-Meier** gère la censure :

```
R̂(t) = Π_{tᵢ ≤ t} (1 − dᵢ / nᵢ)        dᵢ : défaillances en tᵢ, nᵢ : biens encore à risque juste avant tᵢ
Ĥ(t) = Σ_{tᵢ ≤ t} dᵢ / nᵢ                estimateur de Nelson-Aalen du taux de hasard cumulé
```

Le lissage par noyaux permet ensuite d'estimer une densité ou un taux de défaillance continu. Ces trois méthodes sont implémentées dans les scripts MATLAB et Python fournis avec le cours.

### Méthodes paramétriques : ajustement d'une loi de Weibull

**Moindres carrés (MCO).** La fiabilité de Weibull se linéarise :

```
ln(−ln(1 − F(t))) = β ln t − β ln η
F(tᵢ) ≈ (i − 0,3) / (n + 0,4)            rangs médians de Bernard
```

On trace Y = ln(−ln(1 − F)) en fonction de X = ln t. La pente de la droite donne β, et l'ordonnée à l'origine donne η.

**Maximum de vraisemblance (MV).** On cherche les paramètres qui maximisent la probabilité d'avoir observé les données. Il intègre naturellement les données censurées et donne des intervalles de confiance. C'est la méthode recommandée quand l'échantillon est suffisant.

**Exemple (TD1, exercice 4).** Seize durées de vie relevées sur un système :


<figure class="fig" id="fig-weibull_plot"><svg viewBox="0 0 640 290" role="img" aria-label="Diagramme de Weibull des 16 durées de vie du TD1" xmlns="http://www.w3.org/2000/svg"><defs><marker id="ar" viewBox="0 0 10 10" refX="9" refY="5" markerWidth="7" markerHeight="7" orient="auto-start-reverse"><path class="arh" d="M0,0 L10,5 L0,10 z"/></marker></defs><line class="gr" x1="70" x2="610" y1="230.5" y2="230.5"/><line class="gr" x1="70" x2="610" y1="182.7" y2="182.7"/><line class="gr" x1="70" x2="610" y1="135" y2="135"/><line class="gr" x1="70" x2="610" y1="87.3" y2="87.3"/><line class="gr" x1="70" x2="610" y1="39.5" y2="39.5"/><line class="ax" x1="70" y1="240" x2="610" y2="240"/><line class="ax" x1="70" y1="30" x2="70" y2="240"/><text class="tm" x="151" y="256" text-anchor="middle">7,5</text><text class="tm" x="286" y="256" text-anchor="middle">8</text><text class="tm" x="421" y="256" text-anchor="middle">8,5</text><text class="tm" x="556" y="256" text-anchor="middle">9</text><text class="tm" x="64" y="234.5" text-anchor="end">-3</text><text class="tm" x="64" y="186.7" text-anchor="end">-2</text><text class="tm" x="64" y="139" text-anchor="end">-1</text><text class="tm" x="64" y="91.3" text-anchor="end">0</text><text class="tm" x="64" y="43.5" text-anchor="end">1</text><text class="tm" x="610" y="274" text-anchor="end">ln t  (t en heures)</text><text class="tm" x="70" y="22" text-anchor="start">ln(−ln(1 − F))</text><polyline class="c1" points="83.5,210.3 596.5,30"/><circle class="dot2" cx="103.4" cy="236.8" r="4.5"/><circle class="dot2" cx="114.3" cy="192.9" r="4.5"/><circle class="dot2" cx="128.9" cy="169.1" r="4.5"/><circle class="dot2" cx="260.2" cy="152.4" r="4.5"/><circle class="dot2" cx="265.8" cy="139.1" r="4.5"/><circle class="dot2" cx="299.3" cy="127.9" r="4.5"/><circle class="dot2" cx="351.3" cy="118" r="4.5"/><circle class="dot2" cx="367.5" cy="109" r="4.5"/><circle class="dot2" cx="388.3" cy="100.6" r="4.5"/><circle class="dot2" cx="428.6" cy="92.6" r="4.5"/><circle class="dot2" cx="437.4" cy="84.6" r="4.5"/><circle class="dot2" cx="496.6" cy="76.6" r="4.5"/><circle class="dot2" cx="500.4" cy="68.3" r="4.5"/><circle class="dot2" cx="519.8" cy="59.1" r="4.5"/><circle class="dot2" cx="535.9" cy="48.2" r="4.5"/><circle class="dot2" cx="568" cy="32.5" r="4.5"/><text class="tb" x="97" y="46.7" text-anchor="start">Droite des moindres carrés : pente β ≈ 1,99</text><text class="t" x="97" y="65.8" text-anchor="start">η = exp(−ordonnée à l'origine / β) ≈ 5 150 h</text></svg><figcaption>Figure 2.3 — Diagramme de Weibull linéarisé des 16 durées de vie de l'exercice 4 du TD1. Rangs médians de Bernard F = (i − 0,3)/(n + 0,4). Points et droite calculés à partir des données de l'énoncé.</figcaption></figure>


```
β ≈ 1,99    η ≈ 5 150 h    (coefficient de détermination r² ≈ 0,95)
R(2 500 h) = exp(−(2 500 / 5 150)^1,99) ≈ 0,79
λ(2 500 h) = (β/η)(2 500/η)^(β−1) ≈ 1,9·10⁻⁴ h⁻¹
MTTF = η Γ(1 + 1/β) ≈ 4 560 h
```

β ≈ 2 indique une **défaillance par usure** : une maintenance préventive (systématique ou conditionnelle) est justifiée. À 2 500 h, il reste environ 21 % de risque de défaillance, ce qui permet de choisir une périodicité en fonction du risque accepté.

### Approche bayésienne

Quand les données sont rares, l'approche bayésienne combine une **connaissance a priori**, issue d'une banque de données ou de l'avis d'experts, avec les observations du site. On obtient une **loi a posteriori** des paramètres, mise à jour à chaque nouvelle défaillance. Elle est présentée au chapitre 8 du cours.

## Références

<ol class="refs">
<li>[1] A. Villemeur, <i>Sûreté de fonctionnement des systèmes industriels : fiabilité, facteurs humains, informatisation</i>. Paris : Eyrolles, 1988.</li>
<li>[2] IEC, <i>IEC 60812:2018 — Failure modes and effects analysis (FMEA and FMECA)</i>, 3ᵉ éd., Genève : IEC, 2018.</li>
<li>[3] G. Landy, <i>AMDEC : guide pratique</i>, 2ᵉ éd. La Plaine Saint-Denis : AFNOR, 2007.</li>
<li>[4] M. Rausand et A. Høyland, <i>System Reliability Theory: Models, Statistical Methods, and Applications</i>, 2ᵉ éd. Hoboken, NJ : Wiley, 2004.</li>
<li>[5] IEC, <i>IEC 61025:2006 — Fault tree analysis (FTA)</i> ; <i>IEC 61078:2016 — Reliability block diagrams</i> ; <i>IEC 61165:2006 — Application of Markov techniques</i>. Genève : IEC.</li>
<li>[6] F. Ben Hmida, <i>Sûreté de fonctionnement</i>, support de cours (chap. 0 à 8) et TD 1 à 3.</li>
<li>[7] F. Ben Hmida, <i>Estimation des indices FMDS</i>, support de formation, oct. 2025.</li>
<li>[8] E. L. Kaplan et P. Meier, « Nonparametric estimation from incomplete observations », <i>J. Amer. Statist. Assoc.</i>, vol. 53, n° 282, p. 457-481, 1958.</li>
</ol>
