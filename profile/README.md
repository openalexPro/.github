# openalexPro

An R ecosystem for large-scale, on-disk access to [OpenAlex](https://openalex.org) — the open catalogue of global scholarly work.

OpenAlex provides free, comprehensive metadata on over 250 million scholarly works, authors, institutions, and concepts. The **openalexPro** ecosystem is built around a single design principle: process data on disk rather than in memory, so workflows scale to millions of records without hitting RAM limits.

The `main` and `dev` badges show the version in each branch's `DESCRIPTION`, read live from GitHub.

---

## R Packages

### [openalexPro](https://github.com/openalexPro/openalexPro)

[![r-universe](https://openalexpro.r-universe.dev/openalexPro/badges/version)](https://openalexpro.r-universe.dev/openalexPro)
[![main](https://img.shields.io/github/r-package/v/openalexPro/openalexPro/main?label=main)](https://github.com/openalexPro/openalexPro/tree/main)
[![dev](https://img.shields.io/github/r-package/v/openalexPro/openalexPro/dev?label=dev)](https://github.com/openalexPro/openalexPro/tree/dev)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.17453180.svg)](https://doi.org/10.5281/zenodo.17453180)
[![CI](https://github.com/openalexPro/openalexPro/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/openalexPro/openalexPro/actions/workflows/R-CMD-check.yaml)
[![Codecov](https://codecov.io/gh/openalexPro/openalexPro/graph/badge.svg)](https://app.codecov.io/gh/openalexPro/openalexPro)
[![Lifecycle: maturing](https://img.shields.io/badge/lifecycle-maturing-blue.svg)](https://lifecycle.r-lib.org/articles/stages.html)
[![License: GPL-2+](https://img.shields.io/badge/License-GPL%20%3E%3D%202-blue.svg)](https://www.gnu.org/licenses/gpl-2.0)
[![Docs](https://img.shields.io/badge/docs-pkgdown-blue)](https://openalexpro.github.io/openalexPro/)

Core API client — build queries (classic filters or OpenAlex's query language, OQL), page through the results, and store them as Parquet. Resumes interrupted downloads, and processes on disk, so it scales to millions of records without RAM limits.

---

### [openalexSnowball](https://github.com/openalexPro/openalexSnowball)

[![r-universe](https://openalexpro.r-universe.dev/openalexSnowball/badges/version)](https://openalexpro.r-universe.dev/openalexSnowball)
[![main](https://img.shields.io/github/r-package/v/openalexPro/openalexSnowball/main?label=main)](https://github.com/openalexPro/openalexSnowball/tree/main)
[![dev](https://img.shields.io/github/r-package/v/openalexPro/openalexSnowball/dev?label=dev)](https://github.com/openalexPro/openalexSnowball/tree/dev)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20448982.svg)](https://doi.org/10.5281/zenodo.20448982)
[![CI](https://github.com/openalexPro/openalexSnowball/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/openalexPro/openalexSnowball/actions/workflows/R-CMD-check.yaml)
[![Codecov](https://codecov.io/gh/openalexPro/openalexSnowball/graph/badge.svg)](https://app.codecov.io/gh/openalexPro/openalexSnowball)
[![Lifecycle: maturing](https://img.shields.io/badge/lifecycle-maturing-blue.svg)](https://lifecycle.r-lib.org/articles/stages.html)
[![License: GPL-2+](https://img.shields.io/badge/License-GPL%20%3E%3D%202-blue.svg)](https://www.gnu.org/licenses/gpl-2.0)
[![Docs](https://img.shields.io/badge/docs-pkgdown-blue)](https://openalexpro.github.io/openalexSnowball/)

Snowball citation searches — expand a set of seed papers by the works that cite them and the works they cite, written as partitioned Parquet. Runs live against the OpenAlex API (via openalexPro) or offline against a local snapshot (via openalexSnapshot).

---

### [openalexConvert](https://github.com/openalexPro/openalexConvert)

[![r-universe](https://openalexpro.r-universe.dev/openalexConvert/badges/version)](https://openalexpro.r-universe.dev/openalexConvert)
[![main](https://img.shields.io/github/r-package/v/openalexPro/openalexConvert/main?label=main)](https://github.com/openalexPro/openalexConvert/tree/main)
[![dev](https://img.shields.io/github/r-package/v/openalexPro/openalexConvert/dev?label=dev)](https://github.com/openalexPro/openalexConvert/tree/dev)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20448988.svg)](https://doi.org/10.5281/zenodo.20448988)
[![CI](https://github.com/openalexPro/openalexConvert/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/openalexPro/openalexConvert/actions/workflows/R-CMD-check.yaml)
[![Codecov](https://codecov.io/gh/openalexPro/openalexConvert/graph/badge.svg)](https://app.codecov.io/gh/openalexPro/openalexConvert)
[![Lifecycle: experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://lifecycle.r-lib.org/articles/stages.html)
[![License: GPL-2+](https://img.shields.io/badge/License-GPL%20%3E%3D%202-blue.svg)](https://www.gnu.org/licenses/gpl-2.0)
[![Docs](https://img.shields.io/badge/docs-pkgdown-blue)](https://openalexpro.github.io/openalexConvert/)

Export a Parquet corpus to BibTeX, BibLaTeX, CSL JSON, Markdown, LaTeX, HTML, or PDF via Pandoc, or straight into Zotero — with the OpenAlex ID in Extra, re-exports that skip, update or overwrite, nested collections, and tags in both directions.

---

### [openalexSnapshot](https://github.com/openalexPro/openalexSnapshot)

[![r-universe](https://openalexpro.r-universe.dev/openalexSnapshot/badges/version)](https://openalexpro.r-universe.dev/openalexSnapshot)
[![main](https://img.shields.io/github/r-package/v/openalexPro/openalexSnapshot/main?label=main)](https://github.com/openalexPro/openalexSnapshot/tree/main)
[![dev](https://img.shields.io/github/r-package/v/openalexPro/openalexSnapshot/dev?label=dev)](https://github.com/openalexPro/openalexSnapshot/tree/dev)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.20448992.svg)](https://doi.org/10.5281/zenodo.20448992)
[![CI](https://github.com/openalexPro/openalexSnapshot/actions/workflows/R-CMD-check.yaml/badge.svg)](https://github.com/openalexPro/openalexSnapshot/actions/workflows/R-CMD-check.yaml)
[![Codecov](https://codecov.io/gh/openalexPro/openalexSnapshot/graph/badge.svg)](https://app.codecov.io/gh/openalexPro/openalexSnapshot)
[![Lifecycle: experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://lifecycle.r-lib.org/articles/stages.html)
[![License: GPL-2+](https://img.shields.io/badge/License-GPL%20%3E%3D%202-blue.svg)](https://www.gnu.org/licenses/gpl-2.0)
[![Docs](https://img.shields.io/badge/docs-pkgdown-blue)](https://openalexpro.github.io/openalexSnapshot/)

Offline work with a local OpenAlex snapshot in Parquet — ID, DOI and citation indexes, record extraction by OpenAlex ID or DOI at scale, and an offline citation graph (works citing or cited by a paper). Pure R over DuckDB; nothing to compile.

---

### [openalexVectorComp](https://github.com/openalexPro/openalexVectorComp)

[![r-universe](https://openalexpro.r-universe.dev/openalexVectorComp/badges/version)](https://openalexpro.r-universe.dev/openalexVectorComp)
[![main](https://img.shields.io/github/r-package/v/openalexPro/openalexVectorComp/main?label=main)](https://github.com/openalexPro/openalexVectorComp/tree/main)
[![dev](https://img.shields.io/github/r-package/v/openalexPro/openalexVectorComp/dev?label=dev)](https://github.com/openalexPro/openalexVectorComp/tree/dev)
[![DOI](https://zenodo.org/badge/DOI/10.5281/zenodo.19607514.svg)](https://doi.org/10.5281/zenodo.19607514)
[![CI](https://github.com/openalexPro/openalexVectorComp/actions/workflows/pr-checks.yml/badge.svg)](https://github.com/openalexPro/openalexVectorComp/actions/workflows/pr-checks.yml)
[![Codecov](https://codecov.io/gh/openalexPro/openalexVectorComp/graph/badge.svg)](https://app.codecov.io/gh/openalexPro/openalexVectorComp)
[![Lifecycle: experimental](https://img.shields.io/badge/lifecycle-experimental-orange.svg)](https://lifecycle.r-lib.org/articles/stages.html)
[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)
[![Docs](https://img.shields.io/badge/docs-pkgdown-blue)](https://openalexpro.github.io/openalexVectorComp/)

Text embedding, cosine-distance scoring, and threshold calibration — backend-neutral (HuggingFace, OpenAI, TEI). Adds semantic similarity search to the ecosystem.

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
- **Pure R** — none of the packages has compiled code of its own, so nothing needs a toolchain to install.

## Contributing

Issues and pull requests are welcome on the individual package repositories. Please open an issue before starting large changes.

## Acknowledgements

This ecosystem builds on the excellent [openalexR](https://github.com/ropensci/openalexR) package and the [OpenAlex](https://openalex.org) team's commitment to open scholarly infrastructure.

## Disclaimer

The packages are provided **as is**. The authors are not affiliated with OpenAlex.
