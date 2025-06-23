# Sync to FDP

This repository provides a Python script and a GitHub Actions workflow to automatically synchronize model metadata to a FAIR Data Point (FDP) on merged pull requests labeled `sync`.

## Installation

```bash
# Create and activate a virtual environment
python -m venv .venv
source .venv/bin/activate        # macOS/Linux
.\.venv\\Scripts\\activate    # Windows

# Install dependencies
pip install --upgrade pip
pip install -r requirements.txt
```

## Configuration

1. Copy the example environment file:

   ```bash
   cp .env.example .env
   ```
2. Open `.env` and fill in your values:

   ```dotenv
   FDP_EMAIL=you@example.com
   FDP_PASSWORD=supersecret
   FDP_URL=https://fdp.example.com/api
   MODELS_DIR=./models
   METADATA_FILENAME=metadata.ttl
   CATALOG_URI=https://fdp.example.com/catalogs/<CATALOG_ID>
   ```
3. (For CI) Add the same variables as GitHub Secrets or in your chosen Environment.

## Quick Start

Run the sync locally:

```bash
python scripts/sync_to_fdp.py
```

## GitHub Actions

The workflow `.github/workflows/sync.yml` automatically:

* Triggers on merged PRs with the `sync` label
* Sets up Python and installs dependencies
* Loads secrets as environment variables
* Executes the sync script

No further setup is required once your secrets are configured.
