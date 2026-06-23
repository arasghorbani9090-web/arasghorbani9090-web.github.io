# DNS setup for `qorbani.qa`

The custom domain is already configured on GitHub Pages and committed via the `CNAME` file.
The last step is at your **domain registrar** (where you bought `qorbani.qa`).

## 1. Apex domain → GitHub Pages

Add these four **A records** for the root (`@`) host:

| Type | Host | Value |
| --- | --- | --- |
| A | `@` | `185.199.108.153` |
| A | `@` | `185.199.109.153` |
| A | `@` | `185.199.110.153` |
| A | `@` | `185.199.111.153` |

(Optional, for IPv6 — add these **AAAA records** too:)

| Type | Host | Value |
| --- | --- | --- |
| AAAA | `@` | `2606:50c0:8000::153` |
| AAAA | `@` | `2606:50c0:8001::153` |
| AAAA | `@` | `2606:50c0:8002::153` |
| AAAA | `@` | `2606:50c0:8003::153` |

## 2. `www` subdomain (recommended)

| Type | Host | Value |
| --- | --- | --- |
| CNAME | `www` | `arasghorbani9090-web.github.io.` |

## 3. Verify & enable HTTPS

1. Wait for DNS to propagate (minutes to a few hours; `.qa` can be on the slower side).
2. Check it: `nslookup qorbani.qa` should return the GitHub IPs above.
3. In the repo: **Settings → Pages** — once you see **"DNS check successful"**, tick **Enforce HTTPS**.

Until DNS resolves, the site stays live at **https://arasghorbani9090-web.github.io/**.

## Notes
- Don't delete the `CNAME` file in this repo — it tells GitHub which domain to serve.
- Apex domains **must** use A/AAAA records (not a CNAME), per your registrar's rules.
