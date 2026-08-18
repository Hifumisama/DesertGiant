# REGISTRE D'ASSETS — Le Colosse et l'Oasis

> Projet : *Le Colosse et l'Oasis* · 40 assets actifs · 6 retirés · 2 critiques
> Fiche associée : `FICHE_DE_PLAN_colosse.md`
> Statuts : ⬜ à produire · 🟡 en cours · ✅ validé
> Pipeline : Z-Image Turbo (T2I) · Qwen Image Edit 2511 (I2I) · PNG sRGB 8 bits
> Format du film : **16:9** · plates en 1536×864 · identité et détails en 1024×1024

## Ordre de fabrication

1. `CHAR_colosse_master` — parent de 12 assets. Rien ne commence avant lui.
2. `CHAR_colosse_main_gauche_ouverte` ⚠️ et `HUM_portrait_serre` ⚠️ — les deux critiques, à valider avant d'engager le reste.
4. `DEBRIS_main_brisee_paume_ciel` — dérivés de la main du plan 100.
5. Poses et détails du colosse, puis les débris.
6. Décors — indépendants, produisibles en parallèle dès le premier jour.
7. **Frames d'ancrage** (`FRAME_`) — composites assemblés en dernier, une fois décors et poses validés.

> La chaîne de dérivation renverse l'ordre du film : la main du plan 100 se fabrique avant le prop d'ouverture du plan 10, qui en descend.

## Avertissement de production

`DEBRIS_carcasses_ensablees` demande « poses variées ». Z-Image Turbo a une variance de seed très faible — un balayage de seeds donnera trois images quasi identiques. Prévoir **trois prompts réellement distincts**, ou basculer cet asset sur Z-Image Base.

**Sources de pose contre frames d'ancrage.** Les assets `CHAR_` ne portent que la forme : fond neutre, lumière plate, aucune ambiance. Ce sont les `FRAME_` qui portent la lumière, le décor et la composition. Une source de pose tirée avec du sable ou un contre-jour se battra avec la plate au moment de la fusion — et le sol visible dans une source fixe en plus une hauteur de caméra qui contredira celle du plan.

Réglages par défaut, sauf mention contraire : **8 steps · CFG 1 · euler_ancestral / beta · dimensions divisibles par 32**. Pas de negative prompt : Z-Image Turbo l'ignore, toutes les exclusions sont formulées positivement dans le prompt.

---

# Colosse — master et poses

### `CHAR_colosse_master`
- **Statut** : ⬜
- **Plans** : 50, 80, 90, 100 (référence de cohérence)
- **Dérivé de** : — (master)
- **Critique** : non, mais fondation de 12 assets
- **Description canonique** : An enormous humanoid war machine in corroded copper-brown plating, its body split by glowing orange fissures that burn from within. Spiked pauldrons, a riveted helmet-like head with narrow glowing eye slits. **Its right arm ends in a heavy scavenged cannon instead of a hand** — the barrel runs the length of the forearm. Only its left arm carries an articulated five-fingered hand.
- **Cadrage** : plein pied, trois quarts, fond désertique simple, lumière neutre, lisibilité maximale des matières. 1024×1024.
- **Prompt Z-Image** :
  ```text
  Full body three-quarter view of an enormous humanoid war machine, photorealistic, cinematic. Corroded copper-brown armoured plating split by glowing orange fissures that burn from within, spiked pauldrons, a riveted helmet-like head with narrow glowing eye slits. Its right arm ends in a heavy scavenged cannon instead of a hand, the barrel running the length of the forearm. Its left arm carries an articulated five-fingered hand. Plain white background, neutral even lighting, every material and every fissure clearly readable.
  ```
- **Note** : le master vit sur fond blanc, sans échelle ni composition. C'est volontaire — une référence d'identité qui montre le sujet grand et centré enseigne au modèle vidéo que le sujet doit remplir le cadre.
- **Fichier** : `—`
- **Seed** : `—`

### `CHAR_colosse_dos_debout`
- **Statut** : ⬜ · **Plans** : 10 · **Dérivé de** : `CHAR_colosse_master`
- **Description canonique** : The colossus seen from directly behind at extreme distance, reduced to a dark upright silhouette blurred by atmospheric haze.
- **Édition Qwen** — source : `CHAR_colosse_master`
  ```text
  Rotate the machine to be seen from directly behind, walking away from the camera.
  Push it far into the distance so it occupies a small portion of the frame, and soften it with heat haze and atmospheric perspective.
  Relight as a backlit silhouette with hard low sunlight from the right.
  ```
- **Fichier** : `—` · **Seed** : `—`

### `CHAR_colosse_silhouette_marche` — *retiré*
- **Statut** : ⛔ retiré du découpage (v0.8)
- **Motif** : le plan 30 est passé du plan d'ensemble au travelling au buste — la silhouette lointaine de profil n'est plus cadrée.
- Conservé pour mémoire : ne pas le reproduire sans raison de le réintroduire.

### `CHAR_colosse_buste_marche`
- **Statut** : ⬜ · **Plans** : 30 · **Dérivé de** : `CHAR_colosse_master`
- **Rôle** : référence d'identité — forme et matières seulement, ni lumière ni décor
- **Description canonique** : The colossus walking in profile, framed at chest height, cannon arm swinging with the stride, fissures burning through the plating.
- **Édition Qwen** — source : `CHAR_colosse_master`
  ```text
  Crop to a chest-height side profile of the machine in mid-stride, one shoulder forward, the cannon arm swinging at its right side.
  Keep a plain neutral background and flat even lighting, with the glowing fissures clearly readable.
  ```
