# Results

- 18 bundles downloaded for each host.
- No AWS access key, Firebase key, Stripe live secret, private-key header, or credential confirmed by the exact indicator scan.
- Public Sentry DSN and intended API configuration are present in the downloaded application data; these are public client configuration, not confirmed secrets.
- API references include the configured bonus-points, coupons, audiences, zoochat, and content API routes plus runtime loyalty-management paths.
- Broad `token`/`secret` matches include library code and configuration names; they were not validated as credentials.
