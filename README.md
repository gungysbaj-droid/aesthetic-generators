# aesthetic-generators

Reproductions of niche aesthetic-generation websites, built so Claude (or any
LLM writing front-end code) can lift the techniques and drop them into real
websites. Every generator is a single self-contained `index.html` - no
dependencies, no build step. Open the file in a browser and it works.

## Why this exists

The originals are scattered one-off tools, each good at exactly one effect.
This repo consolidates the effects as clean, documented, dependency-free
reference implementations with tunable CONFIG blocks, so they can be studied,
copied, and remixed.

## The generators

| # | Folder | Reproduces | Original site | Effect |
|---|--------|------------|---------------|--------|
| 01 | `generators/01-ascii-magic` | ASCII Magic | ascii-magic.com | Image to ASCII art (charsets, color modes, PNG/TXT export) |
| 02 | `generators/02-dither` | Dither It | ditherit.com | Bayer / Floyd-Steinberg / Atkinson image dithering |
| 03 | `generators/03-glitch-mosh` | PhotoMosh (now Mosh) | photomosh.com | RGB shift, slice displacement, pixel sorting, scanlines |
| 04 | `generators/04-trianglify` | Trianglify | trianglify.io | Low-poly triangle backgrounds (seeded) |
| 05 | `generators/05-svg-waves` | Get Waves / SVG Wave | getwaves.io, svgwave.in | Layered SVG wave sections |
| 06 | `generators/06-blob-maker` | Blobmaker | blobmaker.app | Organic SVG blob shapes |
| 07 | `generators/07-mesh-gradient` | Mesh Gradient | meshgradient.com | Soft mesh gradients as pure CSS |
| 08 | `generators/08-hero-patterns` | Hero Patterns | heropatterns.com | Repeatable SVG background patterns |
| 09 | `generators/09-neumorphism` | Neumorphism.io | neumorphism.io | Soft-UI box-shadow CSS |
| 10 | `generators/10-glassmorphism` | Glassmorphism | glassmorphism.com | Frosted-glass panel CSS |
| 11 | `generators/11-stripes` | Stripes Generator | stripesgenerator.com | CSS stripe backgrounds, optional animation |
| 12 | `generators/12-duotone` | Duotones | duotones.co | Two-color image remap |
| 13 | `generators/13-grain-noise` | fffuel nnnoise | fffuel.co/nnnoise | SVG turbulence grain overlay |

## How Claude should use this

1. Each folder is one `index.html`. Everything is inline - markup, styles,
   and the generator core.
2. Look for the `CONFIG` comment block near the top of each script. Those
   are the meaningful knobs (palettes, ramps, resolutions, passes).
3. The reusable core in each file is a small function (`imageToAscii`,
   `dither`, `makeBlob`, `buildWaves`, `duotone`, ...). Lift the function,
   not the page.
4. Outputs are designed to be pasted: "Copy SVG" / "Copy CSS" buttons emit
   ready-to-use declarations.

## Licensing and attribution

Every file here is a clean-room reimplementation: the effect was reproduced
from scratch, and no source code, path data, or assets were copied from the
original sites. Effects and algorithms (dithering matrices, Chaikin
smoothing, feTurbulence grain, soft-UI shadow math) are unprotectable ideas
and standard published techniques. Notes on the originals:

- Trianglify's library is GPL-3.0; this repo deliberately does not use it.
- Hero Patterns (originals) are CC BY 4.0; the tiles here are our own
  simpler patterns, not copied path data.
- ascii-magic.com, photomosh.com, blobmaker.app, meshgradient.com,
  glassmorphism.com, duotones.co, stripesgenerator.com are proprietary
  tools; credit is given by name and URL in each file's header.
- ditherit.com and neumorphism.io are open source; reimplemented anyway to
  keep this repo license-clean.

If you ship something derived from these files, crediting the original tool
by name is the polite thing to do - they earned the niche.

## Live preview

When GitHub Pages is enabled for this repo (Settings > Pages > main),
each generator is live at
`https://gungysbaj-droid.github.io/aesthetic-generators/generators/<folder>/`.
