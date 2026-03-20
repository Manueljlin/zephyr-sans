# Stroke width

following lucas de groot interpolation theory formula.

geom. ratio per step ×1.2577

| Weight     | Units | Rounded2Rect Ratio | CSS |
|------------|-------|--------------------|-----|
| Thin       | 40    | ~1.8x              | 100 |
| ExtraLight | 50    |                    | 200 |
| Light      | 63    |                    | 300 |
| Regular    | 80    | ~1.45x             | 400 |
| Medium     | 100   |                    | 500 |
| SemiBold   | 126   |                    | 600 |
| Bold       | 158   |                    | 700 |
| ExtraBold  | 200   |                    | 800 |
| Black      | 250   |                    | 900 |


--------------------------------------------------------------------------------


# Sidebearings (weight 100, see multipliers section)

## UPPERCASE

todo


## lowercase

| # | Description                           | Value |
|---|---------------------------------------|-------|
| 1 | = left  sidebearing of n              | 70    |
| 2 | = right sidebearing of n              | 65    |
| 3 | slightly + than left sidebearing of n | 75    |
| 4 | minimum sidebearings                  | 35    |
| 5 | = sidebearings of o                   | 50    |
| 6 | slightly - than sidebearings of o     | 45    |


special cases:
- i
    - on left  -- 57 instead of 75
    - on right -- 52 instead of 70
    - dot is larger and overshooting, so had to measure 75, 70 from the stem

- j 
    - on left  -- -48 instead of 70 (bc of descender)
        - measured 70 from the left above descender (effectively left sb of n)
    - on right -- same as `i`

- r (on right) -- 0 instead of 35 (bc of larger overhang w angle)
    - measured 35 from middle of hook instead of top
    - pretty happy with it
    - `|r| rhinoceros wreck river`
    - `gordon run arabic`

- l (on right) -- -5 instead of 65 (bc of looped tail)
    - visually adjusted volume of space with `nnlnnooloonn |l|`
    - could be improved?

- g
    - on left  -- 60
    - on right -- 35 (minimum sidebearings)
    - visually adjusted with `ogo |g| bga xgz`

- a
    - on left  -- 65 (looked fine)
    - on right -- 70 (left sb of n)
    - `|a| canarias arbusto vaqueros rabia`
    - `nnann a a oooaooo`

- s
    - on left  -- 50 (looked fine)
    - on right -- 45 (looked fine)
    - `|s| nnsnn ooosooo essex silvia`

- z
    - on left  -- 35 (minimum sb)
    - on right -- 35 (ditto)
    - `|o| |z| zephyr zx jazzy zumo`
    - `nnznn ooozooo`

- f
    - on left  -- 35
    - on right -- 40 (looked fine, tried to match gap of fl with gap of lo)
    - `|o| |f| |l| |i| effigy flow flamingo fruitful`
    - `nnfnn ooofooo dogfood affine`

- t
    - on left  -- 50 (from `f`)
    - on right -- 20
        - measured 25 from middle of hook instead of bottom
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
