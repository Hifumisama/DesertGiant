# FICHE DE PLAN — Le Colosse et l'Oasis

> Source : `SCENARIO.md` (découpage v0.3) · Modèle : **MiniMax H3** · **24 fps**
> 11 plans · **63 s de montage** · **69 s à générer**
> 35 assets à produire, dont 2 critiques — voir `REGISTRE_ASSETS_colosse.md`
> 6 plans en ancrage frame (10, 20, 40 en FL2VA ; 70, 80 en I2VA) · 5 en référence de sujet

---

## Paramètres globaux

**Style.** `Cinematic, live-action, photorealistic`. Le scénario ne nomme pas de style ; il est déduit du vocabulaire (perspective atmosphérique, brume de chaleur, profondeur de champ courte, contre-jour). À corriger en tête de fiche si l'intention était stylisée.

**Continuité imposée.** Le bras droit du colosse se termine par un **canon prélevé sur une carcasse** — c'est sa réparation, et c'est ce qui le distingue des morts. Conséquence sur toute la mise en scène : **il n'a qu'une main, la gauche.** Aucun plan ne peut lui en demander deux.

Son corps est parcouru de **fissures incandescentes**. Elles doivent apparaître dans chaque `retention_analysis` où le corps est visible : c'est le trait que le modèle efface en premier, avec le canon. Elles rendent aussi lisible une silhouette minuscule à contre-jour, là où une masse sombre disparaîtrait dans la brume.

**Le geste du film.** Le bras qu'il s'est fabriqué avec les morts est une arme ; c'est l'autre, l'originale, qui s'ouvre. Au plan 90 le canon reste le long du corps et ne touche jamais le sol. Ne jamais le souligner.

**Densité décroissante des débris.** 3-4 au plan 10, 1 tête au plan 20, 1 silhouette à l'horizon au plan 30, aucun à partir du plan 40, zéro métal à partir du plan 70. La règle est traduite plan par plan dans les prompts : chaque description énonce positivement ce qui est visible, jamais « pas de débris ».

**La rime des mains.** `DEBRIS_main_brisee_paume_ciel` (plan 10) est un **dérivé** de `CHAR_colosse_main_gauche_ouverte` (plan 100). Conséquence sur l'ordre de fabrication : l'asset critique du plan 100 se produit en premier, le prop clé du plan 10 en découle. Aucun prompt ne souligne le lien, conformément au scénario.

**Aucun dialogue.** Le film n'en contient pas : aucun `(S1)`, aucune balise `<d>` dans les prompts. Le premier son organique est le cri d'oiseau du plan 40, et les `overall_soundscape` sont construits pour que la rupture s'entende.

**Musique non-diégétique.** Le scénario ne mentionne aucun score. Tous les plans portent `non_diegetic_music: N/A`. Si une musique est prévue au montage, elle se décrit ici plan par plan (instrumentation, tempo, dynamique) — à me redemander.

**Écarts relevés avec le scénario source.**

- Les notes de production visent LTX : « plans 50 et 90 à générer courts puis ralentir via RIFE ». **Caduc sur H3**, qui génère 6 s nativement. Générer directement à la durée cible.
- Le plan 40 est écrit à 3 s, sous le plancher de H3. Généré à 5 s, à couper au montage.
- Les plans à 4 s sont générés à 5 s par sécurité : l'API annonce 4 s de plancher, la doc produit 5 s. Une seconde jetée coûte moins cher qu'un rejet de job.

---

## PLAN 10 — *Les traces*

| Durée montage | Durée génération | FPS | Mode |
|---|---|---|---|
| **8 s** | **8 s** | 24 | **FL2VA** (ancrage première et dernière frame) |

**Références (2/4)**

| Label | Asset | Rôle dans le plan |
|---|---|---|
| `<Picture 1>` | `FRAME_p10_debut` | **Première frame** — plongée sur les empreintes, rien d'autre |
| `<Picture 2>` | `FRAME_p10_fin` | **Dernière frame** — main au premier plan, colosse minuscule à l'horizon |

**Prompt**

