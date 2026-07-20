# List available New York State Open Data datasets

Retrieves a live catalog of New York State Open Data datasets from the
New York State Open Data Portal catalog table (\`ca8h-8gjq\`) and
returns dataset metadata that can be used with \[nys_pull_dataset()\].

## Usage

``` r
nys_list_datasets()
```

## Value

A tibble containing available New York State Open Data datasets.
Important columns include:

- key:

  A human-readable dataset key generated from the dataset name.

- uid:

  The official Socrata dataset identifier used by New York State Open
  Data.

- name:

  The dataset name from the New York State Open Data catalog.

Additional metadata columns from the New York State Open Data catalog
may also be returned.

## Details

The returned tibble includes both the official Socrata dataset \`uid\`
and a human-readable \`key\`. The \`uid\` is the stable identifier used
by the New York State Open Data Portal and Socrata API, while the
\`key\` is generated from the dataset name using
\[janitor::make_clean_names()\] to make datasets easier to reference in
R code, especially in classroom and reproducible research settings.

Most users will begin by calling \`nys_list_datasets()\`, searching the
returned catalog for a dataset of interest, and then passing either the
\`key\` or \`uid\` to \[nys_pull_dataset()\].

## Examples

``` r
if (interactive() && curl::has_internet()) {
  catalog <- nys_list_datasets()

  # View available datasets
  catalog

  # Search for datasets containing a keyword
  catalog[
    grepl("KEYWORD", catalog$name, ignore.case = TRUE),
    c("key", "uid", "name")
  ]
}
```
