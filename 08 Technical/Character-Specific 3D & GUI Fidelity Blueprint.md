---
title: Character-Specific 3D & GUI Fidelity Blueprint
type: spec
status: active
tags:
  - oz
  - oz/characters
  - oz/gui
  - oz/art
  - oz/3d
updated: 2026-11-23
---

# Character-Specific 3D & GUI Fidelity Blueprint

This document maps all **20 approved Character, Subcharacter, Enemy, and Boss design sheets** (`10 Prompt Libraries/Image Generation/Generated References/`) into exact **3D mesh/shader construction specs** and **character-specific GUI treatments** (HUD party medallions, Dialogue portraits, Grimoire spreads, Boss HUD crests, and Tailor of Vices turntable previews).

---

## 1. Playable Party (Main Cast — 7 Sheets)

| Character | Reference Sheet | Signature 3D Silhouette & Shader Details | Character-Specific GUI Treatment |
|---|---|---|---|
| **Dorothy Gale (Oz Seeker)** | `Characters/char_05_dorothy_seeker.jpg` | Procedural royal-blue & white gingham check shader; dark-plum velvet corset waist-cincher with hammered-gold buckle & back bow; double white lace petticoat + dark-plum underskirt; braided pigtails with blue ribbons; mirror-polished Silver Shoes with instep filigree buckles; woven wicker basket. | Center Lead portrait (`dorothy.png`) in glowing gold ring; Dialogue medallion; default Boutique turntable model. |
| **Dorothy Gale (Red Seeker Couture)** | `Characters/char_03_dorothy_red_seeker.jpg` | Crimson-obsidian velvet corset with gold cross-lacing; black scalloped lace hem; silver heeled boots; braided crimson Lace Whip. | Unlocked via *The Tailor of Vices*; swaps portrait badge to `dorothy_red.png` when equipped. |
| **Dorothy Gale (Kansas Monochrome)** | `Characters/char_07_dorothy_kansas.jpg` | Sepia-grey gingham pinafore, scuffed lace-up prairie boots, cloth-lined wicker basket (greyscale shader active in L1 & L7). | Monochrome desaturated HUD frame & silver-ash vitality roses in Kansas. |
| **The Scarecrow** | `Characters/char_01_scarecrow.jpg` | Button-stitched X-eyes & stitched grin; slouching hat with brass gear badge & tucked raven feather; golden straw collar & cuff tufts; crossed rope bandolier + brass belt buckle; gnarled walking staff with hanging brass key. | Orbiting HUD medallion (`scarecrow.png`), Dialogue portrait, Grimoire Companion spread, Boutique burlap/leather/obsidian skins. |
| **The Tin Woodman** | `Characters/char_02_tin_woodman.jpg` | Riveted silver-steel boiler plate; center gilded filigree cage housing a glowing crimson anatomical clockwork heart; glowing amber-gold eyes; twin brass-and-iron steam exhaust pipes on back; spiked pauldrons; tilted funnel cap; engraved woodman's axe. | Orbiting HUD medallion (`tinman.png`), Dialogue portrait, metallic armor-break UI indicator. |
| **The Cowardly Lion** | `Characters/char_04_cowardly_lion.jpg` | Horizontal feline anatomy (broad ribcage, lumbar waist, haunches); 2-tier 18-tuft windswept golden mane; ornate dark-leather & antique-gold chest harness with crimson-ribboned golden Courage Medal & ruby center. | Orbiting HUD medallion (`lion.png`), Dialogue portrait, primal gold Boutique harness. |
| **Toto** | `Characters/char_06_toto.jpg` | Scruffy dark-brindle Cairn terrier with perky triangular ears; dark leather collar with gleaming five-point sterling-silver star charm; sits snugly inside Dorothy's carried wicker basket in Kansas. | Orbiting HUD medallion (`toto.png`), Dialogue portrait (`*yip*`), Boutique silver-spiked collar. |

---

## 2. Subcharacters, Story NPCs & Animals (7 Sheets)

