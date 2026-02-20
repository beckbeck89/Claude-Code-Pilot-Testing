# Claudia: Claude Code vs GitHub Copilot Evaluation Hub

A collaborative repository for our team to systematically compare **Claude Code** and **GitHub Copilot** across real-world developer and data science workflows.

## Why This Exists

AI coding assistants are evolving fast, but "which one is better?" depends heavily on the task, the workflow, and the user. Instead of relying on marketing or benchmarks, we're running our own structured evaluations across the tasks we actually do — and sharing what we learn.

## Quick Start

1. **Pick a use case** from the table below
2. **Run the same task** with both Claude Code and GitHub Copilot
3. **Fill out the [scoring template](evaluation-framework/scoring-template.md)** while you work
4. **Submit your results** via PR to `results/submissions/` or open an [issue](../../issues/new?template=evaluation-submission.md)

## Use Cases

### Developer Tasks

| # | Use Case | Description |
|---|----------|-------------|
| 1 | [Build a REST API](use-cases/developer/01-build-rest-api.md) | Scaffold a full API from a spec |
| 2 | [Debug Existing Code](use-cases/developer/02-debug-existing-code.md) | Find and fix bugs in a broken codebase |
| 3 | [Refactor Legacy Code](use-cases/developer/03-refactor-legacy-code.md) | Modernize messy, outdated code |
| 4 | [Write Tests](use-cases/developer/04-write-tests.md) | Generate unit and integration tests |
| 5 | [Code Review & Explain](use-cases/developer/05-code-review-and-explain.md) | Review and explain unfamiliar code |

### Data Science Tasks

| # | Use Case | Description |
|---|----------|-------------|
| 1 | [Exploratory Data Analysis](use-cases/data-science/01-exploratory-data-analysis.md) | EDA on a new dataset |
| 2 | [Build ML Pipeline](use-cases/data-science/02-build-ml-pipeline.md) | End-to-end ML workflow |
| 3 | [Data Wrangling](use-cases/data-science/03-data-wrangling.md) | Complex data cleaning and transformation |
| 4 | [Statistical Analysis](use-cases/data-science/04-statistical-analysis.md) | Hypothesis testing and statistical modeling |
| 5 | [Visualization & Dashboard](use-cases/data-science/05-visualization-dashboard.md) | Build charts and interactive dashboards |

## Evaluation Metrics (Summary)

We score each tool on **8 dimensions** using a 1-5 scale. See [full metrics guide](evaluation-framework/metrics.md) for details.

| Metric | What It Measures |
|--------|-----------------|
| Speed | Time to first useful output and task completion |
| Accuracy | Code correctness — runs without errors, passes tests |
| Code Quality | Readability, best practices, maintainability |
| Context Understanding | Awareness of full project structure and intent |
| Iteration Efficiency | Number of prompts/edits to reach final result |
| Autonomy | Independent problem-solving vs hand-holding needed |
| Scope of Capability | Range of what the tool can do (multi-file, terminal, etc.) |
| Domain Fit | Suitability for the specific task domain (dev or DS) |

## How to Contribute

See [CONTRIBUTING.md](CONTRIBUTING.md) for the full guide. The short version:

1. Create a branch: `results/your-name/use-case-name`
2. Copy the [scoring template](evaluation-framework/scoring-template.md)
3. Run the use case with both tools, fill in your scores and notes
4. Submit a PR to `main`

## Repo Structure

```
├── evaluation-framework/    # Metrics, scoring templates, methodology
├── use-cases/
│   ├── developer/           # 5 software engineering use cases
│   └── data-science/        # 5 data science use cases
├── results/
│   └── submissions/         # Team evaluation submissions
└── resources/               # Helpful links and references
```

## Results So Far

See the [results summary](results/README.md) for aggregated findings.
