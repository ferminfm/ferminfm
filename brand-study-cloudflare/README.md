# Professional Communication Study

Low-cost multilingual naming study for the Ensenada computational-engineering startup.

## Current decision context

The survey keeps four names in the instrument:

- Ensenada Flow
- Baja California Fluid Dynamics
- Ensenum
- Enseflow

The study does **not** treat all four as equally likely business choices. The current founder preference is strongest for Ensenada Flow and Baja California Fluid Dynamics; Ensenum and Enseflow remain useful comparison anchors unless an objective conflict eliminates them.

## Architecture

- Cloudflare Worker: API + static asset delivery
- Cloudflare D1: anonymous/pseudonymous response storage
- GitHub: canonical source
- GoHighLevel: recruitment and follow-up links, not answer storage
- ChatGPT: code review, survey QA, and analysis

No Prolific dependency.

## Privacy

The survey does not request name, email, phone, employer, or exact address. Recruitment attribution is coarse-grained through query parameters such as `src`, `medium`, `campaign`, and `cohort`; do not place a contact ID, email, phone, or other direct identifier in those parameters.

Examples:

- `/es?src=technical-network&medium=whatsapp&campaign=pilot-sept&cohort=technical`
- `/en?src=ghl-email&medium=email&campaign=pilot-sept&cohort=industry`
- `/ja?src=direct&medium=link&campaign=pilot-sept&cohort=academic`

## Local development

1. Install Node.js 20+.
2. `npm install`
3. Create a local D1 database and apply migrations.
4. Replace the D1 database ID placeholder in `wrangler.jsonc` for remote deployment.
5. `npm run dev`

## Cloudflare deployment

See `docs/DEPLOYMENT.md`.

## Research interpretation

This is a best-effort market/communication study, not a representative population survey. It should be combined with trademark/commercial clearance and founder judgment. See `docs/ANALYSIS_PLAN.md`.
