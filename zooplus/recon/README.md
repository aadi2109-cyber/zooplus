# Reconnaissance Database — zooplus.de

## Overview

This directory contains a persistent, reusable reconnaissance database for authorized reconnaissance of `zooplus.de` and `zooplus.com`.

## Directory Structure

```
recon/
├── scope/
│   ├── scope.csv          # Canonical scope (in-scope targets only)
│   └── scope.json         # JSON version of scope
│
├── data/                  # Canonical data (JSONL)
│   ├── hosts.jsonl        # Host records
│   ├── dns.jsonl          # DNS records
│   ├── http.jsonl         # HTTP/HTTPS service records
│   ├── technologies.jsonl # Technology fingerprints
│   ├── urls.jsonl         # Discovered URLs
│   ├── observations.jsonl # General-purpose observations
│   └── interesting.jsonl  # Priority queue for future investigation
│
├── runs/
│   └── <timestamp>/       # Per-run data
│       ├── commands.json  # Commands executed
│       ├── httpx.jsonl    # Raw httpx output
│       ├── raw-output/    # Raw tool output files
│       └── metadata.json  # Run metadata
│
├── exports/               # CSV exports for interoperability
│   ├── hosts.csv
│   ├── http.csv
│   ├── technologies.csv
│   └── interesting.csv
│
├── schema/                # JSON Schema definitions
│   ├── hosts.schema.json
│   ├── http.schema.json
│   ├── technologies.schema.json
│   └── observations.schema.json
│
├── README.md              # This file
└── recon-summary.json     # Machine-readable summary
```

## Data Formats

- **JSONL** (line-delimited JSON) for all canonical data — one record per line
- **CSV** for exports — flat tables for interoperability with spreadsheets and tools
- **JSON Schema** for validation of record structure
- **JSON** for metadata and summary

## Field Definitions

### hosts.jsonl

| Field | Type | Description |
|-------|------|-------------|
| host_id | string | Stable identifier (host_NNN) |
| hostname | string | Canonical hostname |
| fqdn | string | Fully qualified domain name |
| domain | string | Base domain |
| scope | string | in_scope / out_of_scope / unknown |
| scope_source | string | Source row in scope CSV |
| status | string | up / down / unknown |
| ips | array | List of IP addresses |
| first_seen | datetime | ISO 8601 timestamp |
| last_seen | datetime | ISO 8601 timestamp |
| tags | array | Tags for categorization |

### http.jsonl

| Field | Type | Description |
|-------|------|-------------|
| http_id | string | Stable identifier (http_NNN) |
| host_id | string | Reference to hosts.jsonl |
| url | string | Full URL |
| scheme | string | http or https |
| host | string | Hostname |
| port | integer | Port number |
| status_code | integer | HTTP status code |
| title | string | Page title |
| server | string | Server header |
| content_type | string | Content-Type header |
| webserver | string | Inferred web server |
| cdn | string | CDN in use |
| tls_version | string | TLS version |
| tls_cipher | string | TLS cipher |
| cert_cn | string | Certificate CN |
| cert_san | string | Certificate SAN |
| technologies | array | Detected technologies |
| timestamp | datetime | ISO 8601 timestamp |
| run_id | string | Reference to run |

### technologies.jsonl

| Field | Type | Description |
|-------|------|-------------|
| technology_id | string | Stable identifier (tech_NNN) |
| http_id | string | Reference to http.jsonl |
| host_id | string | Reference to hosts.jsonl |
| name | string | Technology name |
| version | string | Version (unknown if not detected) |
| category | string | web_server, reverse_proxy, cdn, waf, frontend, javascript, backend, framework, cms, analytics, ecommerce, cloud, authentication, database, infrastructure, other |
| source | string | Tool that detected it |
| evidence | string | What led to this detection |
| confidence | string | high, medium, low |
| first_seen | datetime | ISO 8601 timestamp |
| last_seen | datetime | ISO 8601 timestamp |

### observations.jsonl

| Field | Type | Description |
|-------|------|-------------|
| observation_id | string | Stable identifier (obs_NNN) |
| target_id | string | Reference to any entity |
| type | string | http_header, cookie, inline_script, dns, technology, redirect, interesting, other |
| value | string | Observed value |
| source | string | Tool that observed it |
| evidence | string | Raw evidence |
| confidence | string | high, medium, low |
| run_id | string | Reference to run |
| timestamp | datetime | ISO 8601 timestamp |

### interesting.jsonl

| Field | Type | Description |
|-------|------|-------------|
| observation_id | string | Stable identifier |
| host_id | string | Reference to hosts.jsonl |
| hostname | string | Hostname |
| priority | string | high, medium, low |
| reason | string | Why this is interesting |
| evidence | string | Supporting evidence |
| source | string | Tool that found it |
| run_id | string | Reference to run |
| timestamp | datetime | ISO 8601 timestamp |

## Querying the Data

### List all hosts

```bash
jq '.hostname' recon/data/hosts.jsonl
```

### Find all HTTP services with status 200

```bash
jq 'select(.status_code == 200)' recon/data/http.jsonl
```

### Find technologies with high confidence

```bash
jq 'select(.confidence == "high")' recon/data/technologies.jsonl
```

### Find interesting assets by priority

```bash
jq 'select(.priority == "high")' recon/data/interesting.jsonl
```

### Count technologies by category

```bash
jq -r '.category' recon/data/technologies.jsonl | sort | uniq -c | sort -rn
```

### Find all observations for a specific host

```bash
jq 'select(.target_id == "host_001")' recon/data/observations.jsonl
```

### Grep for a specific technology

```bash
grep -i "Next.js" recon/data/technologies.jsonl
```

### List all URLs discovered

```bash
jq '.url' recon/data/urls.jsonl
```

## Adding New Observations

1. Append to the appropriate JSONL file (data/*.jsonl)
2. Use a stable ID format: type_NNN (e.g., obs_009, tech_021)
3. Include timestamp, run_id, source, and confidence
4. Update recon-summary.json if needed

## Rerunning Reconnaissance

1. Create a new run directory: `runs/<timestamp>/`
2. Store raw output in `runs/<timestamp>/raw-output/`
3. Store metadata in `runs/<timestamp>/metadata.json`
4. Update data/*.jsonl with new findings (do NOT delete old data)
5. Update recon-summary.json
6. Update exports/ CSV files

## Historical Comparison

To compare runs:

```bash
# List all runs
ls recon/runs/

# Compare technologies between runs
jq -r '.name' recon/runs/<run1>/httpx.jsonl | sort > /tmp/run1_techs.txt
jq -r '.name' recon/runs/<run2>/httpx.jsonl | sort > /tmp/run2_techs.txt
diff /tmp/run1_techs.txt /tmp/run2_techs.txt
```

## Scope Enforcement

- Only targets listed in `scope/scope.csv` are in scope
- The scope CSV is the authority for what may be tested
- www.zooplus.de and www.zooplus.com are authorized per the scope instruction
- Discovered assets outside scope must be recorded as out-of-scope observations
- Do not probe assets outside the scope CSV

## Tool Provenance

| Tool | Version | Purpose |
|------|---------|---------|
| httpx | Python httpx CLI | HTTP probing, header analysis |
| dig | BIND 9.x | DNS resolution |
| host | bind9-host | DNS lookup |
| nslookup | dnsutils | DNS lookup |

## Safety Notes

- This is authorized reconnaissance only
- No exploitation, brute forcing, or credential attacks were performed
- No intrusive scanning was done
- All data was collected through safe, read-only DNS and HTTP queries