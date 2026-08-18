# ROADMAP — Le Colosse et l'Oasis

> Court-métrage généré localement · ComfyUI · ~45 secondes

---

## 🧭 Si tu es perdu, lis ça

**Règle unique : tu travailles sur la phase la plus basse qui n'est pas encore validée.**

Pas celle qui te fait envie. Pas celle qui est gratifiante. La plus basse non validée.
Chaque phase a une **porte de sortie** : une condition binaire, vraie ou fausse. Tant qu'elle est fausse, tu ne passes pas à la suite.

L'éparpillement sur ce type de projet a toujours la même cause : générer un plan magnifique en phase 5 alors que la phase 2 n'est pas finie, puis découvrir en phase 6 que le personnage a trois designs différents.

---

## 🔒 Décisions figées

Ne se rediscutent pas. Si une hésitation survient, on relit ce tableau.

| Élément | Valeur |
|---|---|
| Taille du colosse | **60 m** → 1 pas / 4 s · empreinte 12 m · poussière retombe en 3 s |
| Doigts | **4**, jamais 5 |
| Visage | **Aucun**. Heaume vide, une lentille. Émotion portée par l'inclinaison du cou |
| Résolution keyframes | **1152 × 640** |
| Résolution génération vidéo | **768 × 512**, puis spatial upscaler ×2 |
| Position du soleil | **Rasante, fin de journée**, identique sur tous les plans désert |
| Type de désert | **Mer de dunes**, épurée. Les repères d'échelle sont des débris mécaniques, pas de la végétation |
| Le monde | Ancienne zone de guerre. Les débris sont **le même modèle** que le colosse — il est un soldat parmi d'autres |
| Signature du colosse | **Bras droit réparé** avec des pièces dépareillées : rouille plus claire, plaque mal alignée. C'est ce qui le distingue des carcasses |
| Densité des débris | Décroissante : 3-4 (P10) → 1 (P20) → 1 à l'horizon (P30) → **zéro dans l'oasis** |
| Palette désert | Ocre chaud · ombres violet-bleu (jamais gris) · rouille = seule couleur saturée |
| Palette oasis | Verts froids saturés · ombres chaudes (inversion assumée) |
| Durée cible | 45 s · ~10 plans |
| Style | Cel animation peinte (pas vectorielle) — garder du grain, LTX en a besoin |

---

## 📊 Suivi

| Phase | Statut | Porte de sortie |
|---|---|---|
| 0 · Socle technique | ⬜ | Un clip de 5 s généré 2× d'affilée sans crash |
| 1 · Scénario | ⬜ | Un découpage écrit qui tient sur une page |
| 2 · Character design | ⬜ | 2 masters validés + fiche des mains réussie |
| 3 · Décor & props | ⬜ | 2 plates validées (désert, oasis) + fiche d'échelle |
| 4 · Storyboard | ⬜ | 10 vignettes lisibles, durées notées |
| 5 · First/Last frames | ⬜ | ~20 images qui racontent l'histoire en fixe |
| 6 · Mouvement | ⬜ | Tous les plans en v1, montables bout à bout |
| 7 · Finitions | ⬜ | Un fichier exporté qu'on peut montrer |

---

# PHASE 0 — Socle technique

**Objectif.** Que l'outil ne soit plus jamais le sujet.

**À faire**
- ComfyUI nightly, lancé avec `--disable-pinned-memory`
  (si crash au VAEDecode, ajouter `--disable-async-offload`)
- Windows : pagefile fixe **64 Go minimum**
- Modèles en place : Z-Image Turbo · Qwen Image Edit · LTX 2.3 (`dev-fp8` + `distilled-fp8`) · encodeur Gemma · spatial upscaler ×2
- Nœuds : ComfyUI-GGUF · Frame-Interpolation (RIFE) · controlnet_aux · VideoHelperSuite · dynamicprompts · rgthree
- DaVinci Resolve installé
- Arborescence projet créée (voir annexe)