| Character | Reference Sheet | Signature 3D Silhouette & Shader Details | Character-Specific GUI Treatment |
|---|---|---|---|
| **Aunt Em** | `Subcharacters/npc_04_aunt_em.jpg` | Monochrome 1900s farm matriarch: neat grey hair bun, cameo neck brooch, stained pocketed work apron over dark prairie skirt, lace-up work boots. | Monochrome Dialogue portrait (`aunt_em.png`) in L1 & L7 Kansas. |
| **Uncle Henry** | `Subcharacters/npc_02_uncle_henry.jpg` | Monochrome 1900s farmer: wide-brimmed felt hat, thick mustache, plaid rolled-sleeve shirt, denim overalls with brass clasps, sturdy boots. | Monochrome Dialogue portrait (`uncle_henry.png`) in L1 & L7 Kansas. |
| **Locasta (Good Witch of the North)** | `Subcharacters/npc_06_locasta.jpg` | Shimmering white-and-silver star-embroidered Victorian ballgown; high scalloped white lace ruff collar; glowing celestial Northern Star halo ring with 6 starlight orbs behind her head; silver star-tipped wand. | Dialogue portrait (`locasta.png`) framed in silver-gold brass in Munchkinland. |
| **Glinda (Good Witch of the South)** | `Subcharacters/npc_03_glinda.jpg` | Flowing auburn curls; ruby-rose & white Victorian ballgown with gold filigree trim; high lace ruff collar; 5-point gold crown with rose-quartz gem; golden rose-quartz star scepter. | Dialogue portrait (`glinda.png`) in Glinda's Ruby Court. |
| **Oscar Diggs (The Humbug Wizard)** | `Subcharacters/npc_07_oscar_diggs.jpg` | Faded pinstripe tailcoat & embroidered vest; silk top hat with tucked *Omaha Fair* ticket; round brass spectacles; dark showman mustache; brass megaphone & geared lever console behind parting crimson velvet curtains. | Dialogue portrait (`wizard.png`) after curtain reveal in Emerald Palace. |
| **Field Mice Team & Cart** | `Subcharacters/npc_05_field_mice_cart.jpg` | Four brown-and-white field mice wearing crimson-leather brass harnesses hitched to a lantern-lit wooden spoked-wheel cart. | World badge & Poppy Field rescue compass target. |
| **Kansas Prairie Poultry** | `Subcharacters/npc_01_kansas_poultry.jpg` | Speckled monochrome hens & strutting rooster with animated pecking/bobbing gait (`chicken_actor.gd`) inside the swinging-gate coop run & interior. | Ambient life in L1 & L7 Kansas Chicken Coop. |

---

## 3. Enemies & Multi-Phase Bosses (6 Sheets)

| Enemy / Boss | Reference Sheet | Signature 3D Silhouette & Shader Details | Character-Specific GUI Treatment |
|---|---|---|---|
| **Munchkin Guild Enforcer** | `Enemies/enemy_05_munchkin_enforcer.jpg` | Uncanny cracked pale porcelain smiling face with rosy cheeks; ruffled cream neck collar; mint-and-rose striped waistcoat; tilted rose pointed hat with brass bell; gold-filigree short hatchet. | Bestiary portrait (`munchkin_enforcer.png`) in Oz Grimoire `[J]`. |
| **Lollipop Guild Marshal (Boss)** | `Enemies/enemy_06_marshal_boss.jpg` | Oversized armored captain: dark-iron & candied-crimson spiked pauldrons; plumed shako hat with lollipop swirl & skull badge; crimson sash; massive serrated ceremonial cleaver. | Bestiary portrait (`marshal.png`) + Dedicated Boss Health/Phase HUD bar. |
| **The Orchard Guardian (Living Tree)** | `Enemies/enemy_01_living_tree.jpg` | Gnarled ancient oak with glowing amber eye-knots & mouth cavity; twisted articulated throwing arms hurling spiked thorny seed-pods; solid fallen timber trunk on defeat. | Bestiary portrait (`living_tree.png`) in Oz Grimoire. |
| **Winged Monkey (Sky-Stalker)** | `Enemies/enemy_03_winged_monkey.jpg` | Leathery bat-feathered wings, riveted dark-iron pauldrons, brass claw gauntlets, diving ambush perches in Winkie Castle. | Bestiary portrait (`winged_monkey.png`) in Oz Grimoire. |
| **Wicked Witch of the West (Boss)** | `Enemies/enemy_04_wicked_witch.jpg` | **Baum Canon**: Chalk-pale gaunt aristocratic face; forged-iron eyepatch with diagonal strap; crown-banded tattered black hat; silver-grey braid; dark Victorian lace mourning gown; iron-ribbed black umbrella-staff topped with a sculpted raven head. | Dialogue portrait (`wicked_witch.png`) + Bestiary portrait + 3-Phase Boss Health Bar. |
| **Oz Volumetric Hologram (Boss)** | `Enemies/enemy_02_oz_hologram.jpg` | Colossal translucent glowing emerald wireframe wizard head crackling between twin tall brass Tesla coils & giant interlocking brass projector gears. | Bestiary portrait (`oz_hologram.png`) + Emerald Palace Boss HUD. |

---

## 4. Next-Pass GUI Integration Checklist (Driven by Future Generated Sheets)
As Buildings (`03`), Key Objects (`04`), and Environments (`05`) sheets arrive:
1. **Tailor of Vices (`shop_menu.gd`)**: Replace procedural vector icons with cropped `128×128` painted icons from generated couture/weapon sheets.
2. **Shattered Memories (`grimoire_menu.gd`)**: Display cropped painted artifact illustrations (Tarnished Locket, Weather Ledger, Cracked Mask, Debt Book, Green Spectacles) on the right Grimoire page.
3. **Act Loading / Transition Cards (`level_transition.gd`)**: Display atmospheric 16:9 biome illustrations during level transitions.
