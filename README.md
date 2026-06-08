# nyrix-web

Product landing page for **Nyrix: BME Tracker** — hosted at [www.aazhara.in](https://www.aazhara.in).

The actual application lives at [nyrix.aazhara.in](https://nyrix.aazhara.in).

## Hosting

Deployed via **Azure Static Web Apps** (`aazhara-web`), in resource group `bme-tracker-rg`.

## Local Preview

Just open `index.html` in a browser — no build step required.

## Deploy

```bash
# Copy to dist dir (source and artifact must differ for SWA CLI)
cp index.html /tmp/nyrix-web-dist/

# Deploy
TOKEN=$(az staticwebapp secrets list -n aazhara-web --query 'properties.apiKey' -o tsv)
npx @azure/static-web-apps-cli deploy /tmp/nyrix-web-dist \
  --deployment-token "$TOKEN" \
  --env production
```

## DNS Setup (Wix DNS for aazhara.in)

| Type  | Name  | Value                                          |
|-------|-------|------------------------------------------------|
| CNAME | `www` | `purple-forest-0f4e9fc10.7.azurestaticapps.net` |

SSL is auto-provisioned by Azure via Let's Encrypt once the custom domain is validated.
