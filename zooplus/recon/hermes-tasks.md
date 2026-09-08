# Hermes Task Queue — Zooplus BBP
Date: 2026-09-08
Priority order: top to bottom.

---

## TASK 1 — Probe `content-api.private.zooplus.net` directly
**Priority:** High
**Reason:** Absolute URL exposed in client-side JS — private subdomain that bypasses CloudFront WAF. May have weaker auth enforcement.

```bash
curl -sv https://content-api.private.zooplus.net/api/v1
curl -sv https://content-api.private.zooplus.net/api/v1/ -H "Accept: application/json"
```

**Record:** HTTP status, response headers (especially auth-related), server header, any data returned. If 200 with data, escalate immediately.

---

## TASK 2 — Map bonus points endpoint structure
**Priority:** High
**Reason:** `/loy/api/bonus-points/v1/customers/balance` — "customers" in the path strongly implies a customer ID parameter. Prime IDOR candidate.

```bash
# Unauthenticated baseline
curl -sv https://www.zooplus.de/loy/api/bonus-points/v1/customers/balance

# Try common ID param patterns
curl -sv https://www.zooplus.de/loy/api/bonus-points/v1/customers/{id}/balance
curl -sv https://www.zooplus.de/loy/api/bonus-points/v1/customers/1/balance
curl -sv https://www.zooplus.de/loy/api/bonus-points/v1/customers/me/balance
```

**Record:** Full request/response for each. Note how customer identity is resolved — JWT sub claim, session cookie, explicit ID param, or path segment.

---

## TASK 3 — Semiprotected endpoint auth enforcement check
**Priority:** High
**Reason:** `/semiprotected/` tier is ambiguous — need to know what it actually enforces before manual testing.

Endpoints to probe unauthenticated:
```
/semiprotected/api/audiences-api
/semiprotected/api/zoochat
/semiprotected/api/contact-form
/semiprotected/api/content-api/api/v1
```

```bash
# No session
curl -sv https://www.zooplus.de/semiprotected/api/audiences-api
# With invalid/empty token
curl -sv https://www.zooplus.de/semiprotected/api/audiences-api -H "Authorization: Bearer invalid"
```

**Record:** 401 vs 403 vs 200 — this determines if "semiprotected" means guest-token-required or rate-limited-public.

---

## TASK 4 — Third-party JS host recon
**Priority:** Medium
**Reason:** `REACT_APP_PIXEL_EXECUTOR_URL` points to `mkt-tech.omt-services.com/main.js` — external domain loading JS on zooplus pages. Not in scope but informs supply chain risk.

```bash
whois omt-services.com
dig omt-services.com A
dig omt-services.com NS
curl -sv https://mkt-tech.omt-services.com/main.js | head -50
```

**Record:** Registrar, registration date, NS provider, JS content summary. Flag if domain looks weakly held or recently registered.

---

## TASK 5 — `/protected/api/coupons` structure mapping
**Priority:** Medium
**Reason:** Coupons tied to user accounts — potential for horizontal privilege escalation (read/apply another user's coupons).

```bash
# Unauthenticated baseline
curl -sv https://www.zooplus.de/protected/api/coupons
```

**Record:** Auth mechanism (cookie vs token), response structure, whether coupon IDs appear in response.

---

## TASK 6 — `/myaccount/api/customer-product-picture-service` vs `/protected/api/customer-product-picture-service`
**Priority:** Low
**Reason:** Same service exposed on two different path prefixes (`/myaccount/` and `/protected/`). Path confusion may lead to auth bypass if one prefix enforces auth and the other doesn't.

```bash
curl -sv https://www.zooplus.de/myaccount/api/customer-product-picture-service
curl -sv https://www.zooplus.de/protected/api/customer-product-picture-service
```

**Record:** Compare HTTP status and response headers between both paths unauthenticated.

---

## Notes for Hermes
- **Do not brute-force** — CloudFront WAF will 403 everything and burn rate limit. Work with known paths only.
- **Delay ≥ 1s** between requests on any endpoint.
- All findings → append to `zooplus/recon/data/interesting.jsonl` with appropriate priority.
- New run outputs → `zooplus/recon/runs/<timestamp>/`.
- Push to GitHub after each task completes.
