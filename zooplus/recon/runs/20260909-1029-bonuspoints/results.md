# Results

- Canonical endpoint: `204`, empty body, `server: istio-envoy`, `x-lambda-region: eu-central-1`, and a fresh HttpOnly/Secure/SameSite=Lax `sid` cookie for `.zooplus.de`.
- Trailing slash, v2, collection root, and customer collection variations returned `404`.
- `/customers/1/balance` and `/customers/me/balance` returned `401`.
- No 200 response or customer identifier was observed. Cross-account isolation and cookie-substitution tests remain unperformed without two authorized test sessions.

Raw evidence is under `raw/`; `summary.txt` contains the status matrix.