- **Fichier** : `—` · **Seed** : `—`

### `CHAR_colosse_buste_arret`
- **Statut** : ⬜ · **Plans** : 50 · **Dérivé de** : `CHAR_colosse_master`
- **Description canonique** : The colossus chest and head in profile, halted and settled, the rebuilt lighter-rust right arm clearly visible.
- **Édition Qwen** — source : `CHAR_colosse_master`
  ```text
  Crop to a chest-height side profile showing only the upper torso, shoulders and head.
  Relight as strong backlight, rimming the head and shoulders against a bright sky, keeping the cannon arm and the glowing fissures readable.
  ```
- **Fichier** : `—` · **Seed** : `—`

### `CHAR_colosse_dos_epaule` — *retiré*
- **Statut** : ⛔ retiré du découpage (v0.8)
- **Motif** : le plan 80 n'est plus une amorce d'épaule mais un plan large de seuil.
- Conservé pour mémoire : ne pas le reproduire sans raison de le réintroduire.

### `CHAR_colosse_agenouillement`
- **Statut** : ⬜ · **Plans** : 90 · **Dérivé de** : `CHAR_colosse_master`
- **Description canonique** : The colossus kneeling on one knee in profile, both hands closed and resting on the ground in front of it, head slightly lowered.
- **Édition Qwen** — source : `CHAR_colosse_master`
  ```text
  Pose the machine kneeling on one knee in full side profile, its left fist closed and set on the ground in front of it, the cannon arm hanging at its side, head tilted slightly down toward its own hands.
  Lower the camera slightly below eye level, keeping the whole figure in frame.
  ```
- **Fichier** : `—` · **Seed** : `—`

---

# Colosse — détails

### `CHAR_colosse_pied_contreplongee`
- **Statut** : ⬜ · **Plans** : 80, 90 (via les frames) · **Dérivé de** : `CHAR_colosse_master`
- **Rôle** : référence d'identité — forme et matières seulement, ni sol ni lumière
- **Description canonique** : The colossus feet and lower legs in extreme low angle, ankle articulation and underside plating visible, sand caked in the joints, fissures glowing through the shin plating.
- **Édition Qwen** — source : `CHAR_colosse_master`
  ```text
  Move the camera down to ground level beside the machine, looking steeply upward, framing the feet and lower legs with strong perspective distortion and the ankle articulation clearly visible.
  Pose it standing motionless, both legs vertical and parallel, feet flat and side by side, weight evenly on both.
  Keep a plain neutral background with no ground and no horizon, and flat even lighting.
  ```
- **Note** : réactivé après avoir été retiré au découpage v0.8. Les plans 80 et 90 ne montrent plus le colosse en entier — c'est cette référence qui porte désormais l'échelle. Le tirage existant est réutilisable après retrait du sable.
- **Pose à l'arrêt obligatoire.** Le master est en appui dynamique ; un composite qui en dérive rendra toujours une foulée, quelles que soient les instructions. La pose jambes parallèles doit exister **dans cette référence**, pas être demandée au moment de la fusion.
- **Fichier** : `—` · **Seed** : `—`

### `CHAR_colosse_epaule_tete` — *retiré*
- **Statut** : ⛔ retiré du découpage (v0.7)
- **Motif** : le plan 40 ne montre plus l'épaule en silhouette contre le ciel.
- Conservé pour mémoire : ne pas le reproduire sans raison de le réintroduire.

### `CHAR_colosse_main_gauche_ouverte` ⚠️
- **Statut** : ⬜ · **Plans** : 100 · **Dérivé de** : `CHAR_colosse_master`
- **Critique** : **oui** — l'échec de cet asset ruine la fin du film, et il est le parent de deux autres
- **Description canonique** : Five enormous segmented metal fingers of its left hand, half open, worn joints and pitted rust, the interior of the hand outside the frame.
- **Cadrage** : gros plan serré, profondeur de champ très courte, lumière chaude douce, arrière-plan hors foyer. Carré 1024×1024.
- **Prompt Z-Image** (génération directe, la précision prime sur la dérivation) :
  ```text
  Extreme close-up of five enormous segmented metal fingers of a colossal machine's left hand of a colossal machine, half open, filling the frame edge to edge. Photorealistic, cinematic, very shallow depth of field. Heavy armoured plates with pitted rust, worn hinge joints, fine grit lodged in the seams, the same corroded metal and lighter salvaged tones as the rest of the machine. Soft warm light rakes across the plating from the left. The background is grass and sand held completely out of focus. The frame stays tight on the fingers and the inside of the hand is outside the frame.
  ```
- **Réglages** : 8 steps · CFG 1 · 1024×1024. **Valider avant d'engager le reste de la production.**
- **Fichier** : `—` · **Seed** : `—`

