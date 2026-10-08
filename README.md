# DASE Beamer template

A local DASE fork of [VincentXWD/hku_beamer_template](https://github.com/VincentXWD/hku_beamer_template) for the Department of Data Science and Engineering, HKU School of Engineering. The original repository is kept as the `upstream` Git remote so future improvements can be compared or merged deliberately.

The DASE fork keeps the upstream repository's modular example files and assets, while `template.tex` is the new canonical entry point. It uses the supplied HKU Engineering and DASE marks, a restrained DASE purple accent, and supporting colours sampled from the HKU crest.

## Compile

From this directory, run either:

```bash
pdflatex template.tex
```

or:

```bash
lualatex template.tex
```

The included `template.tex` is a visual sample deck. Replace its metadata and slide content with your presentation. The theme is local, so `beamerthemeDASE.sty` should stay beside the source file. The copied assets are in `assets/`:

- `HKU_Engineering.png` — supplied Faculty of Engineering mark used on the title and closing slides.
- `HKU_English_logo.png` — supplied HKU English mark for optional use in custom layouts.
- `DASE.svg` — supplied DASE vector artwork kept with the template for future vector workflows.
- `DASE.png` — compile-ready raster export of the supplied DASE mark, used by the theme.
- `HKU_crest_bw.png` — transparent monochrome crest prepared from the supplied `2a.pdf` artwork for watermark use.
- `HKU_crest_white.png` — transparent white crest for watermark use on dark cover pages.
- `images/2a.ai.ps` and `images/4a.jpg` — supplied source branding references retained in the fork.

## Design choices

- `aspectratio=169` gives a current presentation format.
- A warm off-white canvas and dark ink keep body text readable on projectors and video calls.
- DASE purple carries structure; the HKU crest colours are accents for diagrams, blocks, and emphasis.
- Section pages, title pages, footers, blocks, lists, tables, and simple diagram cards are defined in the theme file.
- The monochrome HKU crest from the supplied 2a branding artwork appears as a large, low-contrast watermark on title, section, and closing pages.
- Cover and closing pages use a DASE purple field to the right of the orange divider, with light typography for contrast.
- Title, section, and closing pages share a shallow, left-pointing chevron with an orange edge and its apex 65% down the slide. Section pages stay light; title and closing pages use purple.

If you need a different department name or a dark title, edit the metadata in `template.tex` and the colour definitions near the top of `beamerthemeDASE.sty`.

To see the source relationship:

```bash
git remote -v
git log --oneline --decorate -5
```

The initial commit is inherited from the upstream HKU template; the DASE changes are recorded in the local fork commit on top of it.
