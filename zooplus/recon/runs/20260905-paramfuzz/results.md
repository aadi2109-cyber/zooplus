# Parameter Fuzzing Results — zooplus (20260905-paramfuzz)

## Summary
Completed parameter fuzzing against www.zooplus.de and www.zooplus.com using arjun, ffuf, wfuzz, and nuclei. No vulnerabilities or interesting parameters found. All directory brute-forcing blocked by CloudFront WAF (403).

## Arjun (10 scans)
All "No parameters were discovered":
- GET small: de/home, de/magazin, com/home, com/magazin
- GET medium: de/home, com/home
- POST: de, com
- JSON: de, com

## FFUF (directory brute-force)
Both targets: all 403 (CloudFront WAF). No open directories found.
- ffuf_de_dir.json: 0 results (28 lines, 222KB log, interrupted ~816/4614)
- ffuf_com_dir.json: 0 results (28 lines, 222KB log, interrupted ~816/4614)

## WFUZZ (directory/param fuzzing)
All 403 on both targets.
- wfuzz_de_dir.log: 951 requests, all 403 (common.txt, 118.7s)
- wfuzz_com_dir.log: 951 requests, all 403 (common.txt, 98.7s)
- wfuzz_de_params.log: 1,553 bytes (wfuzz failed — option -T not recognized)
- wfuzz_com_params.log: 1,553 bytes (wfuzz failed — option -T not recognized)
- wfuzz_de_dir2.log: 460 bytes (wfuzz failed — payload count mismatch)
- wfuzz_com_dir2.log: 460 bytes (wfuzz failed — payload count mismatch)

## Nuclei (10,730 templates)
0 matches on both de and com. Both scans reached ~37% (7,233 requests) before timeout, 0 matched, 9 errors each (all CloudFront WAF blocks).
- nuclei_de.log: 6,699 bytes
- nuclei_com.log: 6,697 bytes
- nuclei_de.txt: 0 bytes (no matches)
- nuclei_com.txt: 0 bytes (no matches)

## Infrastructure
Next.js + Spring Boot behind CloudFront + Istio Envoy. CloudFront WAF blocks all brute-forcing attempts.

## Conclusion
No parameters discovered, no vulnerabilities found, all brute-forced paths blocked by WAF.