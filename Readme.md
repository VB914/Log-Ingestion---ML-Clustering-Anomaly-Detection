# LogIntel — Multi-Level Log Ingestion + ML Clustering + Anomaly Detection

LogIntel is a three-level log analytics pipeline built in Python. It starts with robust log ingestion/parsing (Level 1), then adds unsupervised ML to group similar log events (Level 2), and finally flags rare/unusual messages via anomaly detection (Level 3).

---

## Key Features

### Level 1 — Ingestion & Parsing (Data Understanding)
- Recursively scans a directory for `.log` and `.txt` files
- Parses log lines into structured records with:
  - `timestamp`
  - `level` (normalized to `INFO` / `WARN` / `ERROR` / `UNKNOWN`)
  - `message`
  - `raw` line
  - `source_file`
- Handles malformed lines without crashing
- Produces ingestion statistics:
  - total lines, parsed records, malformed lines, per-level counts
- Optional JSON export of parsed records

### Level 2 — AI/ML (Unsupervised Clustering)
- Builds TF-IDF vectors from log messages
- Uses KMeans to group similar messages into clusters
- Outputs cluster summaries with top keywords per cluster

### Level 3 — Anomaly Detection
- Uses IsolationForest on TF-IDF vectors
- Surfaces top-K anomalous log messages with anomaly scores

---

## Project Structure