```text
How the reference pictures align with the target video — Picture 1 (from Shot 1) aligns with the 0.00-second mark of the target video; Picture 2 (from Shot 1) aligns with the 8.00-second mark of the target video.

integrated_multimodal_description: [Shot 1] Cinematic, live-action and photorealistic, in hard low sunlight from the right with a warm slightly desaturated palette. The shot opens on the steep high-angle framing of <Picture 1>, looking down at a line of enormous humanoid footprints pressed deep into the sand, each depression holding cool blue shadow while the crests around them catch gold. Nothing else is in frame. The camera pushes forward along the footprint line with large amplitude at slow speed, one continuous move, the lens easing upward only slightly as it travels so the ground gives way to the horizon. The broken mechanical hand comes into frame from below, palm turned up in the sand with its fingers half open and its palm cavity filled with drifted sand, passing down toward the bottom edge as the camera advances over it. Half-buried machine carcasses slide through the middle distance, corroded plating catching the same low light. The horizon opens out, and far away at the end of the footprint line the walking machine becomes visible, minuscule, seen from behind and moving away from the camera with slow widely spaced steps, faint orange points burning in the fissures of its body. The camera decelerates and comes to a complete stop with the machine at the centre of the frame, holding perfectly still for the rest of the shot while the machine continues to walk away toward the horizon and grows very slightly smaller. Thin ribbons of loose sand drift across the surface throughout, and heat shimmer rises from the crests. The shot ends exactly on <Picture 2>, the broken hand resting along the bottom edge of the frame and the tiny walking silhouette at the end of the footprint line.

overall_soundscape: Steady dry wind moves across the dune field and grains of sand hiss over the crests throughout. Far in the distance, heavy footfalls land in a slow regular rhythm, deep and muffled by distance, each one arriving a fraction quieter than the last as the machine walks further away.

non_diegetic_music: N/A
```

**Notes** — passage en FL2VA. L'ouverture révèle des sujets absents de la première frame — la main brisée et le colosse — que le modèle inventerait en ancrage simple : la main est l'asset de rime, et le canon du colosse est précisément le détail qu'il efface. La dernière frame les verrouille tous les deux.

La main reste au bas du cadre à la fin au lieu d'en sortir. C'est une contrainte technique — pour être portée par `<Picture 2>` — mais aussi le meilleur cadre du plan : la main morte au premier plan, la machine vivante à l'horizon, dans une seule image. La rime avec le plan 100 s'y plante mieux qu'en la faisant disparaître.

Le mouvement est volontairement dégradé : plongée très inclinée plutôt que verticale pure, et bascule minimale pendant la translation. Une vue de dessus stricte imposerait un mouvement à deux axes, exactement ce que les notes de production cherchent à éviter.

Durée portée de 5 à 8 secondes : quatre temps successifs — les empreintes, la main, le colosse, l'arrêt — ne tiennent pas en cinq.

---


## PLAN 20 — *Le passage*

| Durée montage | Durée génération | FPS | Mode |
|---|---|---|---|
| **7 s** | **7 s** | 24 | **FL2VA** (ancrage première et dernière frame) |

**Références (2/4)**

| Label | Asset | Rôle dans le plan |
|---|---|---|
| `<Picture 1>` | `FRAME_p20_debut` | **Première frame** — caméra au sol, le colosse approche de face |
| `<Picture 2>` | `FRAME_p20_fin` | **Dernière frame** — son dos qui s'éloigne, vu du sol |

**Prompt**

```text
How the reference pictures align with the target video — Picture 1 (from Shot 1) aligns with the 0.00-second mark of the target video; Picture 2 (from Shot 1) aligns with the 7.00-second mark of the target video.

integrated_multimodal_description: [Shot 1] Cinematic, live-action and photorealistic, in hard raking sunlight with a warm desaturated palette. The shot opens on the ground-level framing of <Picture 1>, the camera resting almost on the sand in a steep low angle, coarse grains sharp in the foreground and a pale hot sky filling the upper frame, with the enormous humanoid machine walking straight toward the lens in the middle distance, its cannon arm swinging at its right side and orange fissures burning through its plating. It advances with slow widely spaced strides, growing rapidly in frame, each footfall driving a low ring of sand outward. As it reaches the camera its leading foot lands heavily just beside the lens, close enough to fill the lower corner, and its body passes directly over the frame; the camera tilts up and swings with it in one continuous unbroken movement at moderate speed, holding its centre of mass while the underside of its plating, its glowing seams and its trailing leg sweep across the sky. Its shadow floods the frame into near darkness as the mass passes, and the fissures rake across the image as moving bands of warm light. The camera continues its arc and settles low behind the machine as daylight returns, finding its back and the cannon arm as it walks away with the same slow rhythm, growing smaller against the dunes. Suspended dust drifts through the light and fine sand settles across the front of the lens. The shot ends exactly on <Picture 2>, the machine receding along its own line of fresh footprints.

overall_soundscape: Heavy footfalls approach from the middle distance, each impact saturated and low enough to distort, growing louder and closer together. Servo motors grind under load and rise to fill the whole field as the machine passes directly overhead, accompanied by a broad rush of displaced sand. The metallic layers thin out as it moves away, the impacts spacing back out and softening into steady dry wind, with loose grains pattering down onto the lens.

non_diegetic_music: N/A
```

**Notes** — le crâne est supprimé : il ne servait qu'à meubler et il concurrençait la masse du colosse, qui est le seul sujet du plan.

Il enjambe le **cadre**, pas l'objectif. Suivre littéralement son centre de gravité pendant qu'il passe au-dessus de la lentille imposerait une rotation de près de 180°, hors de portée du modèle. Le pied qui se plante à côté de la lentille et le corps qui envahit le cadre produisent la même sensation avec une bascule d'environ cent degrés sur un axe dominant.

