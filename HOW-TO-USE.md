# How to use this template

This is the case-study scaffold for [Ad Rem](https://adrem.services). When a
client engagement ships and you want to document it publicly:

## 1. Create the case-study repo

Use the GitHub UI's "Use this template" button, or via gh CLI:

```bash
gh repo create Ad-Rem-Consulting/case-study-<slug> \
  --template Ad-Rem-Consulting/case-study-template \
  --public \
  --description "<client> — <one-line outcome>"
```

Slug convention: `case-study-<client-or-project-shortname>`. Examples:
- `case-study-acme-portal`
- `case-study-bookings-tool`
- `case-study-nps-dashboard`

## 2. Fill in README.md

Replace every `{{handlebar}}` placeholder with real content. Sections in
order of writing difficulty (easiest first):
1. **Stack** — just list what you used
2. **Timeline & engagement shape** — facts
3. **The problem** — what motivated the work
4. **What we built** — what you actually did
5. **Outcome** — the hardest section, because it requires post-launch data

If outcome data isn't available yet, ship the case study without it and add
a *"Results pending — final report due {{date}}"* note. Update the repo
when the data lands.

## 3. Add screenshots

Drop 2-4 PNGs into `screenshots/`. Compress to ~150KB each (Squoosh or
similar). Caption each one in the README so a visitor scrolling through
can follow the story without clicking the images.

## 4. Surface it on adrem.services

The Website uses Astro Content Collections (not a TS data file). Two
pieces need to land in the Website repo:

**(a)** Drop a new markdown file at `Website/src/content/case-studies/<slug>.md`.
The filename (minus `.md`) becomes the URL slug — the page renders at
`/work/<slug>`. The YAML frontmatter must match the Zod schema in
`Website/src/content/config.ts`:

````markdown
---
client: Acme Industries
project: Customer Portal Rebuild
outcome: 60% reduction in support tickets in Q1.
stack:
  - Next.js
  - Postgres
  - Vercel
repoUrl: https://github.com/Ad-Rem-Consulting/case-study-acme-portal
liveUrl: https://acme-portal.example.com    # omit the field entirely if private
year: 2026
thumbnail: /case-studies/acme-portal-home.jpg
timeline: 6 weeks
engagement: Fixed-price
order: 3                                     # lower numbers surface first
---

Mirror the body of the case-study repo's README here (without the
`<!-- ad-rem-case-study: ... -->` HTML comment header — the YAML
frontmatter above replaces it on the Website side).
````

**(b)** Drop the thumbnail at `Website/public/case-studies/<slug>-<name>.jpg`.
The path must match the `thumbnail` field above. Keep file size around
~150–200KB.

**(c)** Push the `Website` repo. Vercel watches the Website repo directly
and rebuilds on push to `main`. The new card surfaces in the homepage's
Selected Work section and the detail page renders at `/work/<slug>`.

## 5. Delete this HOW-TO-USE.md from the new repo

It's only here in the template; case-study repos shouldn't carry it.
