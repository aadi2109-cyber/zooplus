# Results

- Both homepages expose the same Next.js stack and `server: istio-envoy`, `x-powered-by: Next.js`, HSTS, CloudFront, and domain-scoped guest `sid` behavior.
- `.com` bonus-points returned `204` and issued a `.zooplus.com` guest `sid`; `.com` coupons returned `401` from `awselb/2.0`.
- No CSP header was present in the captured homepage response headers, so no `unsafe-inline`, `unsafe-eval`, or wildcard CSP directive was observed.
- Config drift is primarily locale/site settings and feature toggles; the core API route map is shared. Full raw homepage/config extracts and unified diff are preserved under `raw/`.
- Authenticated `.de` versus `.com` comparison remains blocked without authorized sessions.
