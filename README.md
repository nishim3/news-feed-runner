# news-feed-runner

Scheduled runner for a private news analysis pipeline. Every 30 minutes,
the workflow checks out the private repository and executes its pipeline
script; all code, prompts, and configuration live in the private repo.

This repository is public only so the workflow gets unlimited free
GitHub Actions minutes. There is nothing else to see here.

## Setup (one time)

Repository **secrets** (Settings → Secrets and variables → Actions):

| Secret | Value |
|--------|-------|
| `PRIVATE_REPO_TOKEN` | Fine-grained PAT with **Contents: Read and write** on the private repo only |
| `OPENROUTER_API_KEY` | Optional. OpenRouter key for the classifier; without it, runs crawl and dedup but skip classification |

Optional repository **variables**:

| Variable | Meaning |
|----------|---------|
| `OPENROUTER_MODEL` | Override the default OpenRouter model |
| `PIPELINE_LIMIT` | Classify only the newest N articles per run |
| `NEWS_ANALYZER_SOURCES` | Which outlets to crawl (e.g. `all`) |
| `DATA_RETENTION_DAYS` | Days of runs kept in the published data dir (default 14) |