**Mesure à noter ici :** temps de génération d'un clip de 5 s = `______`
Ce chiffre dicte tout le planning. À 3 min/clip on itère librement ; à 20 min on planifie.

**🚪 Porte de sortie** — un clip généré de bout en bout, **deux fois de suite**, sans OOM.

**⚠️ Piège** — vouloir optimiser la vitesse avant d'avoir mesuré. Mesure d'abord.

---

# PHASE 1 — Scénario

**Objectif.** Décrire en texte tout ce qu'on verra. Aucune image. C'est ce document qui déterminera quels assets méritent d'être produits.

**Format d'une fiche de plan** (une par plan, ~10 au total) :

```
PLAN 30
Durée      : 6 s
Valeur     : plan large
Sujet      : le colosse, de dos, de très loin
Décor      : désert, ligne de crête, soleil rasant derrière
Lumière    : contre-jour, silhouette presque noire
Mouvement  : il traverse le cadre très lentement, de gauche à droite,
             parcourt à peine un dixième de la largeur
Son        : un impact sourd toutes les 4 s, très lointain, presque un souffle
Intention  : le désert est plus grand que lui
Assets req.: colosse (silhouette dos) · plate désert crête
```

Le champ **Mouvement** est le plus important : c'est lui qui deviendra ton prompt LTX en phase 6. Écris-le comme une instruction, pas comme une image.
Le champ **Assets requis** produit automatiquement ta liste de courses pour les phases 2 et 3.

