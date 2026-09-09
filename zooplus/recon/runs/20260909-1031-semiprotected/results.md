# Results

- Audiences and zoochat: all tested forms returned `404`.
- Content API: GET, trailing slash, and invalid Bearer returned `404`.
- Content API OPTIONS returned `204`, `server: istio-envoy`, `x-powered-by: Express`, `x-lambda-region: eu-central-1`, and `Access-Control-Allow-Methods: GET,HEAD,PUT,PATCH,POST,POST,DELETE`; no response data or permissive origin header was observed.
- Bundle references show runtime calls under `/semiprotected/api/content-api/api/v1/loyaltyBannerMarketingProvider` plus query parameters and other loyalty-management paths; the originally tested base paths are not sufficient to reach those runtime routes.
