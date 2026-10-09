# DASE Beamer template

A local DASE fork of [VincentXWD/hku_beamer_template](https://github.com/VincentXWD/hku_beamer_template) for the Department of Data and Systems Engineering, HKU School of Engineering. The original repository is kept as the `upstream` Git remote so future improvements can be compared or merged deliberately.

The DASE fork keeps the upstream repository's modular example files and assets, while `template.tex` is the new canonical entry point. It uses the supplied HKU Engineering and DASE marks, a restrained DASE purple accent, and supporting colours sampled from the HKU crest.

## Use the example deck

Open `template.pdf` for the illustrated guide; edit `template.tex` to reuse its examples. The deck covers:

- A clickable table of contents, theme colours, title/chapter/closing pages, lab branding and chapter progress.
- Standard, example and alert blocks; nested lists; a TikZ diagram; the supplied `images/4a.jpg` with a description; literal code; tables and mathematics.
- Numeric citations, a references page and clickable DOI links.
- Live overflow examples: a long chapter title, slide title/subtitle, an unbroken identifier, block headings and cover/closing fields with their separate limits.
- Exact replacement paths, metadata, copyable slide patterns and the build sequence.

For your own talk, replace the metadata near the top of `template.tex`, overwrite `assets/lab-logo.png`, replace the example sections and frames, and update `bib.bib`. Keep the theme, bundled `truncate.sty` and the tracked branding assets together. Delete the deliberately oversized demonstration chapter and extra cover. Its metadata changes are scoped to that cover frame.

The sample uses `fancyvrb` for literal source examples. The guide-only `guideframe` environment permits displaying a literal `\end{frame}` inside an example; ordinary content uses `frame`, with `[fragile]` when it contains verbatim code. Body content, diagrams and code lines still need to fit their allotted space; automatic ellipses apply to theme text placeholders.

## Compile

The sample includes numeric citations and a references slide, using `biblatex` and Biber. From this directory, run:

```bash
pdflatex template.tex
biber template
pdflatex template.tex
pdflatex template.tex
```

Or use LuaLaTeX:

```bash
lualatex template.tex
biber template
lualatex template.tex
lualatex template.tex
```

Add sources to `bib.bib` and cite them with `\cite{key}`. Citation numbers link to their bibliography entries. The references frame splits into additional slides when needed; rerun Biber after changing citations or bibliography entries.

The included `template.tex` is a visual sample deck. Replace its metadata and slide content with your presentation. Keep `beamerthemeDASE.sty` and `bib.bib` beside the source file. The tracked assets are limited to the files needed by the guide and theme:

- `DASE.svg` — supplied DASE vector artwork kept for future vector workflows.
- `DASE.png` — compile-ready raster export of the supplied DASE mark, used by the theme.
- `lab-logo.png` — transparent “YOUR LAB LOGO HERE” placeholder beneath the DASE mark on title, chapter, and thank-you pages. Replace this file with a PNG that has an alpha channel (RGBA), so the logo has no white rectangle. Remove any background in your image editor and export with transparency enabled: saving or renaming an opaque image as PNG does not remove its background. A PDF without a filled background also works directly. Export SVG artwork to transparent PNG or PDF first; SVG is not loaded directly by this theme. JPEG cannot store transparency. The theme aligns the left edges of the two marks and scales the lab logo to the same width as the DASE mark, preserving its proportions so its height adapts automatically. To use another filename, add `\renewcommand{\daselablogofile}{assets/my-lab-logo.pdf}` after loading the theme.
- `HKU_crest_bw.png` — transparent monochrome crest prepared from the supplied `2a.pdf` artwork for watermark use.
- `HKU_crest_white.png` — transparent white crest for watermark use on dark cover pages.
- `images/4a.jpg` — the image used by the guide's image-and-description example.

## Design choices

- `aspectratio=169` gives a current presentation format.
- A warm off-white canvas and dark ink keep body text readable on projectors and video calls.
- DASE purple carries structure; the HKU crest colours are accents for diagrams, blocks, and emphasis.
- Section pages, title pages, footers, blocks, lists, tables, and simple diagram cards are defined in the theme file.
- The bottom footer shows clickable slide dots grouped by chapter: completed slides are purple, the current slide is orange, and upcoming slides are outlined. The footer uses one line: author and institute, progress dots, the current chapter name, and the content-slide number. Plain pages and unnumbered frames are excluded from progress and numbering, and overlays share one dot. Compile twice after adding or reordering slides to refresh progress.
- The monochrome HKU crest from the supplied 2a branding artwork appears as a large, low-contrast watermark on title, section, and closing pages.
- Cover and closing pages use a DASE purple field to the right of the orange divider, with light typography for contrast.
- Title, section, and closing pages share a left-pointing chevron with an orange edge and its apex 72% down the slide. Section pages stay light; title and closing pages use purple.

If you need a different department name or a dark title, edit the metadata in `template.tex` and the colour definitions near the top of `beamerthemeDASE.sty`.

To see the source relationship:

```bash
git remote -v
git log --oneline --decorate -5
```

The initial commit is inherited from the upstream HKU template; the DASE changes are recorded in the local fork commit on top of it.

Theme-owned titles, subtitles, chapter names, author/date fields, and footer metadata are bounded automatically. Slide headings and footer fields use one line. Presentation cover titles/subtitles and thank-you titles/closing text use up to four lines. Chapter titles use up to eight lines; only text beyond the eighth line receives an ellipsis. Chapter numbers stay centred beside the complete visible title. Overflow ends with an ellipsis at the original font size. The public-domain `truncate.sty` package is bundled so no additional installation is needed. This rule covers the theme placeholders; slide body content remains authored normally.

Generated LaTeX files (`.aux`, `.log`, `.nav`, `.snm`, `.toc`, bibliography intermediates, and similar output) are ignored by `.gitignore`; only source files, required assets, and the compiled guide PDF belong in the repository.