### `CHAR_colosse_surface_paume`
- **Statut** : ⬜ · **Plans** : 110 · **Dérivé de** : — (master, génération directe)
- **Description canonique** : A broad flat expanse of corroded copper-brown armour plating with shallow seams, rivets and corrosion pitting, readable as a floor and never as part of a body.
- **Cadrage** : vue de dessus, plein cadre, aucun bord ni contour. 1024×1024.
- **Prompt Z-Image** :
  ```text
  Overhead view of a vast flat deck of corroded copper-brown armour plating, photorealistic, cinematic. Large flat panels meet along shallow straight seams studded with rivets, the surface pitted and worn smooth by centuries of abrasion, with patches of grey-blue oxidation spreading across the rust. The plating fills the entire frame edge to edge as one continuous uninterrupted floor, seen from directly above. Soft warm light rakes in from the right edge, leaving the far side of the deck in gentle shadow.
  ```
- **Note** : **surtout pas un dérivé de la main.** Qwen Image Edit préserve la structure par conception — lui demander d'effacer des doigts sur une image de main revient à combattre sa fonction, et il rendra des phalanges quel que soit le nombre d'essais. Ici il n'y a aucune identité à conserver : l'asset n'existe que pour *ne pas* ressembler à une main. On le génère donc directement, en décrivant un pont métallique, concept que le modèle possède déjà.
- **Test de validation** : montrer l'image à quelqu'un qui ne connaît pas le projet. S'il dit « une main », c'est raté.
- **Fissures** : aucune sur cette surface. Le plan 110 éclaire les humains depuis le bord du cadre ; un sol incandescent sous des corps endormis se battrait avec cette lumière et donnerait une image inquiétante là où le plan veut de la douceur.
- **Fichier** : `—` · **Seed** : `—`

---

# Humains

> Ce sont **les pilotes du colosse** : une femme et un homme d'une vingtaine d'années, en uniforme de vol blanc portant le même emblème d'unité. Rien dans le film ne le dit — ce sont les uniformes qui le racontent. Le blanc est la seule matière non corrodée de tout le film, et c'est ce qui les met à part sans un mot.

### `PROP_blason_unite`
- **Statut** : ⬜ · **Plans** : 110, 120 · **Dérivé de** : — (master)
- **Description canonique** : A simple two-colour geometric unit emblem, high contrast, no fine detail.
- **Cadrage** : à plat, plein cadre, fond uni. 1024×1024.
- **Prompt Z-Image** :
  ```text
  A simple military unit emblem on a plain flat background, graphic design, flat vector style. One bold geometric shape in deep navy on white, clean hard edges, strong contrast, no gradients, no fine lines, no lettering. Centred, symmetrical, filling most of the frame.
  ```
- **Note** : **à concevoir pour quarante pixels, pas pour mille.** Dans les deux plans où il apparaît, l'emblème occupe une largeur d'épaule ou de col dans un cadre serré. Tout ce qui est fin, ajouré ou textuel deviendra une bouillie, et surtout le modèle vidéo le réinventera différemment à chaque plan. C'est le même mécanisme qui effaçait le canon. Test : réduire l'image à 40 px de large ; si la forme reste identifiable, c'est bon.
- **À produire en premier** parmi les humains : les deux autres assets s'en servent.
- **Fichier** : `—` · **Seed** : `—`

### `HUM_pilote_femme_master`
- **Statut** : ⬜ · **Plans** : source de `HUM_duo_pilotes_allonges` et `HUM_portrait_pilote_femme` · **Dérivé de** : — (master)
- **Description canonique** : A pilot in her twenties with dark skin and African features, in a white close-fitting flight uniform greyed with dust, the unit emblem on her shoulder and a smaller one on her collar.
- **Cadrage** : buste de face, fond neutre, lumière plate, yeux ouverts. 1024×1024.
- **Prompt Z-Image** :
  ```text
  Front-facing bust portrait of a woman in her twenties with dark skin and African features, photorealistic, cinematic. She wears a white close-fitting flight uniform, the fabric greyed and streaked with dust along the folds, collar closed at the throat. Her eyes are open and she looks straight at the camera, fine dust on her skin, dry lips. Plain neutral background, flat even lighting, every facial feature clearly readable.
  ```
- **Passe 2 — application du blason**, sources : ce tirage + `PROP_blason_unite`
  ```text
  Add the emblem from the second image to the shoulder of the uniform, and a smaller version of it on the collar, both following the fabric folds and lighting.
  ```
- **Note** : yeux **ouverts** dans le master, même si les deux plans du film la montrent d'abord endormie. Fermer des yeux ouverts est une édition triviale ; inventer un regard qui n'existe nulle part dans la source, non — et c'est précisément ce que demande le plan 120.
- **Fichier** : `—` · **Seed** : `—`

### `HUM_pilote_homme_master`
- **Statut** : ⬜ · **Plans** : source de `HUM_duo_pilotes_allonges` · **Dérivé de** : — (master)
- **Description canonique** : A pilot in his twenties with Mediterranean features, in a white close-fitting flight uniform greyed with dust, the unit emblem on his shoulder and a smaller one on his collar.
- **Cadrage** : buste de face, fond neutre, lumière plate, yeux ouverts. 1024×1024.
- **Prompt Z-Image** :
  ```text
  Front-facing bust portrait of a man in his twenties with Mediterranean features, olive skin and dark hair, photorealistic, cinematic. He wears a white close-fitting flight uniform, the fabric greyed and streaked with dust along the folds, collar closed at the throat. His eyes are open and he looks straight at the camera, fine dust on his skin, dry lips. Plain neutral background, flat even lighting, every facial feature clearly readable.
  ```
