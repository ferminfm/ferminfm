# Cloudflare deployment

## Target

Deploy under a neutral `workers.dev` hostname so the URL itself does not prime any candidate name.

Suggested Worker name:

`professional-communication-study`

## First deployment

```bash
npm install
npx wrangler login
npx wrangler d1 create brand-study-db
```

Copy the returned `database_id` into `wrangler.jsonc`.

Apply the schema:

```bash
npx wrangler d1 migrations apply brand-study-db --remote
```

Create the private admin export token:

```bash
npx wrangler secret put ADMIN_TOKEN
```

Deploy:

```bash
npm run deploy
```

## Health check

After deployment:

```bash
curl https://<worker>.workers.dev/api/health
```

Expected JSON contains `ok: true` and the current `studyVersion`.

## Export responses

Use an Authorization header; never put the token in a survey URL:

```bash
curl -H "Authorization: Bearer $ADMIN_TOKEN" \
  https://<worker>.workers.dev/api/export.csv \
  -o responses.csv
```

## Cloudflare dashboard alternative

If you prefer Git-connected deployment, connect the GitHub branch/repository in Cloudflare Workers. The project root is this directory. D1 still needs to be created once and its database ID placed in `wrangler.jsonc`.

## Custom domain

Do not use `ensenadaflow.com`, `bcfd...`, or another candidate-bearing hostname while collecting first-impression data. A neutral `workers.dev` URL is preferable until naming is complete.
