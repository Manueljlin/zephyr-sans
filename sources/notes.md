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

two-segment interpolation: linear (100–400) + de groot (400–900)

| Weight     | Units | CSS | ()2[]  |
|------------|-------|-----|--------|
| Thin       | 27    | 100 | ~1.8x  |
| ExtraLight | 45    | 200 |        |
| Light      | 62    | 300 |        |
| Regular    | 80    | 400 | ~1.45x |
| Medium     | 97    | 500 |        |
| SemiBold   | 117   | 600 |        |
| Bold       | 141   | 700 |        |
| ExtraBold  | 171   | 800 |        |
| Black      | 207   | 900 |        |


--------------------------------------------------------------------------------


# Sidebearings (weight 100, see multipliers section)

## UPPERCASE

todo


## lowercase

| # | Description                           | Value |
|---|---------------------------------------|-------|
| 1 | = left  sidebearing of n              | 75    |
| 2 | = right sidebearing of n              | 70    |
| 3 | slightly + than left sidebearing of n | 80    |
| 4 | minimum sidebearings                  | 40    |
| 5 | = sidebearings of o                   | 55    |
| 6 | slightly - than sidebearings of o     | 50    |


special cases:
- i
    - on left  -- 62 instead of 80
    - on right -- 57 instead of 75
    - dot is larger and overshooting, so had to measure 80, 75 from the stem

- j 
    - on left  -- -43 instead of 75 (bc of descender)
        - measured 75 from the left above descender (effectively left sb of n)
    - on right -- same as `i`

- r (on right) -- 5 instead of 40 (bc of larger overhang w angle)
    - measured 40 from middle of hook instead of top
    - pretty happy with it
    - `|r| rhinoceros wreck river`
    - `gordon run arabic`

- l (on right) -- 0 instead of 70 (bc of looped tail)
    - visually adjusted volume of space with `nnlnnooloonn |l|`
    - could be improved?

- g
    - on left  -- 65
    - on right -- 40 (minimum sidebearings)
    - visually adjusted with `ogo |g| bga xgz`

- a
    - on left  -- 70 (looked fine)
    - on right -- 75 (left sb of n)
    - `|a| canarias arbusto vaqueros rabia`
    - `nnann a a oooaooo`

- s
    - on left  -- 55 (looked fine)
    - on right -- 50 (looked fine)
    - `|s| nnsnn ooosooo essex silvia`

- z
    - on left  -- 40 (minimum sb)
    - on right -- 40 (ditto)
    - `|o| |z| zephyr zx jazzy zumo`
    - `nnznn ooozooo`

- f
    - on left  -- 40
    - on right -- 45 (looked fine, tried to match gap of fl with gap of lo)
    - `|o| |f| |l| |i| effigy flow flamingo fruitful`
    - `nnfnn ooofooo dogfood affine`

- t
    - on left  -- 55 (from `f`)
    - on right -- 25
        - measured 30 from middle of hook instead of bottom
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
