# Results

All five tested forms returned `401` with a 144-byte HTML response and `server: awselb/2.0`. No coupon structure, IDs, or backend trace headers were exposed. Authenticated response and IDOR checks remain blocked pending an authorized `sid`.