C'est le raccord d'échelle du film : un vingtième de cadre au plan 10, le cadre entier ici. Le son porte la moitié du travail — les impacts se rapprochent, saturent au passage, puis s'espacent et s'adoucissent.

Durée portée de 5 à 7 secondes : arrivée, passage, éloignement.

---


## PLAN 30 — *La marche*

| Durée montage | Durée génération | FPS | Mode |
|---|---|---|---|
| **7 s** | **7 s** | 24 | **FL2VA** (ancrage première et dernière frame) |

**Références (2/4)**

| Label | Asset | Rôle dans le plan |
|---|---|---|
| `<Picture 1>` | `FRAME_p30_debut` | **Première frame** — travelling au buste, le colosse marche vers la droite |
| `<Picture 2>` | `FRAME_p30_fin` | **Dernière frame** — un oiseau bouche l'objectif et masque le colosse |

**Prompt**

```text
How the reference pictures align with the target video — Picture 1 (from Shot 1) aligns with the 0.00-second mark of the target video; Picture 2 (from Shot 1) aligns with the 7.00-second mark of the target video.

integrated_multimodal_description: [Shot 1] Cinematic, live-action and photorealistic, in hard raking sunlight with a warm desaturated palette. The shot opens on the framing of <Picture 1>, a low-angle chest-height view of the enormous humanoid machine walking in profile toward the right of frame, its corroded plating filling most of the image, orange fissures burning through the metal and the scavenged cannon on its right arm swinging heavily with each stride. Behind it the dune field slides past through layered heat haze. The camera tracks laterally alongside the machine with large amplitude at slow speed, matching its walking pace exactly so the body holds its place in the frame while the desert moves behind it, in one continuous unbroken movement. Dust shakes loose from the shoulder plates at every footfall and drifts backward through the light. A distant broken hull passes through the background haze, motionless. Partway through the shot, migrating birds enter the frame from the left, behind the machine, and overtake it travelling in the same direction, small and sharp against the metal as they cross its chest. More of them follow, closer to the camera each time, until one bird passes directly across the lens, so near that its dark wing sweeps the full width of the frame in heavy motion blur and covers the machine completely. The shot ends exactly on <Picture 2>, the frame filled by the blurred body of the passing bird.

overall_soundscape: Servo motors work in a heavy regular rhythm, plating shifting against plating at every stride, each footfall landing as a deep muffled impact with a soft rush of sand. Dry wind runs underneath throughout. Sharp bird calls cut in from behind the camera and multiply, growing closer and brighter, and a single hard wingbeat snaps past the microphone at the very end.

non_diegetic_music: N/A
```

**Notes** — l'oiseau qui bouche l'objectif est un volet naturel. Raccordé à la première frame du plan 40, où le même oiseau dégage, la coupe devient invisible et les deux plans se lisent comme une seule prise.

Passage en FL2VA pour cette seule raison : en référence de sujet, rien ne garantit qu'un oiseau masque le cadre à la septième seconde. C'est un événement trop précis pour être obtenu par la formulation. Le coût en identité est nul — une frame porte le canon mieux qu'une référence de sujet.

Le colosse marche vers la droite et les oiseaux le doublent dans le même sens. Cette direction gouverne toute la séquence : l'oasis est à droite, donc devant lui.

---

## PLAN 40 — *Les oiseaux*

| Durée montage | Durée génération | FPS | Mode |
|---|---|---|---|
| **8 s** | **8 s** | 24 | **FL2VA** (ancrage première et dernière frame) |

**Références (2/4)**

| Label | Asset | Rôle dans le plan |
|---|---|---|
| `<Picture 1>` | `FRAME_p40_debut` | **Première frame** — l'oiseau dégage, raccord invisible avec le plan 30 |
| `<Picture 2>` | `FRAME_p40_fin` | **Dernière frame** — colosse arrêté au bord gauche, oasis à droite |

**Prompt**