- **Passe 2 — application du blason**, sources : ce tirage + `PROP_blason_unite`
  ```text
  Add the emblem from the second image to the shoulder of the uniform, and a smaller version of it on the collar, both following the fabric folds and lighting.
  ```
- **Fichier** : `—` · **Seed** : `—`

### `HUM_duo_pilotes_allonges`
- **Statut** : ⬜ · **Plans** : 110 · **Dérivé de** : `HUM_pilote_femme_master` + `HUM_pilote_homme_master`
- **Description canonique** : The two pilots lying asleep against each other, seen from directly above on a flat rusted surface, warm light entering from the right edge.
- **Édition Qwen (multi-image)** — sources : les deux masters
  ```text
  Place both people lying asleep on their backs on a flat rusted metal surface, seen from directly above, the woman's head resting against the man's shoulder, their faces turned toward each other with their eyes closed.
  Keep both faces, skin tones, uniforms and shoulder emblems exactly as in the source images.
  Light them with soft warm light entering from the right edge of the frame, leaving the far side in gentle shadow, with a shallow depth of field.
  ```
- **Note** : les uniformes doivent rester **salis**. Du blanc immaculé après une traversée de désert ferait plateau de tournage — et c'est la poussière qui rend crédible le blanc comme seule matière propre du film.
- **Fichier** : `—` · **Seed** : `—`

### `HUM_portrait_pilote_femme` ⚠️
- **Statut** : ⬜ · **Plans** : 120 · **Dérivé de** : `HUM_pilote_femme_master`
- **Critique** : **oui** — c'est le dernier plan du film
- **Description canonique** : Tight portrait of the woman pilot, eyes closed, dust on her skin, dry lips, the dust-greyed white collar of her flight uniform at the bottom of the frame with the unit emblem on it.
- **Édition Qwen** — source : `HUM_pilote_femme_master`
  ```text
  Reframe to a tight close-up portrait filling the frame with her face, and close her eyes.
  Keep the same facial features, skin tone, dust on the skin and dry lips, and keep the collar with its emblem at the bottom edge of the frame.
  Replace the background with dense out-of-focus green foliage and soft filtered light, and use a very shallow depth of field with only the face in focus.
  ```
- **Note** : dérive du master, **pas du duo**. Le duo est une plongée où les visages sont petits, de trois quarts et écrasés par l'angle : en tirer un gros plan reviendrait à demander au modèle d'inventer ce que la source ne contient pas.
- **Fichier** : `—` · **Seed** : `—`

---

# Décors

> Tous les décors sont indépendants et produisibles dès le premier jour, en parallèle du colosse. Ratio **16:9, 1536×864** pour les plates de composition ; les deux fonds hors foyer peuvent rester en carré.

### `DEC_desert_empreintes_sol`
- **Statut** : ⬜ · **Plans** : 10 · **Dérivé de** : —
- **Description canonique** : A sea of tall dunes with a line of enormous humanoid footprints receding to the horizon, blue shadow inside each print, golden sand crests.
- **Prompt Z-Image** :
  ```text
  Very low camera almost at sand level in a sea of tall desert dunes, photorealistic, cinematic wide shot. A line of enormous humanoid footprints presses deep into the sand and recedes toward a distant horizon, each depression holding cool blue shadow while the surrounding crests catch hard golden light. Low raking sunlight from the right, thin ribbons of sand drifting across the surface, clear open sky above the horizon.
  ```
- **Réglages** : 1536×864
- **Fichier** : `—` · **Seed** : `—`

### `DEC_desert_sol_contreplongee`
- **Statut** : ⬜ · **Plans** : 20 · **Dérivé de** : —
- **Description canonique** : Coarse sand filling the lower frame in sharp foreground detail, pale hot sky above, no subject.
- **Prompt Z-Image** :
  ```text
  Camera resting directly on desert sand in extreme low angle, photorealistic, cinematic. Coarse sand grains fill the bottom third of the frame in sharp foreground detail, with a wide pale sun-bleached sky occupying the rest. Hard raking sunlight from the right, suspended dust catching the light, empty frame with no subject.
  ```
- **Réglages** : 1536×864
- **Fichier** : `—` · **Seed** : `—`

### `DEC_desert_panoramique`
- **Statut** : ⬜ · **Plans** : 30 · **Dérivé de** : —
- **Description canonique** : Dunes running unbroken to a distant horizon beneath a vast sky, layered atmospheric perspective and visible heat haze.
- **Prompt Z-Image** :
  ```text
  Extreme wide shot of an unbroken sea of desert dunes running to a distant horizon, photorealistic, cinematic. The dunes occupy the lower third of the frame and an immense pale sky fills the rest. Successive dune ridges fade through layers of atmospheric perspective into visible heat haze. Hard low sunlight from the right, empty landscape, clean uncluttered horizon line.
  ```
- **Réglages** : 1536×864
- **Fichier** : `—` · **Seed** : `—`

### `DEC_ciel_ocre` — *retiré*
- **Statut** : ⛔ retiré du découpage (v0.7)
- **Motif** : le plan 40 a été refondu au niveau du buste, avec horizon — le ciel pur n'est plus cadré.
- Conservé pour mémoire : ne pas le reproduire sans raison de le réintroduire.

