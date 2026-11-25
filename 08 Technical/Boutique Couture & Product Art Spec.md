# Boutique Couture & Product Art Spec (Phase P3.2)

> **Purpose**: Maps all approved *Tailor of Vices* Boutique couture renders and global dark-storybook moodboards archived in `10 Prompt Libraries/Image Generation/Generated References/Couture/Shop/` directly into `oz/assets/art/icons/shop/` and `oz/ui/widgets/shop_item_icon.gd`.

---

## 1. Global Style Anchor
- `style_00_gothic_couture_moodboard.jpg`: Dark gothic cathedral & Victorian royal couture lighting/palette anchor (deep plum velvet, antique brass filigree, candelit stained-glass chiaroscuro).

## 2. Tailor of Vices — Painted Boutique Product Icons (`oz/assets/art/icons/shop/`)
All 13 `SHOP_CATALOG` items in `oz/systems/save_manager.gd` now render real 256×256 painted product/portrait artwork framed in antique brass inside `ShopItemIcon` (`oz/ui/widgets/shop_item_icon.gd`):

| Reference File | Cropped Icon (`oz/assets/art/icons/shop/`) | Mapped `SHOP_CATALOG` ID(s) |
| :--- | :--- | :--- |
| `shop_dorothy_gingham.jpg` | `dorothy_gingham.png` | `dorothy_gingham` (Prairie Gingham) |
| `shop_dorothy_velvet.jpg` | `dorothy_velvet.png` | `dorothy_velvet` (Velvet Corset Couture) |
| `shop_dorothy_sovereign.jpg` | `dorothy_sovereign.png` | `dorothy_sovereign` (Silver-Lace Sovereign) |
| `shop_dorothy_whip_plus.jpg` | `dorothy_whip_plus.png` | `dorothy_whip_plus` (Lace Whip Mastery) |
| `shop_scarecrow_classic.jpg` | `scarecrow_classic.png` | `scarecrow_classic`, `scarecrow_leather` |
| `shop_scarecrow_obsidian.jpg` | `scarecrow_obsidian.png` | `scarecrow_obsidian` (Obsidian Crowmaster) |
| `shop_tinman_royal.jpg` | `tinman_royal.png` | `tinman_velvet` (Chrome & Crimson Velvet) |
| `shop_lion_primal.jpg` | `lion_primal.png` | `lion_primal` (Primal Gold Harness) |
| `shop_toto_spiked.jpg` | `toto_spiked.png` | `toto_silver_collar` (Silver-Spiked Collar) |
| *(Character Portraits)* | `portraits/{tinman,lion,toto}.png` | `tinman_classic`, `lion_classic`, `toto_classic` |