```text
How the reference pictures align with the target video — Picture 1 (from Shot 1) aligns with the 0.00-second mark of the target video; Picture 2 (from Shot 1) aligns with the 8.00-second mark of the target video.

integrated_multimodal_description: [Shot 1] Cinematic, live-action and photorealistic, in hard raking sunlight with a warm desaturated palette and heavy atmospheric haze. The shot opens on the framing of <Picture 1>, the blurred dark body of a bird still clearing the left of the lens, uncovering the enormous machine as it walks in profile toward the right of frame. More birds pour past the camera and away to the right, their wingbeats sharp and their bodies blurred by proximity. The focus racks off the machine and onto the flock, the metal falling into soft blur while the birds become the sharpest thing in the image. The camera stops tracking the machine and swings right to follow the flock instead, at slow speed in one continuous movement. The machine's walking stops abruptly during this movement: the body settles and long streams of fine sand pour from its shoulder plates. Falling behind the camera, it drifts back toward the left edge of the frame, staying in shot but out of focus and no longer the centre of attention, and its head rotates slowly to the right to follow the birds. As the camera continues after the flock, the desert opens out ahead and the horizon comes into view, and far away at the end of the birds' path a small green patch trembles in the heat. The focus pulls back toward depth, the birds continuing away into the distance. The shot ends exactly on <Picture 2>, the machine halted at the left edge with its head turned right, and the distant green held near the centre.

overall_soundscape: Servo motors and heavy footfalls carry over from the previous rhythm, then cut off sharply as the machine stops, leaving a metallic settling creak and the long soft hiss of sand pouring off the shoulders. Over them, sharp bird calls overlap and answer each other, passing very close to the microphone before spreading out into the distance. Wind rises underneath, and beneath it all, extremely faint and far away, a trace of moving water.

non_diegetic_music: N/A
```

**Notes** — le relais de regard est le cœur du plan : les oiseaux prennent la mise au point, entraînent l'œil, et entraînent le sien. C'est le seul moment du film où la caméra et le personnage découvrent la même chose en même temps.

La géographie est fixée par le plan 30 : tout va vers la droite, donc l'oasis est à droite. Le colosse s'arrête, prend du retard sur la caméra, et dérive vers le bord **gauche** en regardant à **droite**. Une erreur de sens ici casserait le raccord des deux plans.

FL2VA pour deux raisons cumulées. La première frame doit raccorder au volet du plan 30 au pixel près. Et la dernière impose deux choses que le modèle ne ferait jamais seul : une oasis minuscule à l'horizon, et un colosse hors centre et flou.

---


## PLAN 50 — *Le regard*

| Durée montage | Durée génération | FPS | Mode |
|---|---|---|---|
| 6 s | 6 s | 24 | full-reference |

**Références (3/4)**

| Label | Asset | Rôle dans le plan |
|---|---|---|
| `<Picture 1>` | `CHAR_colosse_buste_arret` | Buste et tête, pose d'arrêt |
| `<Picture 2>` | `CHAR_colosse_master` | Cohérence : bras droit réparé, textures |
| `<Picture 3>` | `DEC_desert_horizon_oasis` | Horizon désertique avec la tache verte lointaine |

**Prompt**

```text
subject_definitions:
<Subject 1> is the colossus in <Picture 1> and <Picture 2>, an enormous humanoid war machine; <Picture 1> establishes its chest and head in a halted stance and <Picture 2> establishes its overall build, worn plating, glowing orange fissures and a right arm ending in a scavenged cannon.
<Subject 2> is the desert horizon in <Picture 3>, a line of low dunes meeting a bright backlit sky, with a small green patch trembling in the heat far away.

summary:
[reference generation] The target video is a single six-second locked shot in which <Subject 1> stands motionless, already halted, sand still pouring from its shoulders, its head held toward the distant green patch of <Subject 2>.

retention_analysis:
<Subject 1> (appears in [Shot 1]): fully_preserved - the chest and head structure, worn plating, glowing fissures and cannon arm are retained.
<Subject 2> (appears in [Shot 1]): fully_preserved - the horizon line, backlit sky and distant green patch are retained.

detailed_description:
The target video is cinematic, live-action and photorealistic, strongly backlit, with a warm desaturated palette and heavy atmospheric haze.
[Shot 1] A chest-height shot frames <Subject 1> from the side against the bright sky, its head and shoulders rimmed by hard backlight, the cannon on its right arm hanging at its side and its fissures glowing steadily through the plating. The machine is already at a standstill and stays motionless for the whole shot. Fine dust and sand continue to pour from its shoulder plates in long thin streams that drift downward through the backlight and thin out toward the end. Its head is held turned away from its direction of travel, and it does not move. Behind it, <Subject 2> stretches out in soft focus, layered dunes under a bright hazy sky with a small green patch shimmering far away on the horizon. The camera holds a completely static shot for the entire duration. Only the falling sand, the heat shimmer and the faint pulsing of the fissures move in the frame. The composition is unchanged from first to last frame.

overall_soundscape:
Heavy servo movement cuts off sharply at the start, leaving a metallic settling creak. Sand streams off the shoulders in a soft continuous hiss that thins out as the pan continues, then wind alone, and beneath it, extremely faint and far away, a trace of moving water.

non_diegetic_music:
N/A
```

**Notes** — le plan a changé de fonction. Il révélait l'oasis ; le plan 40 s'en charge désormais. Il devient l'**après** de la découverte : un temps de contemplation entre la révélation et l'oasis, où il ne se passe rien d'autre que du sable qui tombe.

C'est le plan le plus immobile du film, et c'est délibéré. Après un travelling, un passage au-dessus de la caméra et un relais de regard, six secondes sans mouvement pèsent leur poids. La caméra est fixe, le sujet est fixe, seule la matière bouge.