**Rappels narratifs à intégrer**
- Les oiseaux annoncent l'oasis — le géant les suit. Cause → effet, jamais coïncidence.
- Un temps d'hésitation avant l'agenouillement : il s'immobilise, la tête s'incline. C'est là qu'il devient un personnage.
- Le plan final se fait **en deux plans coupés** : (a) les doigts qui s'écartent, jamais la main entière ; (b) insert serré sur les deux humains. Jamais les deux sujets nets dans le même cadre.
- Ironie de rouille : ce qui le détruit (l'eau) est ce qui sauve les humains. Une goutte de condensation en dernier plan.

**📦 Livrable** — `SCENARIO.md`, une fiche par plan.

**🚪 Porte de sortie** — le découpage tient sur une page, le total des durées fait ~45 s, et chaque plan a une intention formulable en une phrase.

**⚠️ Piège** — écrire des mouvements de caméra spectaculaires. LTX gère mal les grands déplacements. Privilégie : caméra fixe, panoramique lent, léger travelling avant. Le mouvement doit être dans le sujet, pas dans l'objectif.

---

# PHASE 2 — Character design

**Objectif.** Deux sujets verrouillés : le colosse, et les deux humains.
Le colosse mérite un traitement complet ; les humains apparaissent 3 secondes et méritent une seule image.

## Workflows

### `CD-01_Refine` ⭐ *le workflow le plus réutilisable du projet*

La forme de départ ne se génère pas : elle se griffonne en deux minutes, ou vient d'une photo, ou d'un collage. Le rôle du workflow est de **l'habiller**, pas de l'inventer.

```
LoadImage → ImageScale (côté long 1024) → VAEEncode
→ KSampler (Z-Image, 8 steps, euler_ancestral, denoise variable)
→ VAEDecode → SaveImage
```

Un seul réglage compte, le **denoise** :

| Entrée | Denoise | Ce qui est conservé |
|---|---|---|
| Griffonnage grossier | 0.75 – 0.85 | La grande masse uniquement |
| Croquis lisible | 0.55 – 0.70 | La structure et les proportions |
| Photo / composite | 0.35 – 0.50 | Tout, on ne change que le style |

Si un denoise élevé mange trop la structure : brancher un **ControlNet Canny ou Depth** depuis l'image d'entrée. Tu montes alors le denoise sans perdre la forme.

Il resservira partout : les props, les plates de décor, et surtout les composites de la phase 5 — `KF-01_Compose` n'est que ce workflow avec une entrée différente.

### `UTIL-01_Silhouette`
`LoadImage` → `ImageQuantize (colors = 2)` → `PreviewImage`

Pas un générateur : un **contrôle qualité**. À passer sur le master, sur les plates, sur chaque keyframe. Si la forme ne se lit plus en aplat noir, elle ne se lira pas non plus dans le plan large.
(Avec `controlnet_aux`, le préprocesseur **Binary** fait un vrai seuillage réglable, plus propre.)

### `CD-02_MasterRef`
La sortie de CD-01 retenue → passes Qwen Image Edit pour correction chirurgicale (« retire le cinquième doigt », « ajoute de la rouille sur les épaules », « assombris le heaume »).
**Sortie : une seule image, verrouillée, jamais régénérée.** Tout le reste en découle.

### `CD-03_Turnaround`
Étage 1 — cohérence : QIE, **une seule génération** en ratio large (2048×768), prompt de type *model sheet, 4 vues côte à côte*. Générer les vues ensemble force leur cohérence mutuelle.
Étage 2 — résolution : `ImageCrop` ×4 → `ImageScale` ×2 → QIE en refine léger, master en seconde référence.

> ⛔ **Jamais en cascade.** master → face → profil → dos en chaîne accumule la dérive. Toujours repartir du master.

### `CD-04_DetailSheet`
`LoadImage(master)` → `ImageCrop(zone)` → `ImageScale ×2` → QIE (« extreme close-up of… ») → `SaveImage`
**Exception main** : le prompt ne donnera jamais 4 doigts de façon fiable. Dessiner une forme à 4 doigts dans Krita → Canny/Depth ControlNet.

### `CD-05_PoseSheet`
Une image par pose clé identifiée en phase 1 : marche (appui / suspension), arrêt, agenouillement, mains tendues.
QIE depuis le master + prompt de pose. Ces images serviront directement de first/last frames en phase 5.

**📦 Livrables**
- `colosse_master.png` (verrouillé)
- Turnaround 4 vues
- Fiches détail : main ouverte · tête · pied + empreinte
- 4–6 poses clés
- `humains_master.png`

**🚪 Porte de sortie** — la fiche des mains est réussie (4 doigts, paume large et plate), et le master passe le test de lisibilité en aplat noir.

**⚠️ Piège** — produire des vues qui n'apparaissent dans aucun plan. Relire le champ *Assets requis* du scénario avant de lancer quoi que ce soit.

---

# PHASE 3 — Décor & props

**Objectif.** Deux environnements cohérents, avec leur lumière verrouillée.

## Workflows

### `ENV-01_Plate`
Génération d'un lieu à un moment donné. Structure identique à CD-02, mais le master est ici une **plaque de décor sans sujet** — le colosse sera composité par-dessus en phase 5.
Produire pour chaque lieu : un plan large, un plan moyen, un détail.

### `ENV-02_TimeOfDay`
`LoadImage(plate)` → QIE (« same location, same composition, at dawn / at dusk / under harsh noon light »).
Sert à tester la palette, pas à produire du final. Une fois le moment choisi (soleil rasant), on n'y revient plus.

### `ENV-03_Prop`
Éléments isolés sur fond neutre, détourables : palmier, arbre fruitier, rocher, oiseau, plan d'eau.
Ils alimenteront les composites de la phase 5.

### `ENV-04_ScaleSheet` ⭐
**Le livrable le plus important de cette phase.** Le colosse à côté d'un palmier, puis à côté d'une silhouette humaine, à l'échelle exacte (60 m).
C'est la référence contre laquelle tous les cadrages seront vérifiés. Sans elle, l'échelle dérivera de plan en plan sans que tu le remarques.

**📦 Livrables**
- Plate désert (large / moyen / détail)
- Plate oasis (de loin / de près)
- 4–6 props détourés
- La fiche d'échelle

**🚪 Porte de sortie** — les deux plates ont la même direction de lumière que celle figée en tête de document, et la fiche d'échelle existe.

**⚠️ Piège** — générer des décors somptueux et détaillés. Un décor de fond doit être **simple** : il sera derrière un colosse de 60 m, et LTX doit pouvoir l'animer sans le faire bouillir.

---

# PHASE 4 — Storyboard

**Objectif.** Traduire chaque fiche de plan en une image de cadrage. Pas de beauté ici, uniquement de la composition.

**Méthode.** Vignettes dessinées à la main, même très grossières. Trois raisons :
1. C'est plus rapide que de négocier un cadrage avec un modèle
2. Le cadrage est une décision, pas une génération
3. Ces vignettes deviennent des **depth/lineart maps** exploitables en ControlNet à la phase 5

**Ce qu'une vignette doit contenir**
- Où est le sujet dans le cadre (et surtout : quelle fraction du cadre il occupe)
- La ligne d'horizon et la hauteur de caméra
- Une flèche pour le mouvement
- La durée en secondes, écrite dessus

**Sur l'échelle** — le rappel qui vaut tout le reste : un colosse ne se lit pas sans étalon dans le cadre. Chaque plan large doit contenir un repère de taille (oiseaux, panache de poussière, trace de pas, palmier).

**📦 Livrable** — 10 vignettes numérotées, scannées ou photographiées, dans `storyboard/`.

**🚪 Porte de sortie** — un tiers qui regarde les 10 vignettes dans l'ordre comprend l'histoire.

**⚠️ Piège** — vouloir automatiser cette phase. C'est la moins automatisable et la plus décisive. Une heure de crayon économise dix heures de GPU.

---

# PHASE 5 — First / Last frames

**Objectif.** Fusionner personnages, décors et cadrages en images finales. À la sortie, l'histoire se comprend déjà en fixe.

## Workflow `KF-01_Compose`

C'est le workflow le moins sexy et le plus important du projet.

```
1. Composite MANUEL (Krita / Photopea)
   plate de décor + découpe du sujet à la bonne échelle + props
   → même si c'est laid, l'échelle se décide à la souris

2. img2img Z-Image, denoise 0.40–0.50
   → harmonise lumière, grain, style

3. QIE en retouche ciblée si nécessaire

4. Vérification via UTIL-01 → la silhouette se lit-elle toujours ?
```

C'est `CD-01_Refine` avec un composite en entrée. Même graphe, denoise plus bas.
Optionnel : ControlNet depth depuis la vignette de storyboard pour verrouiller le cadrage à l'étape 2.

## Workflow `KF-02_Pair`

Pour chaque plan, produire la **première et la dernière frame** :
- Résolution strictement identique (1152 × 640)
- Même lumière, même palette
- L'écart entre les deux définit le mouvement : sur un plan de marche, le colosse doit avoir avancé d'une longueur crédible, pas traversé le cadre

**📦 Livrable** — ~20 images dans `keyframes/`, nommées `s30_wide-desert_first.png` / `s30_wide-desert_last.png`

**🚪 Porte de sortie** — les 20 images alignées côte à côte racontent l'histoire, et deux plans consécutifs ont visiblement la même lumière.

**⚠️ Piège** — un écart trop grand entre first et last. LTX interpolera n'importe quoi pour combler, et « n'importe quoi » ressemble généralement à du morphing.

---

# PHASE 6 — Mouvement

**Objectif.** Maintenant seulement, la vidéo. Le modèle a toutes les cartes : deux frames de référence, un cadrage validé, une description de mouvement écrite en phase 1.

## Workflow `VID-01_FLF2V`

```
Checkpoint : ltx-2.3-22b-distilled-fp8
Résolution : 768 × 512
first_strength : 0.95 – 1.0
last_strength  : 0.70 – 0.80   ← mouvement plus naturel qu'à 1.0
Prompt : le champ "Mouvement" de la fiche de plan, tel quel
```

## Workflow `VID-02_UnionControl` (optionnel, fort levier)

IC-LoRA Union Control : guidance structurelle depuis une vidéo de référence (depth / Canny / pose).

Un pantin de cubes animé dans Blender, exporté en depth map, et LTX habille ça de ton colosse. Le timing du pas, la cadence, la masse — plus rien n'est laissé au hasard du prompt.
À réserver aux 3 plans de marche. C'est ce qui sépare « robot IA qui glisse » de « machine de 60 tonnes ».

## Méthode

1. **Tous les plans en v1 d'abord**, même moches
2. Monter l'animatic dans Resolve, regarder en entier
3. **Seulement là**, identifier les 3 plans qui méritent dix essais

**📦 Livrable** — 10 clips dans `shots/`, versionnés `s30_wide-desert_v01.mp4`

**🚪 Porte de sortie** — un animatic complet, montable bout à bout, qu'on peut regarder en entier.

**⚠️ Piège** — perfectionner le plan 1 avant d'avoir généré le plan 10. Le montage révèle toujours que certains plans sont inutiles ; les perfectionner avant est du temps jeté.

---

# PHASE 7 — Finitions

**Objectif.** Transformer 10 générations disparates en un objet cohérent.

**Ordre des opérations**
1. **Upscale** — spatial upscaler ×2 sur les plans retenus uniquement
2. **Interpolation RIFE** — générer en 16 fps, interpoler vers 48–60. C'est ici que la lourdeur des pas se fabrique. Essentiel.
3. **Montage** (Resolve) — le rythme, les points de coupe, les respirations
4. **Étalonnage** — la passe qui unifie tout. C'est elle qui fait qu'on ne voit plus 10 générations mais un film. Ne pas la sauter.
5. **Son** — un sub-bass par impact de pas, du vent, puis le contraste absolu à l'arrivée de l'oasis : eau et oiseaux. Le poids d'un géant est à 50 % dans le son.

**📦 Livrable** — un fichier exporté.

**🚪 Porte de sortie** — tu peux le montrer à quelqu'un sans dire « alors, imagine que… ».

---

# Annexe A — Arborescence

```
colosse/
├── ROADMAP.md
├── SCENARIO.md
├── bible/
│   ├── colosse_master.png
│   ├── colosse_turnaround_*.png
│   ├── colosse_detail_main.png
│   ├── colosse_pose_*.png
│   └── humains_master.png
├── env/
│   ├── plate_desert_*.png
│   ├── plate_oasis_*.png
│   ├── props_*.png
│   └── scale_sheet.png
├── storyboard/
│   └── vignette_s*.png
├── keyframes/
│   ├── s30_wide-desert_first.png
│   └── s30_wide-desert_last.png
├── shots/
│   └── s30_wide-desert_v01.mp4
├── workflows/          → sous git
└── edit/               → projet Resolve
```

**Numérotation des plans par 10** (s10, s20, s30…) : tu vas insérer des plans en cours de route.

---

# Annexe B — Rappel technique

| Usage | Modèle |
|---|---|
| Image de base | Z-Image Turbo — 8 steps, cfg 1.0, euler_ancestral |
| Cohérence / édition | Qwen Image Edit — ~16 s/image |
| Vidéo I2V, T2V | `ltx-2.3-22b-dev-fp8` |
| Vidéo FLF2V | `ltx-2.3-22b-distilled-fp8` |
| Upscale | `ltx-2.3-spatial-upscaler-x2` |

**Lancement :** `--disable-pinned-memory` (+ `--disable-async-offload` si crash au VAEDecode)

**Hygiène mémoire :** cliquer *Free model and node cache* entre un workflow image et un workflow vidéo. Ne jamais mettre les deux dans le même graphe.

**Nœuds :** ComfyUI-GGUF · Frame-Interpolation · controlnet_aux · VideoHelperSuite · dynamicprompts · rgthree

**Mode « application » :** emballer chaque workflow en Subgraph et n'exposer que les widgets utiles (prompt, seed, denoise). Pour aller plus loin : `Save (API Format)` + l'API HTTP `POST /prompt` de ComfyUI, avec un petit front local qui injecte les paramètres dans le template JSON.