### `DEC_desert_horizon_oasis`
- **Statut** : ⬜ · **Plans** : 50 · **Dérivé de** : —
- **Description canonique** : Backlit desert horizon of low dunes, with a small green patch trembling in the heat far away.
- **Prompt Z-Image** :
  ```text
  Backlit wide shot of a desert horizon, low dunes meeting a bright hazy sky, photorealistic, cinematic. Far away on the horizon line, a small green patch shimmers and distorts in the rising heat, small enough to be ambiguous. Strong contre-jour, heavy atmospheric haze, layered depth, warm desaturated palette.
  ```
- **Réglages** : 1536×864. La tache verte doit rester petite : rejeter tout tirage où l'oasis est déjà identifiable.
- **Fichier** : `—` · **Seed** : `—`

### `DEC_oasis_large`
- **Statut** : ⬜ · **Plans** : 70 · **Dérivé de** : —
- **Description canonique** : An oasis in late afternoon, low sun raking through a dark canopy, grasses burning green against deep shadow, a still pool mirroring the sky. Saturated and deep — a different world from the desert.
- **Prompt Z-Image** :
  ```text
  Wide shot of a desert oasis in late afternoon, photorealistic, cinematic. Low sun rakes in from the left through a dark canopy of date palms, throwing long visible shafts of light across the humid air and igniting the tall grasses into bright rim-lit green against deep shadow. A still pool fills the lower right of the frame, mirroring the bright sky and the lit fronds in saturated greens and gold. Layers of vegetation recede into soft haze behind, dense and deep. Strong contrast between the dark canopy and the burning highlights, rich saturated colour, asymmetric composition weighted to the right, vegetation and water filling the frame with sand visible only at the extreme edges.
  ```
- **Réglages** : 1536×864. **Sert de première frame exacte du plan 70** : la composition doit être définitive.
- **Note** : le brief précédent listait des contenus — palmiers, bassin, herbes — et produisait une image d'inventaire en lumière plate. Le « wouaw » d'une oasis ne vient pas de la végétation mais de la **lumière** : contre-jour bas, canopée sombre, herbes en liseré, rayons visibles. Le plan doit trancher avec vingt-cinq secondes d'ocre monochrome ; s'il partage la palette du désert, il a échoué même s'il est joli.
- **Fichier** : `—` · **Seed** : `—`

### `DEC_oasis_vue_aerienne`
- **Statut** : ⬜ · **Plans** : 50 · **Dérivé de** : — (génération directe)
- **Description canonique** : The oasis seen from high above, straight down — dense palm canopies, wide channels of still water, clearings of grass, running to every edge of the frame with no end in sight, desert sand at one edge only.
- **Prompt Z-Image** :
  ```text
  Aerial view looking straight down from high above a vast desert oasis, photorealistic, cinematic. Dense canopies of date palms in saturated green fill the frame, threaded by wide channels of still water that catch the sky in bright mirrored strips, with clearings of tall grass between them. Pale desert sand meets the vegetation along the left edge of the frame only; everywhere else the green runs unbroken to the edges with no end in sight. Late afternoon light rakes in low from the left, cutting long shadows between the palms and igniting the water.
  ```
- **Réglages** : 1536×864
- **Note** : le sable au bord gauche est essentiel. Sans point de comparaison, une immensité verte n'est qu'une texture — c'est le désert qui la rend immense.
- **Fichier** : `—` · **Seed** : `—`

### `DEC_oasis_depuis_dune` — *retiré*
- **Statut** : ⛔ retiré du découpage (v0.8)
- **Motif** : le plan 80 est devenu une entrée latérale par la lisière, la vue depuis la dune n'est plus cadrée.
- Conservé pour mémoire : ne pas le reproduire sans raison de le réintroduire.

### `DEC_oasis_lisiere`
- **Statut** : ⬜ · **Plans** : 90, 100 · **Dérivé de** : — (génération directe)
- **Description canonique** : The boundary where open sand meets the thick grass of the oasis, seen low from the sand side, palms rising beyond.
- **Prompt Z-Image** :
  ```text
  Low lateral shot of the boundary where open desert sand meets the thick grass of an oasis, photorealistic, cinematic. The camera sits low on the sand side, close to the ground. A sharp irregular line crosses the middle of the frame where bare rippled sand gives way to dense tall grass, individual blades rim-lit by low sun from behind. Date palms rise beyond the grass line into a bright hazy sky. Warm backlight behind, cool green fill in front, shallow depth of field on the near sand.
  ```
- **Réglages** : 1536×864
- **Note** : même raison — la lisière est un autre point de vue, pas une retouche de l'oasis large.
- **Fichier** : `—` · **Seed** : `—`

### `DEC_oasis_bokeh`
- **Statut** : ⬜ · **Plans** : 120 · **Dérivé de** : `DEC_oasis_large`
- **Description canonique** : Dense oasis foliage rendered entirely out of focus, wide soft green bokeh with bright highlights between the leaves.
- **Édition Qwen** — source : `DEC_oasis_large`
  ```text
  Throw the entire image completely out of focus into wide soft green bokeh.
  Keep bright circular highlights where sunlight passes between the leaves.
  ```
- **Fichier** : `—` · **Seed** : `—`

---

# Débris — dérivés du master, aucun design neuf

> Méthode commune : repartir du master ou d'un détail du colosse et le repasser en édition avec « sectionné, à demi enseveli, érodé, immobile depuis des siècles ». Varier réellement les poses et les états d'ensablement — Z-Image Turbo ne produira pas cette variation tout seul.

