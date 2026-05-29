# openalexPro

An R ecosystem for large-scale, on-disk access to [OpenAlex](https://openalex.org) — the open catalogue of global scholarly work.

OpenAlex provides free, comprehensive metadata on over 250 million scholarly works, authors, institutions, and concepts. The **openalexPro** ecosystem is built around a single design principle: process data on disk rather than in memory, so workflows scale to millions of records without hitting RAM limits.

## Packages

| Package | Description | Install |
|---------|-------------|---------|
| [**openalexPro**](https://github.com/openalexPro/openalexPro) | Core API client — query OpenAlex, page through results, and store everything in Parquet files for efficient downstream use | [![r-universe](https://openalexpro.r-universe.dev/openalexPro/badges/version)](https://openalexpro.r-universe.dev/openalexPro) |
| [**openalexSnowball**](https://github.com/openalexPro/openalexSnowball) | Snowball citation searches — iteratively expand a seed set by following forward and backward citations across the graph | [![r-universe](https://openalexpro.r-universe.dev/openalexSnowball/badges/version)](https://openalexpro.r-universe.dev/openalexSnowball) |
| [**openalexConvert**](https://github.com/openalexPro/openalexConvert) | Export a Parquet corpus to BibTeX, BibLaTeX, CSL JSON, Markdown, LaTeX, HTML, or PDF via Pandoc | [![r-universe](https://openalexpro.r-universe.dev/openalexConvert/badges/version)](https://openalexpro.r-universe.dev/openalexConvert) |
| [**openalexSnapshot**](https://github.com/openalexPro/openalexSnapshot) | Bulk snapshot tools — convert the full OpenAlex JSON.GZ snapshot to Parquet, build ID-lookup indexes, and extract records at scale using a Rust back-end | [![r-universe](https://openalexpro.r-universe.dev/openalexSnapshot/badges/version)](https://openalexpro.r-universe.dev/openalexSnapshot) |
| [**openalexVectorComp**](https://github.com/openalexPro/openalexVectorComp) | Text embedding, cosine-distance scoring, and threshold calibration — backend-neutral (HuggingFace, OpenAI, TEI) | [![r-universe](https://openalexpro.r-universe.dev/openalexVectorComp/badges/version)](https://openalexpro.r-universe.dev/openalexVectorComp) |

## Rust core

[**openalex-snapshot**](https://github.com/openalexPro/openalex-snapshot) is the compiled Rust CLI and library that powers `openalexSnapshot`'s hot path (JSON→Parquet conversion, indexing, ID extraction). It is automatically compiled or downloaded as a pre-built static library when you install `openalexSnapshot` — no manual Rust setup required for most users.

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
