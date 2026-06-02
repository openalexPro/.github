# openalexPro

An R ecosystem for large-scale, on-disk access to [OpenAlex](https://openalex.org) — the open catalogue of global scholarly work.

OpenAlex provides free, comprehensive metadata on over 250 million scholarly works, authors, institutions, and concepts. The **openalexPro** ecosystem is built around a single design principle: process data on disk rather than in memory, so workflows scale to millions of records without hitting RAM limits.

---

## R Packages

### [openalexPro](https://github.com/openalexPro/openalexPro)

[![CI](https://github.com/openalexPro/openalexPro/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/openalexPro/openalexPro/actions/workflows/R-CMD-check.yaml)
[![r-universe](https://openalexpro.r-universe.dev/openalexPro/badges/version)](https://openalexpro.r-universe.dev/openalexPro)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.17453180.svg)](https://doi.org/10.5281/zenodo.17453180)
[![Lifecycle: maturing](https://img.shields.io/badge/lifecycle-maturing-blue.svg)](https://lifecycle.r-lib.org/articles/stages.html)
[![License: GPL-2+](https://img.shields.io/badge/License-GPL%20%3E%3D%202-blue.svg)](https://www.gnu.org/licenses/gpl-2.0)
[![Codecov](https://codecov.io/gh/openalexPro/openalexPro/graph/badge.svg)](https://app.codecov.io/gh/openalexPro/openalexPro)
[![Docs](https://img.shields.io/badge/docs-pkgdown-blue)](https://openalexpro.github.io/openalexPro/)

Core API client — query OpenAlex, page through results, and store everything in Parquet files for efficient downstream use. The on-disk processing approach scales to millions of records without RAM limits.

---

### [openalexSnowball](https://github.com/openalexPro/openalexSnowball)

[![CI](https://github.com/openalexPro/openalexSnowball/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/openalexPro/openalexSnowball/actions/workflows/R-CMD-check.yaml)
[![r-universe](https://openalexpro.r-universe.dev/openalexSnowball/badges/version)](https://openalexpro.r-universe.dev/openalexSnowball)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20448982.svg)](https://doi.org/10.5281/zenodo.20448982)
[![Lifecycle: maturing](https://img.shields.io/badge/lifecycle-maturing-blue.svg)](https://lifecycle.r-lib.org/articles/stages.html)
[![License: GPL-2+](https://img.shields.io/badge/License-GPL%20%3E%3D%202-blue.svg)](https://www.gnu.org/licenses/gpl-2.0)
[![Codecov](https://codecov.io/gh/openalexPro/openalexSnowball/graph/badge.svg)](https://app.codecov.io/gh/openalexPro/openalexSnowball)
[![Docs](https://img.shields.io/badge/docs-pkgdown-blue)](https://openalexpro.github.io/openalexSnowball/)

Snowball citation searches — iteratively expand a seed set by following forward and backward citations across the graph. Supports configurable depth and deduplication.

---

### [openalexConvert](https://github.com/openalexPro/openalexConvert)

[![CI](https://github.com/openalexPro/openalexConvert/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/openalexPro/openalexConvert/actions/workflows/R-CMD-check.yaml)
[![r-universe](https://openalexpro.r-universe.dev/openalexConvert/badges/version)](https://openalexpro.r-universe.dev/openalexConvert)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20448988.svg)](https://doi.org/10.5281/zenodo.20448988)
[![Lifecycle: experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://lifecycle.r-lib.org/articles/stages.html)
[![License: GPL-2+](https://img.shields.io/badge/License-GPL%20%3E%3D%202-blue.svg)](https://www.gnu.org/licenses/gpl-2.0)
[![Codecov](https://codecov.io/gh/openalexPro/openalexConvert/graph/badge.svg)](https://app.codecov.io/gh/openalexPro/openalexConvert)
[![Docs](https://img.shields.io/badge/docs-pkgdown-blue)](https://openalexpro.github.io/openalexConvert/)

Export a Parquet corpus to BibTeX, BibLaTeX, CSL JSON, Markdown, LaTeX, HTML, or PDF via Pandoc. Bridges the openalexPro ecosystem with reference managers and publishing workflows.

---

### [openalexSnapshot](https://github.com/openalexPro/openalexSnapshot)

[![CI](https://github.com/openalexPro/openalexSnapshot/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/openalexPro/openalexSnapshot/actions/workflows/R-CMD-check.yaml)
[![r-universe](https://openalexpro.r-universe.dev/openalexSnapshot/badges/version)](https://openalexpro.r-universe.dev/openalexSnapshot)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20448992.svg)](https://doi.org/10.5281/zenodo.20448992)
[![Lifecycle: experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://lifecycle.r-lib.org/articles/stages.html)
[![License: GPL-2+](https://img.shields.io/badge/License-GPL%20%3E%3D%202-blue.svg)](https://www.gnu.org/licenses/gpl-2.0)
[![Codecov](https://codecov.io/gh/openalexPro/openalexSnapshot/graph/badge.svg)](https://app.codecov.io/gh/openalexPro/openalexSnapshot)
[![Docs](https://img.shields.io/badge/docs-pkgdown-blue)](https://openalexpro.github.io/openalexSnapshot/)

Bulk snapshot tools — convert the full OpenAlex JSON.GZ snapshot to Parquet, build ID-lookup indexes, and extract records by ID at scale. Powered by a compiled Rust back-end with a pure-R/DuckDB fallback.

---

### [openalexVectorComp](https://github.com/openalexPro/openalexVectorComp)

[![CI](https://github.com/openalexPro/openalexVectorComp/actions/workflows/pr-checks.yml/badge.svg)](https://github.com/openalexPro/openalexVectorComp/actions/workflows/pr-checks.yml)
[![r-universe](https://openalexpro.r-universe.dev/openalexVectorComp/badges/version)](https://openalexpro.r-universe.dev/openalexVectorComp)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.19607514.svg)](https://doi.org/10.5281/zenodo.19607514)
[![Lifecycle: experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://lifecycle.r-lib.org/articles/stages.html)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Codecov](https://codecov.io/gh/openalexPro/openalexVectorComp/graph/badge.svg)](https://app.codecov.io/gh/openalexPro/openalexVectorComp)
[![Docs](https://img.shields.io/badge/docs-pkgdown-blue)](https://openalexpro.github.io/openalexVectorComp/)

Text embedding, cosine-distance scoring, and threshold calibration — backend-neutral (HuggingFace, OpenAI, TEI). Adds semantic similarity search to the ecosystem.

---

## Rust Core

### [openalex-snapshot](https://github.com/openalexPro/openalex-snapshot)

[![CI](https://github.com/openalexPro/openalex-snapshot/actions/workflows/ci.yml/badge.svg)](https://github.com/openalexPro/openalex-snapshot/actions/workflows/ci.yml)
[![Release](https://img.shields.io/github/v/release/openalexPro/openalex-snapshot)](https://github.com/openalexPro/openalex-snapshot/releases/latest)
[![Docs](https://img.shields.io/badge/docs-mkdocs-blue)](https://openalexpro.github.io/openalex-snapshot/)

Compiled Rust CLI and library powering `openalexSnapshot`'s hot path (JSON→Parquet conversion, indexing, ID extraction). Downloaded automatically as a pre-built static library when installing `openalexSnapshot` — no manual Rust setup required for most users.

---

## Installation

All R packages are available from the openalexPro r-universe:

```r
install.packages(
  c("openalexPro", "openalexSnowball", "openalexConvert",
    "openalexSnapshot", "openalexVectorComp"),
  repos = c("https://openalexpro.r-universe.dev", "https://cloud.r-project.org")
)
```

## Design principles

- **On-disk processing** — results are paged and written to Parquet; memory use stays flat regardless of corpus size.
- **Arrow / DuckDB throughout** — all data manipulation uses columnar formats; SQL queries run in-process.
- **Composable** — each package has a single responsibility and speaks the same Parquet dialect, so they chain naturally.
- **Rust where it matters** — the bulk snapshot converter delegates hot-path work to a compiled Rust back-end, with a pure-R/DuckDB fallback.

## Contributing

Issues and pull requests are welcome on the individual package repositories. Please open an issue before starting large changes.

## Acknowledgements

This ecosystem builds on the excellent [openalexR](https://github.com/ropensci/openalexR) package and the [OpenAlex](https://openalex.org) team's commitment to open scholarly infrastructure.

## Disclaimer

The packages are provided **as is**. The authors are not affiliated with OpenAlex.
