# openalexPro

An R ecosystem for large-scale, on-disk access to [OpenAlex](https://openalex.org) — the open catalogue of global scholarly work.

OpenAlex provides free, comprehensive metadata on over 250 million scholarly works, authors, institutions, and concepts. The **openalexPro** ecosystem is built around a single design principle: process data on disk rather than in memory, so workflows scale to millions of records without hitting RAM limits.

## Packages

| Package | Description | CI | Docs | Install |
|---------|-------------|-----|------|---------|
| [**openalexPro**](https://github.com/openalexPro/openalexPro) | Core API client — query OpenAlex, page through results, and store everything in Parquet files for efficient downstream use | [![CI](https://github.com/openalexPro/openalexPro/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/openalexPro/openalexPro/actions/workflows/R-CMD-check.yaml) | [📖](https://openalexpro.github.io/openalexPro/) | [![r-universe](https://openalexpro.r-universe.dev/openalexPro/badges/version)](https://openalexpro.r-universe.dev/openalexPro) [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.17453180.svg)](https://doi.org/10.5281/zenodo.17453180) |
| [**openalexSnowball**](https://github.com/openalexPro/openalexSnowball) | Snowball citation searches — iteratively expand a seed set by following forward and backward citations across the graph | [![CI](https://github.com/openalexPro/openalexSnowball/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/openalexPro/openalexSnowball/actions/workflows/R-CMD-check.yaml) | [📖](https://openalexpro.github.io/openalexSnowball/) | [![r-universe](https://openalexpro.r-universe.dev/openalexSnowball/badges/version)](https://openalexpro.r-universe.dev/openalexSnowball) [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20448982.svg)](https://doi.org/10.5281/zenodo.20448982) |
| [**openalexConvert**](https://github.com/openalexPro/openalexConvert) | Export a Parquet corpus to BibTeX, BibLaTeX, CSL JSON, Markdown, LaTeX, HTML, or PDF via Pandoc | [![CI](https://github.com/openalexPro/openalexConvert/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/openalexPro/openalexConvert/actions/workflows/R-CMD-check.yaml) | [📖](https://openalexpro.github.io/openalexConvert/) | [![r-universe](https://openalexpro.r-universe.dev/openalexConvert/badges/version)](https://openalexpro.r-universe.dev/openalexConvert) [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20448988.svg)](https://doi.org/10.5281/zenodo.20448988) |
| [**openalexSnapshot**](https://github.com/openalexPro/openalexSnapshot) | Bulk snapshot tools — convert the full OpenAlex JSON.GZ snapshot to Parquet, build ID-lookup indexes, and extract records at scale using a Rust back-end | [![CI](https://github.com/openalexPro/openalexSnapshot/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/openalexPro/openalexSnapshot/actions/workflows/R-CMD-check.yaml) | [📖](https://openalexpro.github.io/openalexSnapshot/) | [![r-universe](https://openalexpro.r-universe.dev/openalexSnapshot/badges/version)](https://openalexpro.r-universe.dev/openalexSnapshot) [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20448992.svg)](https://doi.org/10.5281/zenodo.20448992) |
| [**openalexVectorComp**](https://github.com/openalexPro/openalexVectorComp) | Text embedding, cosine-distance scoring, and threshold calibration — backend-neutral (HuggingFace, OpenAI, TEI) | [![CI](https://github.com/openalexPro/openalexVectorComp/actions/workflows/pr-checks.yml/badge.svg)](https://github.com/openalexPro/openalexVectorComp/actions/workflows/pr-checks.yml) | [📖](https://openalexpro.github.io/openalexVectorComp/) | [![r-universe](https://openalexpro.r-universe.dev/openalexVectorComp/badges/version)](https://openalexpro.r-universe.dev/openalexVectorComp) [![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.19607514.svg)](https://doi.org/10.5281/zenodo.19607514) |

## Rust core

| Package | Description | CI | Docs | Release |
|---------|-------------|-----|------|---------|
| [**openalex-snapshot**](https://github.com/openalexPro/openalex-snapshot) | Compiled Rust CLI and library powering `openalexSnapshot`'s hot path (JSON→Parquet conversion, indexing, ID extraction). Downloaded automatically as a pre-built static library on install — no manual Rust setup required for most users. | [![CI](https://github.com/openalexPro/openalex-snapshot/actions/workflows/ci.yml/badge.svg)](https://github.com/openalexPro/openalex-snapshot/actions/workflows/ci.yml) | [📖](https://openalexpro.github.io/openalex-snapshot/) | [![GitHub release](https://img.shields.io/github/v/release/openalexPro/openalex-snapshot)](https://github.com/openalexPro/openalex-snapshot/releases/latest) |

## Installation

All R packages are available from the openalexPro r-universe:

```r
install.packages(
  c("openalexPro", "openalexSnowball", "openalexConvert",
    "openalexSnapshot", "openalexVectorComp"),
  repos = c("https://openalexpro.r-universe.dev", "https://cloud.r-project.org")
)
```

## Typical workflow

```r
library(openalexPro)

# 1. Query OpenAlex and store results as Parquet
fetch_works(
  query = '"biodiversity" AND "ecosystem services"',
  output = "my_corpus"
)

# 2. Or work directly with the bulk OpenAlex snapshot
library(openalexSnapshot)
oa_snapshot_to_parquet(
  snapshot_dir = "/data/openalex-snapshot",
  parquet_dir  = "/data/openalex-parquet"
)

# 3. Snowball-expand a seed set (optional)
library(openalexSnowball)
snowball(corpus = "my_corpus", depth = 1, output = "my_corpus_expanded")

# 4. Export to BibTeX, CSL JSON, etc.
library(openalexConvert)
corpus_to_csljson("my_corpus", output = "csl/")
csljson_convert_pandoc("csl/", "refs/", to = "bibtex")
```

## Design principles

- **On-disk processing** — results are paged and written to Parquet; memory use stays flat regardless of corpus size.
- **Arrow / DuckDB throughout** — all data manipulation uses columnar formats; SQL queries run in-process.
- **Composable** — each package has a single responsibility and speaks the same Parquet dialect, so they chain naturally.
- **Rust where it matters** — the bulk snapshot converter delegates hot-path work to a compiled Rust back-end ([openalex-snapshot](https://github.com/openalexPro/openalex-snapshot)), with a pure-R/DuckDB fallback for environments without a Rust toolchain.

## Contributing

Issues and pull requests are welcome on the individual package repositories. Please open an issue before starting large changes.

## Acknowledgements

This ecosystem builds on the excellent [openalexR](https://github.com/ropensci/openalexR) package and the [OpenAlex](https://openalex.org) team's commitment to open scholarly infrastructure.

## Disclaimer

The packages are provided **as is**. The authors are not affiliated with OpenAlex.
