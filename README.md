# soapcheckr

[![soapcheckr status
badge](https://benjaminhlina.r-universe.dev/badges/soapcheckr)](https://benjaminhlina.r-universe.dev/soapcheckr)

## Check whether a soap film smoother boundary and knots make sense

Setting up a soap film smoother is often a hard and frustrating process.
This packages provides functions that checks the boundary, knots, and
data that you feed to a soap are “correct”. The functions in the package
will also plot the area that will be modeled by the soap film smoother
in red, and knots and/or data as circles as viable locations. Any
circles that have a X through them are considered inadequate and will
need to be removed.

To do the spatial analysis, we require a couple of extra libraries:
[{sf}](https://r-spatial.github.io/sf/) and
[{mgcv}](https://cran.r-project.org/web/packages/mgcv/index.html). That
will be loaded when installing
[{soapcheckr}](https://github.com/dill/soap_checker).

`{soapcheckr}` can be installed using the following code;

``` r
install.packages("devtools")
devtools::install_github("dill/soapcheckr")
```

Next load `{soapcheckr}` and walk through the vignette to see how to use
the functions. We highly encourage walking through both examples in the
vignette.

``` r
library(soapcheckr)
vignette("how_to_use_soapcheckr")
```

## Other tips

- Note that you need to set the `k` and `nmax` argument in
  `autocruncher()` to be the same as your planned value in `gam()` for
  your soap film smoother
- The functions assumes that your spatial variable names are `x` and `y`
  unless you supply the naming arguments with the column names from your
  data.
- Make sure that your locations are in Northings/Eastings, (e.g., UTMs).
  Using latitude and longitude (e.g., decimal degree) will give strange
  results (as the soap film smoother is isotropic so treats 1 unit
  change in either dimension is equal, this isn’t true for lat/long!).
- Sometimes you need to increase the tolerance (e.g `tol = 1e-6`)
  argument when using `soap_check()`
- Note that the boundary must be a `list` of `list`s or `data.frame`s.
  So if you have a polygon boundary with your boundary vertices in it,
  that must be wrapped in a `list`! The vector names of each boundary
  need to be names `x` and `y` for the functions to work.
- You can also access the vignette at the following [blog
  post](https://blog.benjaminhlina.com/posts/post-with-code/soapcheckr/)

Written by David L. Miller and Benjamin L. Hlina. Released under the GPL
(version 2).
