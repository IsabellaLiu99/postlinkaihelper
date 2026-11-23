# postlinkaihelper

AI-powered helper functions for the [postlink](https://github.com/postlink-group/postlink) R package.

## Overview

This package provides two main functions:

- **`explain()`** — generates a plain-language interpretation of linkage-corrected model results using an LLM
- **`generate_report()`** — produces a formatted analysis report (Markdown, HTML, Quarto, or Quarto manuscript)

## Installation

```r
# Install from GitHub
# install.packages("remotes")
remotes::install_github("IsabellaLiu99/postlinkaihelper")
```

Requires the [postlink](https://github.com/postlink-group/postlink) package and [httr2](https://httr2.r-lib.org/) for LLM API calls.

## Usage

```r
library(postlink)
library(postlinkaihelper)

# Fit a postlink model
fit <- adjMixture(y ~ x1 + x2, data = linked_data, ...)

# Get an AI-generated plain-language explanation
explain(fit, provider = "openai", api_key = Sys.getenv("OPENAI_API_KEY"))

# Generate a full report
generate_report(fit,
  output_format = "html",
  output_file   = "report.html",
  provider      = "openai",
  api_key       = Sys.getenv("OPENAI_API_KEY")
)
```

## Supported LLM Providers

| Provider | Environment variable |
|----------|---------------------|
| OpenAI   | `OPENAI_API_KEY` |
| Anthropic | `ANTHROPIC_API_KEY` |
| Google Gemini | `GEMINI_API_KEY` |
| Ollama (local) | — |

## License

MIT
