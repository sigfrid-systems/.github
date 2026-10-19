# Brand assets

Public brand assets for the Sigfrid Systems GitHub organization. This is the organization's only public repository, so these files are the publishable copies of the marks: everything on the profile is fetched from here, never from a private repository.

The marks come in two sets. The files directly under `logo/` are the canonical marks, which suit any context that styles them itself. The files under `logo/github/` are derived from them for inlining in GitHub Markdown, which neither passes the page theme to an image nor keeps inline styles.

## The canonical marks

| File | Use |
| --- | --- |
| `logo/sigfrid-bird.svg` | The bird in its default pose, drawn in `currentColor` on a 1080×1080 viewBox. |
| `logo/sigfrid-bird-animated.svg` | The wing-flap animation, also in `currentColor`. |
| `logo/avatar.svg` | Square avatar on a light radial background, bird in brand gradients. Vector. |
| `logo/avatar-512.png` | 512×512 raster, for the organization avatar and social previews. |
| `logo/avatar-1024.png` | 1024×1024 raster, for high-DPI previews. |

## The GitHub inlining set

GitHub serves README images through a proxy that drops the page theme, so `currentColor` resolves to black whatever the reader's theme. Each file in `logo/github/` therefore sets its own ink, either through a `prefers-color-scheme` media query inside the SVG or as a fixed color:

| File | Ink |
| --- | --- |
| `logo/github/sigfrid-bird.svg` | Default pose, theme-aware. |
| `logo/github/sigfrid-bird-on-light.svg` | Default pose, fixed dark ink for a light background. |
| `logo/github/sigfrid-bird-on-dark.svg` | Default pose, fixed light ink for a dark background. |
| `logo/github/sigfrid-bird-animated.svg` | Animation, theme-aware. |
| `logo/github/sigfrid-bird-animated-on-light.svg` | Animation, fixed dark ink for a light background. |
| `logo/github/sigfrid-bird-animated-on-dark.svg` | Animation, fixed light ink for a dark background. |

GitHub also strips `style` attributes, so CSS cannot size or offset an inlined image. The bird's placement beside a heading is built into the geometry of every file in this set instead: the bird is scaled to 75% of its canvas and offset so that it keeps a right margin from the text and sits slightly below the cap line.

The profile heading combines the animated set with a `<picture>` element, which pins each theme to a fixed-ink source and falls back to the theme-aware file. The `<sub>` element survives GitHub's sanitizer and lowers the image toward the text baseline:

```html
<h1>
  <sub>
    <picture>
      <source media="(prefers-color-scheme: dark)" srcset="…/logo/github/sigfrid-bird-animated-on-dark.svg">
      <source media="(prefers-color-scheme: light)" srcset="…/logo/github/sigfrid-bird-animated-on-light.svg">
      <img src="…/logo/github/sigfrid-bird-animated.svg" alt="" height="36">
    </picture>
  </sub>
  Sigfrid Systems
</h1>
```

## Color system

The full-color avatar uses the Sigfrid tonal palette. The GitHub inlining set uses GitHub's own foreground colors, `#1f2328` on light and `#f0f6fc` on dark, so the bird matches the heading text beside it.

| Element | Base | Range |
| --- | --- | --- |
| Body (primary) | `#0074e1` | `#005db8`–`#2e8bff` |
| Wing (primary, light) | `#5ca3ff` | `#2e8bff`–`#87bbff` |
| Leaf (tertiary) | `#e68600` | `#a45c00`–`#ffb77c` |
| Background (neutral) | `#f8fafd` | `#f8fafd`–`#d6dde2` |

## Trademark

Sigfrid® is a registered trademark. Use the marks as they are, without recoloring, stretching, or recomposing the bird or the avatar; the inks and the placement geometry of the GitHub inlining set are the only sanctioned derivations.
