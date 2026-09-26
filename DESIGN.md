# Wildflower — Design Language

## Core idea

Wildflower is a dark botanical desktop theme built around one scene: golden blooms held in a shaded canopy. The interface keeps the image's quiet structure—stone, leaf, and stump shadow—then gives flower gold the lead and dusk lilac a measured second voice.

## Emotional target

**Should feel:** shaded, grounded, intimate, and softly luminous: the last light finding flowers beneath a canopy.

**Should not feel:** autumnal brown-orange, purple-dominant, neon, candy-coloured, cozy-rustic, or like a full rainbow of equally loud accents.

## Visual thesis

The wallpaper supplies the material language. Near-neutral canopy and stone form the ground. Flower gold is the visible point of focus; lilac evokes the dusk haze without taking over. Most surfaces stay quiet so the scene remains the desktop's focal image.

This is an image-led interpretation, not a literal pixel trace. No wallpaper filter is applied.

## Source of truth

`backgrounds/01-wildflower.jpg` is the canonical image. The gold `#EED079` was sampled as the median RGB of a broad bright-yellow mask after resizing the image to 1000 × 562. It is an image-inspired sample, not a calibrated physical colour.

Dusk lilac `#C393C1` is a small chroma lift from the earlier `#B79BB5`, retaining its hue and lightness. The brighter lilac `#D2BDD1` remains available for high-contrast border work. Canopy, stone, stump, leaf, and petal shades are hand-art-directed interpretations of the image, not exact pixel samples. Selection moss `#484836` is the median of a broad, shadowed-foliage sample from the resized source image.

`colors.toml` is Omarchy's runtime palette source. `wildflower-base24.yaml` is a named 24-slot companion palette for compatible consumers; Omarchy does not load that YAML directly.

## Palette roles

| Role | Material | Colour | Intended use |
|---|---|---:|---|
| Background | Shadowed canopy | `#252824` | Main desktop ground |
| Raised surface | Stump shade | `#343831` | Cards and raised panels |
| Deep surface | Deep canopy | `#1E211D` | Shell, popups, and notifications |
| Deepest surface | Root shadow | `#181A18` | Launcher and menu surfaces |
| Foreground | Stone petals | `#D3D3CA` | Default readable text |
| Light foreground | Soft petal | `#E3E1D7` | Secondary emphasis |
| Bright foreground | Pollen light | `#F2F0E7` | High-contrast and selected text |
| Primary accent | Flower gold | `#EED079` | Focus, warning, and active emphasis |
| Support accent | Dusk lilac | `#C393C1` | Links, information, and magenta mapping |
| Bright support | Lilac haze | `#D2BDD1` | Brighter border stop and high emphasis |
| Selection | Canopy moss | `#484836` | Selected-row fill |
| Muted text | Quiet stone | `#98998F` | Secondary text and inactive structure |
| Success | Leaf shadow | `#9DA58C` | Success state |
| Error | Worn petal | `#BA8078` | Error state |
| Information | Sage stone | `#A7B0A1` | Quiet cyan/information mapping |

## Colour hierarchy

Gold leads by placement, not by covering large surfaces. Lilac appears often enough to belong—in links, information, ANSI magenta, and supporting focus treatments—but must not become the background or displace pollen as the primary signal. Leaf sage remains a supporting material, not the default ANSI-green identity.

The ANSI mapping is deliberately nonliteral and repeats the flower colour instead of filling a standard rainbow:

| Slot | Wildflower mapping | Intent |
|---|---|---|
| `green` / `color2` / Base24 `base0B` | Pollen gold `#EED079` | Theme-colored terminal/logo accents |
| `yellow` / `color3` / Base24 `base0A` | Pollen gold `#EED079` | Repeat the primary instead of adding another hue |
| `blue` / `color4` / Base24 `base0D` | Canopy stone `#9CA39C` | Quiet neutral |
| `cyan` / `color6` / Base24 `base0C` | Sage stone `#A7B0A1` | Retain the foliage material |
| `magenta` / `color5` / Base24 `base0E` | Dusk lilac `#C393C1` | Keep lilac as the supporting flower/dusk voice |
| `orange` / Base24 `base09` | Dry pollen `#C4AA70` | Warm image-derived support |
| Explicit `success` role | Leaf shadow `#9DA58C` | Use where a consumer supports a separate success colour |

Other slots use the petal, bark, and stone shades above. Some apps use ANSI green for success too, so those consumers will show pollen gold; state labels and icons remain important.

## Wallpaper world

The active set stays in the same botanical, gold-and-lilac world as the canonical image. The other backgrounds may shift the composition or balance of colour, but should still sit beside the dark canopy and muted interface without demanding a new palette.

- Keep `01-wildflower.jpg` unchanged as the defining scene.
- Prefer original high-resolution sources; do not fake-upscale or colour-filter them.
- Let crop and image composition vary; do not force every image into the same treatment.
- Keep image origins and dimensions in `backgrounds/SOURCES.md`.

