# Kerning

## Left

| Group            | Reference | Characters               |
|------------------|-----------|--------------------------|
| opening          | (         | {, (                     |
| closing          | )         | }, )                     |
| punctuation      | .         | comma, period            |
| rounded          | o         | b, o, p                  |
| arches           | n         | h, m, n                  |
| verticals        | i         | d, i, j, q, u[^1]        |
| diagonals        | x         | k, x                     |
| diagonals (desc) | v         | v, w, y                  |

## Right

| Group            | Reference | Characters                       |
|------------------|-----------|----------------------------------|
| opening          | (         | {, (                             |
| closing          | )         | }, )                             |
| punctuation      | .         | comma, period                    |
| rounded          | o         | c, ç, d, e, o, q                 |
| verticals        | i         | b, h, i, j, k, l[^2], m, n, p, r |
| diagonals        | x         | x                                |
| diagonals (desc) | v         | v, w, y                          |

[^1] afaict usually doesn't inherit from `i`, so this is non standard
[^2] `l` has looped tail on this font so its r kerning is not shared with i

special cases in regular (kerning.plist is canonical, this may be outdated):

glyph to glyph:
- `Aa`, `aa`, `ag`
- `ca`, `ct`
- `ea`, `ef`, `es`, `et`
- `fa`, `f]`, `ff`, `f'`, `ft`, `fu`
- `ga`, `gu`
- `la`, `lt`
- `'s`, `'t`
- `ra`, `rg`, `r-`
- `sa`, `st`
- `ta`, `tf`, `ts`, `tt`
- `ug`

glyph to group:
- `a` + diagonals (desc)
- `[` + verticals
- `c` + verticals
- `e` + punctuation, diagonals (desc), diagonals
- `f` + closing, punctuation, verticals, rounded
- `g` + punctuation, rounded
- `l` + closing, punctuation, verticals, rounded, diagonals (desc)
- `'` + rounded
- `r` + punctuation, rounded, diagonals (desc)
- `s` + punctuation, verticals
- `t` + rounded, diagonals (desc)
- `z` + rounded

group-to-glyph:
- verticals + `a`, `]`, `g`, `s`
- arches + `a`, `f`, `g`, `t` (`n` + `f` coverd here so dnf looks right)
- rounded + `a`, `f`, `g`, `s`, `t`
- diagonals (desc) + `a`, `g`, `s`
- diagonals + `a`, `f`, `g`, `s`, `t`


--------------------------------------------------------------------------------


# Stroke width

read https://manueljlin.com/post/fontra-101/en#interpolation-curves for more info

| Weight     | Units | CSS | ()2[]  |
|------------|-------|-----|--------|
| Hairline   | 54    | 50  |        |
| Thin       | 71    | 100 | ~1.8x  |
| ExtraLight | 98    | 200 |        |
| Light      | 127   | 300 |        |
| Regular    | 160   | 400 | ~1.45x |
| Medium     | 198   | 500 |        |
| SemiBold   | 241   | 600 |        |
| Bold       | 291   | 700 |        |
| ExtraBold  | 348   | 800 |        |
| Black      | 414   | 900 |        |


--------------------------------------------------------------------------------


# Sidebearings (weight 100, see multipliers section)

## UPPERCASE

todo


## lowercase

| # | Description                           | Value |
|---|---------------------------------------|-------|
| 1 | = left  sidebearing of n              | 150   |
| 2 | = right sidebearing of n              | 140   |
| 3 | slightly + than left sidebearing of n | 160   |
| 4 | minimum sidebearings                  | 80    |
| 5 | = sidebearings of o                   | 110   |
| 6 | slightly - than sidebearings of o     | 100   |


special cases:
- i
    - on left  -- 124 instead of 160
    - on right -- 114 instead of 150
    - dot is larger and overshooting, so had to measure 160, 150 from the stem

- j 
    - on left  -- -86 instead of 150 (bc of descender)
        - measured 150 from the left above descender (effectively left sb of n)
    - on right -- same as `i`

- r (on right) -- 10 instead of 80 (bc of larger overhang w angle)
    - measured 80 from middle of hook instead of top
    - pretty happy with it
    - `|r| rhinoceros wreck river`
    - `gordon run arabic`

- l (on right) -- 0 instead of 140 (bc of looped tail)
    - visually adjusted volume of space with `nnlnnooloonn |l|`
    - could be improved?

- g
    - on left  -- 130
    - on right -- 80 (minimum sidebearings)
    - visually adjusted with `ogo |g| bga xgz`

- a
    - on left  -- 140 (looked fine)
    - on right -- 150 (left sb of n)
    - `|a| canarias arbusto vaqueros rabia`
    - `nnann a a oooaooo`

- s
    - on left  -- 110 (looked fine)
    - on right -- 100 (looked fine)
    - `|s| nnsnn ooosooo essex silvia`

- z
    - on left  -- 80 (minimum sb)
    - on right -- 80 (ditto)
    - `|o| |z| zephyr zx jazzy zumo`
    - `nnznn ooozooo`

- f
    - on left  -- 80
    - on right -- 90 (looked fine, tried to match gap of fl with gap of lo)
    - `|o| |f| |l| |i| effigy flow flamingo fruitful`
    - `nnfnn ooofooo dogfood affine`

- t
    - on left  -- 110 (from `f`)
    - on right -- 50
        - measured 60 from middle of hook instead of bottom
    - `|t| |f| tlo stick pt tuna ootoo htc nntnn deutsche`


see "testing spacing" from designing type by karen cheng
in the eu/uk release (red cover), 2nd edition is page 55

alternatively, "letters of credit: a view of type design" by walter tracy,
(or search "tracy method") which is what karen cheng references on the same page


### sidebearing multipliers
- 100 -> 1x
- 400 -> 1.25x
- 900 -> todo


# Angles

- 5deg  `g f t j l c`
- 15deg `{ } ç`
- 30deg `( )`