---

## PLAN 70 — *L'oasis*

| Durée montage | Durée génération | FPS | Mode |
|---|---|---|---|
| 5 s | 5 s | 24 | **I2VA** |

**Références (1/4)**

| Label | Asset | Rôle dans le plan |
|---|---|---|
| `<Picture 1>` | `DEC_oasis_large` | **Première frame exacte** du plan |

**Prompt**

```text
For the target video, at 0.00 seconds into the target video, <Picture 1> (from [Shot 1]) is fully referenced.

integrated_multimodal_description: [Shot 1] Cinematic, live-action and photorealistic, the wide shot opens exactly on the oasis established in <Picture 1>, preserving the arrangement of palms, fruit trees, tall grasses, the clear pool and the surrounding light. The palette inverts from the surrounding desert into saturated cool greens with warm shadows, and sunlight filters through the canopy in shifting patches across the water and the grass. The camera holds a completely static shot for the entire duration. Fronds and leaves move gently in a light wind, tall grasses bend and recover along the water's edge, and slow ripples cross the surface of the pool, breaking the reflected canopy into moving fragments. Two birds descend into the frame from the upper right and settle on a low branch above the water, and a third lands at the pool edge and dips its head. No metal, machinery or debris appears anywhere in the frame. The composition established in <Picture 1> is held unchanged from first to last frame.

overall_soundscape: Water moves continuously against the pool edge with a soft irregular lapping, and dense birdsong overlaps from several directions in the canopy. Leaves and fronds rustle steadily in the wind, and brief wingbeats cut through as birds land.

non_diegetic_music: N/A
```

**Notes** — seul plan en mode base de la fiche. La plate d'oasis fait un excellent premier frame : la composition est fixe et validée d'avance, autant l'imposer plutôt que de la décrire. Les oiseaux et la végétation sont dans la plate, aucun asset supplémentaire nécessaire.

---

## PLAN 80 — *La reprise*

| Durée montage | Durée génération | FPS | Mode |
|---|---|---|---|
| 4 s | **5 s** | 24 | **I2VA** (ancrage frame) |

**Références (1/4)**

| Label | Asset | Rôle dans le plan |
|---|---|---|
| `<Picture 1>` | `FRAME_p80_epaule_oasis` | **Première frame exacte** — amorce d'épaule et canon, oasis derrière |

**Prompt**

```text
For the target video, at 0.00 seconds into the target video, <Picture 1> (from [Shot 1]) is fully referenced.

integrated_multimodal_description: [Shot 1] Cinematic, live-action and photorealistic, the shot opens exactly on the composition established in <Picture 1>, the machine's back, right shoulder and cannon arm filling the left foreground and cut by the frame edge, the dune slope running down into the palms and grasses of the oasis behind. Warm sunlight catches the upper edges of the plating while cool green light bounces up from below, and the fissures burn steadily through the metal. The camera holds a completely static shot for the entire duration. After a beat the machine begins to walk again: the shoulder rises, rotates forward and drops heavily as the first step lands, and the whole mass descends so that the shoulder and the cannon pass partially out of the bottom of the frame, progressively uncovering the oasis behind. Loose sand slides down the slope in sheets where the foot has pressed. The shot ends with the shoulder low against the bottom edge and the green fully open in the background.

overall_soundscape: Servo motors restart with a low rising whine and settle into a heavy working rhythm. A single deep footfall lands closer and louder than in earlier shots, followed by sand sliding down the dune face in a long dry rush, with faint birdsong carrying up from below.

non_diegetic_music: N/A
```

**Notes** — bascule en ancrage frame. L'amorce d'épaule coupée par le bord du cadre est exactement le cadrage partiel que le modèle refuse de tenir en référence de sujet. L'identité ne se perd pas pour autant : une première frame *est* l'identité, et cinq secondes de caméra fixe ne laissent pas le temps de dériver. Durée générée à 5 s, couper 1 s en entrée.

---

## PLAN 90 — *L'agenouillement*

| Durée montage | Durée génération | FPS | Mode |
|---|---|---|---|
| 6 s | 6 s | 24 | full-reference |

**Références (3/4)**

| Label | Asset | Rôle dans le plan |
|---|---|---|
| `<Picture 1>` | `CHAR_colosse_agenouillement` | Pose d'agenouillement, de profil |
| `<Picture 2>` | `DEC_oasis_lisiere` | Lisière de l'oasis, sable puis herbe |
| `<Picture 3>` | `CHAR_colosse_master` | Cohérence : silhouette debout, bras réparé |

**Prompt**

