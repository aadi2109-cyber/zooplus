# Parameter Fuzzing Plan — zooplus.de

## Overview

This plan defines a safe, controlled parameter fuzzing approach for authorized reconnaissance of `zooplus.de` and `zooplus.com`.

## Tools Available

| Tool | Path | Version | Purpose |
|------|------|---------|---------|
| arjun | /usr/bin/arjun | python-arjun | Parameter discovery |
| ffuf | /usr/bin/ffuf | ffuf | Directory/endpoint discovery |
| wfuzz | /usr/bin/wfuzz | wfuzz | Parameter fuzzing |
| paramspider | - | - | NOT INSTALLED |
| paramminer | - | - | NOT INSTALLED |
| qsreplace | - | - | NOT INSTALLED |

## Arjun Wordlists

| Wordlist | Path | Size |
|----------|------|------|
| small | /usr/lib/python3/dist-packages/arjun/db/small.txt | 835 words |
| medium | /usr/lib/python3/dist-packages/arjun/db/medium.txt | 10,984 words |
| large | /usr/lib/python3/dist-packages/arjun/db/large.txt | 25,889 words |

## Scope

- www.zooplus.de (in_scope)
- www.zooplus.com (in_scope)

## Phases

### Phase 1: Arjun GET - Small Wordlist
- Tool: arjun
- Method: GET
- Wordlist: small (835 words)
- Targets: www.zooplus.de, www.zooplus.com
- Threads: 3, Delay: 1s, Timeout: 15s

### Phase 2: Arjun GET - Medium Wordlist
- Tool: arjun
- Method: GET
- Wordlist: medium (10,984 words)
- Targets: www.zooplus.de, www.zooplus.com
- Threads: 3, Delay: 1s, Timeout: 15s

### Phase 3: Arjun POST
- Tool: arjun
- Method: POST
- Wordlist: small (835 words)
- Targets: www.zooplus.de, www.zooplus.com
- Threads: 3, Delay: 1s, Timeout: 15s

### Phase 4: Arjun JSON
- Tool: arjun
- Method: JSON
- Wordlist: small (835 words)
- Targets: www.zooplus.de, www.zooplus.com
- Threads: 3, Delay: 1s, Timeout: 15s

### Phase 5: ffuf Directory Discovery
- Tool: ffuf
- Wordlist: /usr/share/wordlists/dirb/common.txt
- Targets: www.zooplus.de, www.zooplus.com
- Threads: 5, Delay: 1s, Timeout: 15s

### Phase 6: wfuzz Parameter Fuzzing
- Tool: wfuzz
- Wordlist: /usr/share/wordlists/wfuzz/params.txt
- Targets: www.zooplus.de, www.zooplus.com
- Threads: 3, Delay: 1s, Timeout: 15s

## Safety Rules

- Rate limit: minimum 1 request per second
- Max threads: 5
- Timeout: 15 seconds per request
- No credential brute-forcing
- No vulnerability exploitation
- Only in-scope targets
