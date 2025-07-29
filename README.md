# [aisicresearch.github.io](https://aisicresearch.github.io)

This is the AISIC project website.

The English version is at the top level. To make changes, simply edit the `.qmd` files — updates are deployed automatically when you commit.

The German version is located in the `/de` subdirectory. Please ensure that **both** versions are updated when making changes.


### Technical Note

Quarto does not natively support multilingual websites ([see discussion](https://github.com/quarto-dev/quarto-cli/issues/275)). To work around this, the site uses Quarto 'profiles'.

1. The top-level site is rendered using `quarto render --profile english`, which loads settings from `_quarto-english.yml`.
2. Then the German version is rendered with `quarto render --profile german`, which outputs to `_site/de`.

However, due to how Quarto includes all `.qmd` files regardless of profile, the German output in `_site/de` contains both the english version and the german only one in the subdirectory: `_site/de/de/`.

To fix this, the [deployment process](.github/workflows/publish.yml) copies files from `_site/de/de/` to `_site/de/`. The `_quarto-german.yml` is set up to work with the adjusted paths.