```text
subject_definitions:
<Subject 1> is the colossus in <Picture 1> and <Picture 3>, an enormous humanoid war machine; <Picture 1> establishes its kneeling posture in profile, left fist on the ground and cannon arm at its side and <Picture 3> establishes its standing build, worn plating, glowing orange fissures and a right arm ending in a scavenged cannon.
<Subject 2> is the oasis edge in <Picture 2>, a boundary where open sand gives way to thick green grass, with palms rising behind it.

summary:
[reference generation] The target video is a single six-second lateral shot in which <Subject 1> halts before <Subject 2>, holds still, then lowers onto one knee and sets its closed left hand on the ground.

retention_analysis:
<Subject 1> (appears in [Shot 1]): fully_preserved - the full-body structure, kneeling posture, worn plating, glowing fissures and cannon arm are retained.
<Subject 2> (appears in [Shot 1]): fully_preserved - the sand-to-grass boundary and the palms behind it are retained.

detailed_description:
The target video is cinematic, live-action and photorealistic, in mixed light with warm backlight behind and cool green fill from the front.
[Shot 1] A wide lateral shot, framed from slightly below, holds <Subject 1> in full figure in profile, standing at the edge of <Subject 2> where sand meets thick grass; warm light rims its back while green bounce fills its front plating and the cannon on its right arm hangs at its side. The camera holds a completely static shot for the entire duration. The machine stops dead and stays entirely motionless for about two seconds, with only fine dust drifting from its joints. Then the descent begins: the right leg bends and the body lowers slowly and very heavily onto one knee, the movement continuous and weighted, plating shifting against plating as the mass transfers. The knee meets the ground and drives sand outward in a low ring. Its left hand, held closed, comes down and settles onto the ground in front of the body, while the cannon arm stays lowered at its side and never touches the ground. The machine holds this final kneeling position, head lowered toward its own closed left hand, as the last dust settles.

overall_soundscape:
The shot opens into near silence with only faint wind and settling dust. A long structural creak builds as the body lowers, metal grinding slowly under load, then one heavy muffled impact as the hand meets the ground, followed by a soft rush of displaced sand. Birdsong continues quietly from the oasis behind.

non_diegetic_music:
N/A
```

**Notes** — les 2 s d'immobilité initiale sont explicitement chiffrées dans le prompt : c'est le battement que le scénario interdit de raccourcir, et un modèle vidéo comble le vide s'il n'est pas décrit. Générer en 6 s natifs, sans passer par un ralenti.

---

## PLAN 100 — *Les doigts*

| Durée montage | Durée génération | FPS | Mode |
|---|---|---|---|
| 4 s | **5 s** | 24 | full-reference |

**Références (3/4)**

| Label | Asset | Rôle dans le plan |
|---|---|---|
| `<Picture 1>` | `CHAR_colosse_main_gauche_ouverte` | **ASSET CRITIQUE** — détail des cinq doigts |
| `<Picture 2>` | `CHAR_colosse_master` | Cohérence : matière, rouille, échelle des plaques |
| `<Picture 3>` | `DEC_oasis_lisiere` | Sol herbe et sable, hors foyer |

**Prompt**

```text
subject_definitions:
<Subject 1> is the colossus hand in <Picture 1> and <Picture 2>; <Picture 1> establishes its five enormous left-hand fingers, their segmented plating and worn joints, and <Picture 2> establishes the machine's overall metal surface, rust tone and panel scale.
<Subject 2> is the ground in <Picture 3>, grass and sand at the oasis edge, present only as soft out-of-focus texture.

summary:
[reference generation] The target video is a single close shot of the five fingers of <Subject 1> opening very slowly above <Subject 2>, with warm light escaping from within and the contents never revealed.

retention_analysis:
<Subject 1> (appears in [Shot 1]): fully_preserved - the finger structure, segmented plating, worn joints and rust tone are retained.
<Subject 2> (appears in [Shot 1]): weak_reference - only the general colour and texture of grass and sand are retained, held far out of focus.

detailed_description:
The target video is cinematic, live-action and photorealistic, with a very shallow depth of field and a warm, soft key light.
[Shot 1] A close shot frames only the five fingers of <Subject 1>, filling the frame from edge to edge, their segmented plating and pitted rust rendered in sharp detail while <Subject 2> sits far behind them as a soft wash of green and sand tones, completely out of focus. The camera holds a completely static shot for the entire duration. The fingers begin to spread apart very slowly in one continuous movement, the joints rotating a fraction at a time, plating sliding against plating and fine grit falling from the seams. As the gap between the fingers widens, a warm soft light escapes from inside and grows across the inner surfaces of the metal, catching the worn edges and the rust. The framing stays tight on the fingers throughout and never widens, and the interior of the hand remains outside the frame, so that what the fingers hold is never visible. The movement continues to the final frame without completing.

overall_soundscape:
A single continuous metallic creak runs through the entire shot, thin and very slow, the sound of large plates rotating under their own weight. Grains of grit fall from the joints in brief scattered ticks, with quiet birdsong and moving water further back.

non_diegetic_music:
N/A
```

