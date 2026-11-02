# Averia Libre

No source of this family was ever published: the fonts Google Fonts ships
were its only form. The sources in `sources/` were converted from those
fonts with [babelfont-rs](https://github.com/felipesanches/babelfont-rs/tree/2026-11-02), and
build with [gftools-builder](https://github.com/simoncozens/gftools-rust)
and fontc.

The fonts they were converted from remain in the git history.

How these sources were checked against the released fonts (the tools, this family's plan and the logs): https://github.com/felipesanches/gf-source-modernization.

## Known differences from the released fonts

These sources rebuild the fonts Google Fonts ships, except for the following, which were reviewed and deliberately left as they are:

- The released fonts kern with a legacy `kern` table; these sources kern through a GPOS kern feature, which is how fontc builds kerning. HarfBuzz shapes every kerned pair alike in both, except pairs with the soft hyphen (U+00AD), which it hides: there the release leaves half the pair's value on the following glyph and the build none (42 to 102 pairs per style, tools/probes/binary_to_source/results/legacy-kern-pairs.txt in the evidence repository). Decided 2026-10-01: releases with an old kern table are accepted and disclosed.
