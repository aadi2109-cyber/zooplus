# Parameter Fuzzing Plan — zooplus (EXECUTION)
Date: 2026-09-05
Run ID: 20260905-paramfuzz
Targets: www.zooplus.de, www.zooplus.com
Discovered endpoints: /magazin, /checkout/cart, /account/orders/reorder, /contact_form

## Safety
- Delay: 1s between requests
- Max threads: 5
- Timeout: 15s
- No auth brute-force, no exploitation

## Phases
1. arjun GET small (835 words) — both targets + discovered endpoints
2. arjun GET medium (10,984 words) — both targets (homepage only)
3. arjun POST small — both targets
4. arjun JSON small — both targets
5. ffuf directory /common.txt — both targets
6. wfuzz param fuzzing — both targets
7. nuclei tech scan (Next.js, Spring Boot)

## Outputs
- raw-output/arjun_*.json
- raw-output/ffuf_*.json
- raw-output/wfuzz_*.csv
- raw-output/nuclei_*.json