**Notes** — la contrainte du scénario (jamais la main entière et son contenu dans un même cadre net) est traduite en instructions positives : cadre serré maintenu, intérieur hors champ, mouvement inachevé. C'est aussi la raison d'être de `<Picture 3>` en slot 3 : sans référence de sol, le modèle a tendance à reculer pour « montrer le contexte ».

---

## PLAN 110 — *Les humains*

| Durée montage | Durée génération | FPS | Mode |
|---|---|---|---|
| 4 s | **5 s** | 24 | full-reference |

**Références (3/4)**

| Label | Asset | Rôle dans le plan |
|---|---|---|
| `<Picture 1>` | `HUM_duo_pilotes_allonges` | Les deux pilotes allongés, l'un contre l'autre |
| `<Picture 2>` | `CHAR_colosse_surface_paume` | La paume, lisible seulement comme surface |
| `<Picture 3>` | `PROP_blason_unite` | L'emblème d'unité, pour qu'il ne se réinvente pas |

**Prompt**

```text
subject_definitions:
<Subject 1> are the two pilots in <Picture 1>, a young woman with dark skin and African features and a young man with Mediterranean features, both in their twenties, lying asleep against each other in white close-fitting flight uniforms stained with dust, each uniform carrying the same unit emblem on the shoulder.
<Subject 2> is the metal surface in <Picture 2>, a broad expanse of rusted plating with shallow seams and pitting, readable as a floor and not as part of a body.
<Subject 3> is the unit emblem in <Picture 3>, a simple high-contrast geometric badge worn on the shoulder of both uniforms.

summary:
[reference generation] The target video is a single tight overhead insert of <Subject 1> resting on <Subject 2>, which tilts very slightly as one of them breathes and a drop of condensation slides across the rust.

retention_analysis:
<Subject 1> (appears in [Shot 1]): fully_preserved - the facial features and skin tones of both pilots, their positions against each other and the dust-stained white uniforms are retained.
<Subject 2> (appears in [Shot 1]): fully_preserved - the rusted plating, seams and pitting are retained.
<Subject 3> (appears in [Shot 1]): fully_preserved - the exact shape and contrast of the shoulder emblem are retained on both uniforms.

detailed_description:
The target video is cinematic, live-action and photorealistic, lit by a warm soft light entering from the edge of the frame.
[Shot 1] A tight high-angle insert looks straight down on <Subject 1>, the two pilots lying close together on <Subject 2>, which fills the frame edge to edge as an expanse of rusted plating; the metal reads only as a surface, with no outline that identifies it as a hand. Their white uniforms are the only clean bright thing in the frame, greyed with dust along the folds, and <Subject 3> sits clearly on the shoulder of each. Warm light enters from the right edge and falls across their faces and the rust, leaving the far side of the frame in soft shadow. The camera holds a completely static shot for the entire duration. The surface beneath them tilts downward by a very small amount in one slow continuous movement, and both bodies shift a fraction with it. The woman moves almost imperceptibly as her chest rises and falls once. A bead of condensation forms on the plating near their shoulders, holds, then slides down across the rust and pools in a shallow seam. The frame ends unchanged in composition, with the light steady on both faces.

overall_soundscape:
A slow shallow breath is audible close to the microphone, followed by a second. Birdsong from the oasis is now very near and bright on all sides, mixed with soft water movement, and a faint metallic settling tick runs under it.

non_diegetic_music:
N/A
```

**Notes** — le blason occupe le troisième slot au lieu de rester vide. C'est le détail que le modèle réinvente d'un plan à l'autre, exactement comme le canon ; lui donner sa propre référence coûte un slot et règle le problème. Le quatrième reste libre : ajouter le master du colosse rendrait la paume identifiable comme une main et tuerait le plan.

---

## PLAN 120 — *Le regard*

| Durée montage | Durée génération | FPS | Mode |
|---|---|---|---|
| 4 s | **5 s** | 24 | full-reference |

**Références (3/4)**

| Label | Asset | Rôle dans le plan |
|---|---|---|
| `<Picture 1>` | `HUM_portrait_pilote_femme` | **ASSET CRITIQUE** — portrait serré de la pilote |
| `<Picture 2>` | `DEC_oasis_bokeh` | Verts de l'oasis en flou complet |
| `<Picture 3>` | `PROP_blason_unite` | L'emblème, visible sur le col |

**Prompt**

