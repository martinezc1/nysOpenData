# List datasets available in nysOpenData

Retrieves the current Open NY catalog and returns datasets available for
use with \`nys_pull_dataset()\`.

## Usage

``` r
nys_list_datasets()
```

## Value

A tibble of available datasets, including generated \`key\`, dataset
\`uid\`, and dataset \`title\`.

## Details

Keys are generated from dataset titles using
\`janitor::make_clean_names()\`.

## Examples

``` r
if (interactive() && curl::has_internet()) {
  nys_list_datasets()
}
```
