# Load Any NYS Open Data Dataset

Downloads any NYS Open Data dataset given its Socrata JSON endpoint.

## Usage

``` r
nys_any_dataset(
  json_link,
  limit = 10000,
  timeout_sec = 30,
  clean_names = TRUE,
  coerce_types = TRUE
)
```

## Arguments

- json_link:

  A Socrata dataset JSON endpoint URL (e.g.,
  "https://data.ny.gov/resource/28gk-bu58.json").

- limit:

  Number of rows to retrieve (default = 10,000).

- timeout_sec:

  Request timeout in seconds (default = 30).

- clean_names:

  Logical; if TRUE, convert column names to snake_case (default = TRUE).

- coerce_types:

  Logical; if TRUE, attempt light type coercion (default = TRUE).

## Value

A tibble containing the requested dataset.

## Examples

``` r
# Examples that hit the live nys Open Data API are guarded so CRAN checks
# do not fail when the network is unavailable or slow.
if (interactive() && curl::has_internet()) {
  endpoint <- "https://data.ny.gov/resource/28gk-bu58.json"
  out <- try(nys_any_dataset(endpoint, limit = 3), silent = TRUE)
  if (!inherits(out, "try-error")) {
    head(out)
  }
}
```