### `DEBRIS_main_brisee_paume_ciel` ⚠️
- **Statut** : ⬜ · **Plans** : 10 · **Dérivé de** : `CHAR_colosse_main_gauche_ouverte`
- **Critique** : prop clé — et sa production dépend de l'asset critique du plan 100
- **Description canonique** : A broken mechanical hand lying palm-up in the sand, fingers half open, joints eroded, the palm cavity half filled with drifted sand. Same hand model as the colossus.
- **Édition Qwen** — source : `CHAR_colosse_main_gauche_ouverte`
  ```text
  Place the hand lying in desert sand, severed at the wrist, palm turned up toward the sky, fingers half open and frozen in place.
  Erode the plating and the joints as if it had been exposed for centuries, and fill the palm cavity halfway with drifted sand.
  Relight with hard low raking sunlight from the right.
  ```
- **Note** : c'est la rime d'ouverture et de fermeture du film. Le modèle de main doit rester identifiable comme le même — c'est la raison de la dérivation.
- **Fichier** : `—` · **Seed** : `—`

### `DEBRIS_carcasses_ensablees`
- **Statut** : ⬜ · **Plans** : 10 · **Dérivé de** : `CHAR_colosse_master`
- **Description canonique** : Two or three colossus carcasses half buried in dunes, corroded plating and structural limbs emerging from the sand, varied poses.
- **Édition Qwen** — source : `CHAR_colosse_master`, **trois passes distinctes** :
  ```text
  1. Lay the machine face down in the dunes, buried to the shoulders, only the upper back and one arm emerging from the sand, plating corroded and worn smooth.
  2. Lay the machine on its side, buried to the waist, one bent leg and the ribcage structure emerging, plating split open along the seams.
  3. Sit the machine upright and collapsed, buried to the chest, head missing, one arm reaching sideways out of the sand.
  ```
- **Note** : trois prompts réellement différents, pas trois seeds. C'est l'asset où la faible variance de Z-Image se paie comptant. Sobriété : pas de champ de bataille, pas de fumée, pas de cratère.
- **Fichier** : `—` · **Seed** : `—`

### `DEBRIS_tete_sectionnee` — *retiré*
- **Statut** : ⛔ retiré du découpage (v0.7)
- **Motif** : le plan 20 a été recentré sur le seul passage du colosse. La tête meublait le cadre et concurrençait sa masse.
- Conservé ici pour mémoire : ne pas le reproduire si le plan 20 évolue à nouveau sans raison de le réintroduire.

### `DEBRIS_carcasse_horizon`
- **Statut** : ⬜ · **Plans** : 30 · **Dérivé de** : `DEBRIS_carcasses_ensablees`
- **Description canonique** : A single broken hull silhouette resting on the far horizon line, softened by haze, readable as a shape rather than a detail.
- **Édition Qwen** — source : `DEBRIS_carcasses_ensablees`
  ```text
  Push the carcass far back onto the horizon line so it occupies a very small part of the frame.
  Soften it with heavy atmospheric haze until it reads as a single dark broken silhouette.
  ```
- **Fichier** : `—` · **Seed** : `—`

---

# Frames d'ancrage — composites pour les plans 10 à 40

