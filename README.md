# MedGuardAI - Medicare Fraud Detection

Data ingestion pipeline for Medicare Part B claims data.

## Setup

```bash
pip install -r requirements.txt
```

## Authentication

Set up GCP authentication:

```bash
gcloud auth application-default login
```

Or use a service account key:

```bash
export GOOGLE_APPLICATION_CREDENTIALS="/path/to/service-account-key.json"
```

## Run Ingestion

```bash
python ingest_cms_data.py
```

This will:
- Fetch Medicare Part B 2023 data from CMS API in batches of 50,000 records
- Convert each batch to Parquet format
- Upload to GCS bucket: `medguard_rawdata/raw/cms_partb_2023/`

## Configuration

Edit `ingest_cms_data.py` to adjust:
- `BATCH_SIZE`: Records per batch (default: 50,000)
- `BUCKET_NAME`: GCS bucket name
- `PROJECT_ID`: GCP project ID