## Surface language

### Structure

Use near-neutral dark surfaces and stone text for most of the interface. A surface should read through its material/lightness step—not through a large patch of accent colour.

### Focus and selection

The selected menu and launcher rows use a solid canopy-moss fill `#484836` with bright text `#F2F0E7`. The menu's narrow left selection stripe uses the gold-to-lilac border gradient `#EED079` → `#D2BDD1`; the fill itself stays solid. The launcher uses a gold left stripe.

The reference desktop's active window border echoes the gold-to-lilac pairing. Its 3 px frame width is local Hyprland styling, not a required theme installation step.

### Tone and geometry

Let the stock Omarchy layout carry the geometry. This theme changes colour and surface character; it does not require a custom menu plugin, new widget, font install, or altered keybinding. Keep popups and cards dark, edges readable, and accent treatments narrow.

## Surface-by-surface intent

### Omarchy shell

`shell.toml` applies the palette to the bar, popups, tooltip, notifications, launcher, menu, polkit, lock screen, and image picker. Deep canopy and root-shadow surfaces hold the panels together. Gold marks priority; selected labels stay pale and legible.

The menu selection has two separate parts: a solid mauve fill and a gold-to-lilac left stripe. Do not turn the whole selected row into a gradient.

### GTK

GTK views and windows use canopy surfaces with stone foregrounds. Hover and selection use canopy moss; gold is reserved for focus and warning. Destructive states use worn petal red, while success remains subdued foliage.

### Editor and terminal

The Zed theme keeps normal text in stone, comments in quiet stone, functions in flower gold, and keywords in dusk lilac. Green strings, neutral-cyan constants, and stone-blue types stay supporting rather than forming a forced rainbow.

ANSI roles use the mapping above rather than a literal rainbow. In Zed, functions use pollen gold, keywords dusk lilac, strings leaf sage, constants sage stone, and types canopy stone. Bright green repeats pollen light (`#F5E1A1`) so green-labeled terminal art follows the theme; bright yellow uses the same colour.

### Browser

Zen Browser uses canopy and stump shades for toolbar surfaces, stone text, canopy-moss selection, and gold focus. Browser chrome should remain a frame around the page, not a second accent display.

### Discord

Vencord uses Refact0r's Midnight layout with Wildflower's own colour overrides, not Midnight's preset palette. The Midnight stylesheet is imported remotely, so this treatment requires Vencord/Vesktop and network access.

### Visualizer

Cava's eight-stop gradient starts with pollen gold and moves through lilac, stone, foliage, dry pollen, and muted stone. The display can carry more colour than app chrome, but it should still read as one spectrum rather than eight unrelated accents.

### Icons

`icons.theme` requests Yaru-Purple. The icon pack is separate from this theme; icon styling is optional and does not change the palette's lead/support relationship.

## Integration boundaries

| Asset | Role |
|---|---|
| `colors.toml` | Omarchy's runtime palette source |
| `shell.toml` | Omarchy shell surfaces and selected-state styling |
| `gtk.css`, `zed.json`, `zen.css`, `cava_theme` | Optional app-specific theme assets |
| `vencord.theme.css` | Midnight-based Vencord styling with Wildflower colours |
| `wildflower-base24.yaml` | Optional 24-slot palette for compatible tools |

App-specific rendering depends on each app and its theme support. The local Hyprland frame width is separate from these portable theme assets. Wallpapers and the preview are bundled for personal desktop use, separately from the MIT-licensed code; their rights remain with their creators and rights holders. See [`backgrounds/SOURCES.md`](backgrounds/SOURCES.md) for uploader and source-page credits.

## Legibility and accessibility limits

| Pairing | WCAG contrast |
|---|---:|
| Foreground `#D3D3CA` on background `#252824` | 9.90:1 |
| Muted `#98998F` on background `#252824` | 5.18:1 |
| Selected text `#F2F0E7` on selection `#484836` | 8.15:1 |
| Lilac `#C393C1` on background `#252824` | 5.87:1 |
| Error `#BA8078` on background `#252824` | 4.58:1 |
| Success `#9DA58C` on background `#252824` | 5.82:1 |

The error pairing sits near the usual 4.5:1 normal-text baseline. Colour-vision simulation still finds the explicit petal-error and leaf-success hues insufficiently distinct by hue alone; retain labels, icons, or other non-colour cues. These measurements do not certify every app or every rendered state.

## Design guardrails

1. Keep flower gold primary and dusk lilac secondary.
2. Preserve the canonical wallpaper and avoid filters or fake upscaling.
3. Do not turn the theme into a brown-orange forest ramp, a purple desktop, or a forced rainbow.
4. Keep selected-row fills solid; use the gold-to-lilac gradient on the narrow menu stripe, not across the whole row.
5. Treat local compositor preferences and optional app styling separately from portable theme files.

**One-sentence test:** the interface belongs when it feels like stone and leaf shadow, with pollen-gold focus and lilac afterlight.
