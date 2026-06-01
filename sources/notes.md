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

```ts
const Zephyr: StrokeCurveConfig = {
  minWeight: 50,
  maxWeight: 900,
  minStroke: 54,
  maxStroke: 463,
  curvature: 1 / Math.sqrt(2)
}

strokeFromWeight(50,  Zephyr) // 54
strokeFromWeight(100, Zephyr) // rounded to 72
strokeFromWeight(200, Zephyr) // rounded to 101
strokeFromWeight(300, Zephyr) // rounded to 133
strokeFromWeight(400, Zephyr) // rounded to 170
strokeFromWeight(500, Zephyr) // rounded to 213
strokeFromWeight(600, Zephyr) // rounded to 262
strokeFromWeight(700, Zephyr) // rounded to 319
strokeFromWeight(800, Zephyr) // rounded to 386
strokeFromWeight(900, Zephyr) // 463
```

| Weight     | Units | CSS |
|------------|-------|-----|
| Hairline   | 54    | 50  |
| Thin       | 72    | 100 |
| ExtraLight | 101   | 200 |
| Light      | 133   | 300 |
| Regular    | 170   | 400 |
| Medium     | 213   | 500 |
| SemiBold   | 262   | 600 |
| Bold       | 319   | 700 |
| ExtraBold  | 386   | 800 |
| Black      | 463   | 900 |

read https://manueljlin.com/post/fontra-101/en#interpolation-curves for more info.
keep in mind it's somewhat outdated.


--------------------------------------------------------------------------------


# Sidebearings (weight 100, see multipliers section)

## UPPERCASE

Derived from `O` and `H`.

`H` width is (1/1.1) * `O` width 1300 = ~1180
`H` side bearings is 20% of its inner width 820 = 164

### ratios


### results

##  uppercase
(hairline -> stem width (180))
| # | Description                      | Value |
|---|----------------------------------|-------|
| 1 | = sidebearing of H               | 193   |
| 2 | slightly - than sidebearing of H | 135   | <!-- 0.7x H sidebearing -->
| 3 | half of sidebearing of H         | 96    |
| 4 | minimum sidebearings             | 40    | <!-- may need some more tweaking -->
| 5 | = sidebearing of O               | 120   |


> FIXME: recalculate based on hairline
(regular -> stem width (180))
| # | Description                      | Value |
|---|----------------------------------|-------|
| 1 | = sidebearing of H               | 164   |
| 2 | slightly - than sidebearing of H | 116   |
| 3 | half of sidebearing of H         | 58    |
| 4 | minimum sidebearings             |       |
| 5 | = sidebearing of O               |       |


## lowercase

### ratios
| # | Description                           | Value |
|---|---------------------------------------|-------|
| 1 | = left  sidebearing of n              | 1.0   |
| 2 | = right sidebearing of n              | 0.921 |
| 3 | slightly + than left sidebearing of n | 1.079 |
| 4 | minimum sidebearings                  | 0.211 |
| 5 | = sidebearing of o                    | 0.789 |
| 6 | slightly - than sidebearing of o      | 0.711 |

### results
(hairline -> stem width (54) * 3.0 is left sidebearing of n)
| # | Description                           | Value |
|---|---------------------------------------|-------|
| 1 | = left  sidebearing of n              | 162   |
| 2 | = right sidebearing of n              | 149   |
| 3 | slightly + than left sidebearing of n | 175   |
| 4 | minimum sidebearings                  | 34    |
| 5 | = sidebearing of o                    | 128   |
| 6 | slightly - than sidebearing of o      | 115   |

> FIXME: stem width is actually 170 rn!!
(regular -> stem width (180) * 0.8 is left sidebearing of n)
| # | Description                           | Value |
|---|---------------------------------------|-------|
| 1 | = left  sidebearing of n              | 144   |
| 2 | = right sidebearing of n              | 133   |
| 3 | slightly + than left sidebearing of n | 155   |
| 4 | minimum sidebearings                  | 30    |
| 5 | = sidebearing of o                    | 114   |
| 6 | slightly - than sidebearing of o      | 102   |

(black -> stem width (463) * 0.1 is left sidebearing of n)
| # | Description                           | Value |
|---|---------------------------------------|-------|
| 1 | = left  sidebearing of n              | 46    |
| 2 | = right sidebearing of n              | 42    |
| 3 | slightly + than left sidebearing of n | 50    |
| 4 | minimum sidebearings                  | 10    |
| 5 | = sidebearing of o                    | 36    |
| 6 | slightly - than sidebearing of o      | 33    |


special cases (note that it's based on hairline):
- r (on right)
    - `|r| rhinoceros wreck river`
    - `gordon run arabic`

- l (on right) -- 17
    - visually adjusted volume of space with `nnlnnooloonn |l|`
    - could be improved?

- g
    - on left  -- 94
    - on right -- 60
    - visually adjusted with `ogo |g| bga xgz`

- a
    - on left  -- 115
    - on right -- 140
    - `|a| canarias arbusto vaqueros rabia`
    - `nnann a a oooaooo`

- s
    - on left  -- 95
    - on right -- 85
    - `|s| nnsnn ooosooo essex silvia`

- z
    - on left  -- 85
    - on right -- 77
    - `|o| |z| zephyr zx jazzy zumo`
    - `nnznn ooozooo`

- f
    - on left  -- 77
    - on right -- 0
    - `|o| |f| |l| |i| effigy flow flamingo fruitful`
    - `nnfnn ooofooo dogfood affine`

- t
    - on left  -- 50
    - on right -- 60
    - `|t| |f| tlo stick pt tuna ootoo htc nntnn deutsche`


see "testing spacing" from designing type by karen cheng
in the eu/uk release (red cover), 2nd edition is page 55

alternatively, "letters of credit: a view of type design" by walter tracy,
(or search "tracy method") which is what karen cheng references on the same page


# Angles
- 5deg  `g f t j l c`
- 15deg `{ } ç`
- 30deg `( )`


# Contrast
- 100 -> 10%
- 400 -> 10%
- 900 -> 20%


# Horizontal scaling of glyph relative to hairline
- 100 -> 1x
- 400 -> todo
- 900 -> estimate is ~1.3x