```text
subject_definitions:
<Subject 1> is the young woman in <Picture 1>, a pilot in her twenties with dark skin and African features, seen in tight portrait with dust on her skin, dry lips and closed eyes, the collar of her white flight uniform visible at the bottom of the frame.
<Subject 2> is the oasis background in <Picture 2>, dense green foliage and filtered light rendered entirely out of focus.
<Subject 3> is the unit emblem in <Picture 3>, a simple high-contrast geometric badge carried on the uniform collar.

summary:
[reference generation] The target video is a single close shot of <Subject 1> against <Subject 2>, in which her eyes open slowly before the image fades to black.

retention_analysis:
<Subject 1> (appears in [Shot 1]): fully_preserved - her facial features, skin tone, the dust on her skin and the framing are retained.
<Subject 2> (appears in [Shot 1]): fully_preserved - the out-of-focus green foliage and filtered light are retained.
<Subject 3> (appears in [Shot 1]): fully_preserved - the exact shape and contrast of the emblem on the collar are retained.

detailed_description:
The target video is cinematic, live-action and photorealistic, with an extremely shallow depth of field, warm soft light on the face and cool green light behind it.
[Shot 1] A close-up frames the face of <Subject 1>, sharp against <Subject 2>, whose greens dissolve into wide soft bokeh across the whole background with occasional bright highlights where light passes between the leaves. Warm light falls across her cheek and brow while the far side of her face stays in gentle shadow, and fine dust is visible on her skin. At the bottom edge of the frame, the dust-greyed white collar of her uniform carries <Subject 3>, slightly out of focus but clearly shaped. The camera holds a completely static shot for the entire duration. Her face remains completely still at first, with only a faint movement of breath. Around the third second her eyelids begin to lift, slowly and unevenly, until her eyes are fully open and focused on something beyond the frame; the pupils contract slightly in the light. The background bokeh shifts very gently as the foliage moves behind. In the final half second the image fades smoothly to black.

overall_soundscape:
Close, slow breathing continues throughout, with bright birdsong and moving water very near on all sides. Leaves rustle softly behind. Every layer drops away into complete silence as the image fades to black.

non_diegetic_music:
N/A
```

**Notes** — c'est elle qui ouvre les yeux, et c'est le dernier plan du film. Le fondu au noir est décrit dans le prompt et la coupure sonore lui est synchronisée, pour que le silence final soit généré et pas ajouté en post.

---


# Notes de production

**Ordre de fabrication.** La chaîne de dérivation impose une séquence :

1. `CHAR_colosse_master` — tout en dépend, y compris les débris.
2. `CHAR_colosse_main_gauche_ouverte` ⚠️ et `HUM_portrait_serre` ⚠️ — les deux assets critiques. Valider avant de lancer quoi que ce soit d'autre.
3. `DEBRIS_main_brisee_paume_ciel` et `CHAR_colosse_surface_paume`, tous deux dérivés de la main du plan 100.
4. Le reste des poses et détails du colosse, puis les débris.
5. Les décors, produisibles en parallèle dès le départ — ils ne dépendent de rien.

**Ce qui a changé par rapport au scénario.** Les notes de production visaient LTX. Sur H3 : les plans 50 et 90 se génèrent en 6 s natifs, le détour par RIFE est inutile et dégraderait le panoramique du plan 50. En revanche H3 impose un plancher de durée, ce qui touche le plan 40 (3 s écrits, 5 s générés) et les quatre plans à 4 s.

**Le problème d'échelle, et son remède.** Les plans 10, 20, 30, 40 et 80 sont passés en ancrage par frame. En mode référence de sujet, le modèle ramenait systématiquement le colosse vers l'avant du cadre : il est entraîné sur des images bien composées, sujet lisible et centré, et ce prior gagne contre n'importe quelle formulation. Quatre d'entre eux sont des plans où l'identité n'a aucune importance visuelle — une silhouette d'un dixième de cadre, un pied, une ombre. Le cinquième, le plan 80, est un cadrage partiel : une amorce coupée par le bord du cadre, que le modèle refuse tout autant de tenir. Et l'ancrage ne coûte rien en identité, puisqu'une première frame *est* l'identité — son seul risque est la dérive dans la durée, négligeable sur des plans fixes de cinq secondes.

Le corollaire vaut pour les cinq plans restants en référence de sujet : **le budget de mots gouverne l'échelle**. L'attention du modèle suit la place accordée à chaque chose. Un colosse qui reçoit quarante mots sur cent devient le sujet, donc devient grand.

**Plans à risque.**

- **Plan 100** — le cadre doit rester serré. Un modèle vidéo a une pente naturelle vers l'élargissement pour « montrer le contexte » ; c'est exactement ce que le plan interdit. Si les générations reculent malgré le prompt, recadrer en post plutôt que de relancer.
- **Plan 20** — l'ombre qui noie le cadre puis se retire reste le passage le plus fragile, mais les fissures incandescentes donnent au modèle de quoi animer l'obscurcissement au lieu d'une seconde d'image morte.
- **Plan 50** — le panoramique doit rester synchronisé à la rotation de la tête, sans coupe. C'est un seul geste, et le prompt l'énonce comme tel ; toute génération où la caméra part avant la tête est à rejeter.

**Le piège.** « Désert post-apocalyptique jonché d'épaves » est le cliché par défaut des modèles. Les prompts ne le nient jamais — ils décrivent positivement un nombre précis de débris à des positions précises, ce qui est la seule formulation qui tienne.