> Ces quatre images ne sont pas des références de sujet : ce sont les **premières frames exactes** de leur plan, en mode ancrage par frame. Le cadrage n'est donc plus négocié avec le modèle vidéo, il est donné.
>
> Elles se fabriquent en **multi-image avec Qwen 2511** (jusqu'à 3 sources), à partir d'assets déjà validés. Ratio **1536×864**, jamais carré : une frame d'ancrage porte la composition du plan.
>
> C'est le remède direct au problème d'échelle — un modèle vidéo ramène toujours le sujet vers le centre et vers l'avant, mais il ne discute pas une première frame.

### `FRAME_p10_debut`
- **Statut** : ⬜ · **Plan** : 10 (première frame)
- **Dérivé de** : `DEC_desert_empreintes_sol`
- **Édition Qwen**
  ```text
  Tilt the view down into a steep high angle looking at the sand from above, keeping the line of enormous footprints running away through the frame.
  Remove the horizon and the sky from the frame so only sand and footprints are visible.
  ```
- **Note** : cadre volontairement vide — ni main, ni colosse, ni horizon. C'est tout l'intérêt de l'ouverture : le plan commence sur des traces sans montrer ce qui les a laissées.
- **Fichier** : `—` · **Seed** : `—`

### `FRAME_p10_fin`
- **Statut** : ⬜ · **Plan** : 10 (dernière frame)
- **Sources** : `DEC_desert_empreintes_sol` + `DEBRIS_main_brisee_paume_ciel` + `CHAR_colosse_dos_debout`
- **Édition Qwen (multi-image)**
  ```text
  Place the broken hand along the bottom edge of the frame in the immediate foreground, lying palm-up in the sand and cut off by the lower frame edge.
  Place the walking machine at the very end of the footprint line on the horizon, seen from behind, no taller than one twentieth of the frame height, softened by heat haze with its glowing fissures still visible as small points of light.
  Keep the footprint line running from the foreground to the horizon and the low raking light from the right.
  ```
- **Note** : c'est cette image qui verrouille l'apparition du colosse — sa taille, sa position, son canon. Sans elle, le modèle invente la fin du plan. Si le colosse ressort trop grand, le réduire encore : trop petit se corrige au montage, trop gros ne se corrige pas.
- **Fichier** : `—` · **Seed** : `—`

### `FRAME_p20_debut`
- **Statut** : ⬜ · **Plan** : 20 (première frame)
- **Sources** : `DEC_desert_sol_contreplongee` + `CHAR_colosse_master`
- **Édition Qwen (multi-image)**
  ```text
  Place the machine in the middle distance walking straight toward the camera, seen head-on, its full body in frame with the cannon arm at its right side and the glowing fissures visible.
  Keep the camera at sand level with coarse grains sharp in the foreground and pale hot sky filling the upper frame.
  ```
- **Fichier** : `—` · **Seed** : `—`

### `FRAME_p20_fin`
- **Statut** : ⬜ · **Plan** : 20 (dernière frame)
- **Sources** : `DEC_desert_sol_contreplongee` + `CHAR_colosse_dos_debout`
- **Édition Qwen (multi-image)**
  ```text
  Place the machine seen from behind, walking away from the camera in the middle distance, its cannon arm visible at its right side and a line of fresh footprints in the sand behind it.
  Keep the camera low near the sand with the pale sky above.
  ```
- **Note** : le canon doit être lisible sur les deux frames. C'est le seul détail qui certifie qu'on voit le même colosse à l'entrée et à la sortie du passage.
- **Fichier** : `—` · **Seed** : `—`

### `FRAME_p30_debut`
- **Statut** : ⬜ · **Plan** : 30 (première frame)
- **Sources** : `CHAR_colosse_buste_marche` + `DEC_desert_panoramique` + `DEBRIS_carcasse_horizon`
- **Édition Qwen (multi-image)**
  ```text
  Place the machine walking in profile toward the right of the frame, framed at chest height and seen slightly from below, its plating filling most of the image with the cannon arm swinging at its right side and the fissures glowing.
  Place the broken hull far away in the background haze behind it, small and motionless.
  Keep the dune field and hazy horizon sliding past, lit by hard raking sunlight from the right.
  ```
- **Fichier** : `—` · **Seed** : `—`

### `FRAME_p30_fin`
- **Statut** : ⬜ · **Plan** : 30 (dernière frame)
- **Sources** : `FRAME_p30_debut` + `PROP_oiseau_proche`
- **Édition Qwen (multi-image)**
  ```text
  Bring the close bird across the frame so its blurred dark wing covers the machine completely, filling almost the entire image.
  Keep the camera position, the angle and the background light exactly as in the first image.
  ```
- **Note** : **à produire en même temps que `FRAME_p40_debut`, depuis la même base.** Les deux images sont le même instant à un souffle près — l'oiseau qui bouche, puis l'oiseau qui dégage. Toute différence de position de caméra fera apparaître la coupe.
- **Fichier** : `—` · **Seed** : `—`

### `FRAME_p40_debut`
- **Statut** : ⬜ · **Plan** : 40 (première frame)
- **Sources** : `FRAME_p30_fin`
- **Édition Qwen**
  ```text
  Move the blurred bird toward the left edge of the frame so it is clearing out of shot, uncovering the machine walking toward the right.
  Keep the camera position, the angle and the background light exactly as in the source.
  ```
- **Note** : image jumelle de `FRAME_p30_fin`. C'est le raccord invisible entre les deux plans.
- **Fichier** : `—` · **Seed** : `—`

### `FRAME_p40_fin`
- **Statut** : ⬜ · **Plan** : 40 (dernière frame)
- **Sources** : `CHAR_colosse_buste_arret` + `DEC_desert_horizon_oasis`
- **Édition Qwen (multi-image)**
  ```text
  Place the machine halted at the left edge of the frame, out of focus, its head turned to the right toward the horizon, sand pouring from its shoulders.
  Keep the desert horizon open across the frame with the small green patch shimmering far away on the right, held in sharp focus.
  ```
- **Note** : le colosse doit rester **hors centre, à gauche, et flou**. C'est ce que le modèle ne ferait jamais spontanément, et c'est tout le sens du plan : il n'est plus le sujet, l'oasis l'est. Le sens compte — tout va vers la droite depuis le plan 30.
- **Fichier** : `—` · **Seed** : `—`

### `FRAME_p50_aerien`
- **Statut** : ⬜ · **Plan** : 50 (première frame)
- **Sources** : `DEC_oasis_vue_aerienne` + `PROP_oiseaux_vol`
- **Édition Qwen (multi-image)**
  ```text
  Place the flock of birds flying over the oasis seen from directly above, small against the canopies below, with their shadows falling on the palms.
  Keep the overhead view, the desert sand along the left edge and the low raking light unchanged.
  ```
- **Fichier** : `—` · **Seed** : `—`

### `FRAME_p70_fin`
- **Statut** : ⬜ · **Plan** : 70 (dernière frame)
- **Sources** : `FRAME_p40_fin` + `CHAR_colosse_buste_marche`
- **Édition Qwen (multi-image)**
  ```text
  Bring the machine into sharp focus and move it further into the frame, mid-stride and walking toward the right, its head still turned toward the distant green patch.
  Keep the camera position, the horizon and the small green patch exactly as in the first image.
  ```
- **Note** : dérive de la dernière frame du plan 40. C'est ce qui garantit qu'on reprend exactement là où on l'avait laissé.
- **Fichier** : `—` · **Seed** : `—`

### `FRAME_p80_debut`
- **Statut** : ⬜ · **Plan** : 80 (première frame)
- **Sources** : `DEC_oasis_large` + `CHAR_colosse_master`
- **Édition Qwen (multi-image)**
  ```text
  Lower the camera to the surface of the water, looking slightly upward across the pool, so still water fills the lower half of the frame and reflects the canopy, with palms rising on both sides and a dune visible beyond the far bank.
  Place the machine standing in the far distance on the other side of the water, small enough to be seen in full figure from head to feet, its cannon arm at its right side and its fissures glowing.
  Keep the low warm backlight raking through the palms.
  ```
- **Note** : le colosse doit être **entier et petit**. C'est la seule image du film où on peut le mesurer, et c'est ce qui rend mesurable ce qui suit : dans la dernière frame, le cadre ne le contient plus.
- **Fichier** : `—` · **Seed** : `—`

### `FRAME_p80_fin`
- **Statut** : ⬜ · **Plan** : 80 (dernière frame)
- **Sources** : `FRAME_p80_debut` + `CHAR_colosse_pied_contreplongee`
- **Édition Qwen (multi-image)**
  ```text
  Place two enormous armoured feet standing motionless in the shallow water, flat on the bottom and side by side, both legs vertical and parallel, level with each other and facing the camera, weight evenly on both, filling the lower half of the frame, the legs rising out of the top of the frame so the body is never visible.
  Add water swirling and settling around the submerged soles, with ripples spreading outward toward the camera.
  Keep the camera position, the palms, the dune beyond and the low warm backlight exactly as in the first image.
  ```
- **Statut de production** : 🟡 première version tirée — à retirer en lumière basse et chaude, la version actuelle est en plein midi et ne raccorde pas avec les plans 50 à 70.
- **Note** : **le corps ne doit jamais entrer dans le cadre.** Les jambes sortent par le haut. Rejeter tout tirage où l'on devine le torse : c'est tout l'enjeu du plan.
- **Ne jamais écrire « walking » ici.** Le mot produit une foulée, un pied devant l'autre, et aucune formulation de la pose d'arrêt ne le contrebalance. L'arrivée se raconte par les empreintes qui s'achèvent aux pieds, pas par le mouvement.
- Vérifier l'orientation des semelles : il entre par la gauche et regarde vers la droite, comme depuis le plan 30.
- **Fichier** : `—` · **Seed** : `—`

### `FRAME_p90_debut`
- **Statut** : ⬜ · **Plan** : 90 (première frame)
- **Sources** : `FRAME_p80_fin`
- **Édition Qwen**
  ```text
  Move the camera lower and closer to the feet, and turn it to a side view so one leg is nearer the camera than the other, keeping the water around them and the palms behind.
  Keep the same lighting and the same time of day, and keep the body out of the frame above.
  ```
- **Note** : ce n'est plus un raccord dans l'axe mais un changement de place — un resserrement sur des pieds ne donnerait que des pieds. Même lieu, même lumière, caméra déplacée.
- **Fichier** : `—` · **Seed** : `—`

### `FRAME_p90_fin`
- **Statut** : ⬜ · **Plan** : 90 (dernière frame)
- **Sources** : `FRAME_p90_debut` + `CHAR_colosse_agenouillement`
- **Édition Qwen (multi-image)**
  ```text
  Put the machine on one knee in the shallow water so that its knee breaking the surface, its closed left fist held just above the water and its lowered head all come down into the frame from above, the head turned down toward its own hand.
  Keep the cannon arm hanging at its side without touching the water.
  Keep the camera position, the water and the lighting exactly as in the first image.
  ```
- **Note** : c'est l'image du film. Il était trop grand pour tenir dans le cadre ; il y entre en pliant le genou.
- **Fichier** : `—` · **Seed** : `—`

### `PROP_oiseau_proche`
- **Statut** : ⬜ · **Plans** : 30, 40 (via les frames de raccord) · **Dérivé de** : `PROP_oiseaux_vol`
- **Description canonique** : A single bird passing extremely close to the lens, its dark wing sweeping the full width of the frame in heavy motion blur.
- **Édition Qwen** — source : `PROP_oiseaux_vol`
  ```text
  Bring one bird extremely close to the camera so its dark wing sweeps across the full width of the frame in heavy motion blur, filling most of the image.
  Keep the same bird species, plumage and wing shape as in the source.
  ```
- **Note** : c'est le volet de raccord entre les plans 30 et 40. Même oiseau des deux côtés de la coupe, sinon le raccord se voit.
- **Fichier** : `—` · **Seed** : `—`

### `PROP_oiseaux_vol`
- **Statut** : ⬜ · **Plans** : 40 · **Dérivé de** : —
- **Description canonique** : A loose formation of small dark migrating birds in sustained flight, steady wingbeats, lit from above.
- **Prompt Z-Image** :
  ```text
  A loose formation of small dark migrating birds in sustained flight across an open ochre sky, photorealistic, cinematic. Wings extended mid-beat, the birds spread in a ragged diagonal line, each one sharply defined against the bright sky. Lit from above and slightly behind, high thin clouds in the background.
  ```
- **Réglages** : 1536×864
- **Fichier** : `—` · **Seed** : `—`

---

# Journal de production

*(à remplir au fil des passes : ce qui a été validé, ce qui a résisté, ce qui remonte vers la fiche ou le scénario)*
