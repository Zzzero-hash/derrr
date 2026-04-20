# DERRR brand kit

All assets are editable SVGs. No rasters are committed. Regenerate PNGs on demand.

## Files

Canonical set:

```
assets/
├── banner-v2.svg                     # README header / landing image
├── logo/
│   ├── derrr-logo-primary.svg        # mascot + wordmark, horizontal
│   ├── derrr-icon.svg                # square icon / avatar
│   └── derrr-logo-mono.svg           # single-color, uses currentColor
├── social/
│   └── derrr-social-preview.svg      # 1280×640 Open Graph card
└── diagrams/
    └── derrr-loop.svg                # loop diagram
```

Older `derrr-header*.svg` files are legacy explorations, not the canonical pack.

## Palette

| Phase    | Token       | Hex       |
|----------|-------------|-----------|
| Document | `derrr.d`   | `#7ee787` |
| Execute  | `derrr.e`   | `#f6c177` |
| Review   | `derrr.r1`  | `#ff7b72` |
| Research | `derrr.r2`  | `#ff6ac1` |
| Restart  | `derrr.r3`  | `#a5a1ff` |
| BG base  | `derrr.bg`  | `#0a0712` |
| Ink      | `derrr.ink` | `#c9d1d9` |

Palette is shared across banner, social, logo, and diagram. Don't drift without updating all five.

## Typography

- **Wordmark:** `ui-monospace, "JetBrains Mono", "Fira Code", "SF Mono", Menlo, Consolas, monospace`, weight 900, negative letter-spacing.
- **Body / captions:** `ui-sans-serif, system-ui, -apple-system, "Segoe UI", Inter, sans-serif`.

All type is live SVG `<text>` — not paths. Keep it that way so the files stay editable.

## Quality bar

The pack should read cleanly at a glance.

Prefer:
- fewer decorative lines and frames
- one clear focal point per asset
- logo details that survive small rendering
- diagrams that explain the loop without becoming poster art

If an asset feels crowded, trim it before adding more flourish.

## Mascot rules

The goblin is a working mascot, not a prestige logo. Keep it:

- a little asymmetric (eyes not perfectly aligned, head slightly lumpy)
- visibly drooling *or* holding a clipboard (at least one at all times)
- nerd glasses over the eyes, not floating
- green on dark; never green on green

Do **not** clean him up into a polished SaaS blob. That betrays the voice.

## Mono variant usage

`derrr-logo-mono.svg` uses `currentColor`. Set color via CSS on the host:

```html
<span style="color: #c9d1d9">
  <object data="assets/logo/derrr-logo-mono.svg" type="image/svg+xml"></object>
</span>
```

Or inline and style via the parent element.

## Export recipes

PNGs are not committed. Generate on demand.

### `rsvg-convert` (fast, headless)

```bash
# 1x and 2x icon
rsvg-convert -w 256  assets/logo/derrr-icon.svg          -o derrr-icon@1x.png
rsvg-convert -w 512  assets/logo/derrr-icon.svg          -o derrr-icon@2x.png

# GitHub social preview (1280×640 is the upload target)
rsvg-convert -w 1280 assets/social/derrr-social-preview.svg -o derrr-social-preview.png
```

### `inkscape`

```bash
inkscape assets/social/derrr-social-preview.svg \
  --export-type=png --export-width=1280 \
  --export-filename=derrr-social-preview.png
```

## GitHub social preview

Upload `derrr-social-preview.png` (exported from the 1280×640 SVG) via:
**Repo → Settings → General → Social preview → Upload an image**.

## License

Brand assets are covered by the repo's MIT license. Use them to reference or link DERRR; don't imply endorsement of unrelated projects.
