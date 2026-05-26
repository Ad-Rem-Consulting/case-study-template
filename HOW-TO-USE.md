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

Add an entry to `src/data/case-studies.ts` in the Website repo:

```ts
{
  slug: 'acme-portal',
  client: 'Acme Industries',
  project: 'Customer Portal Rebuild',
  outcome: '60% reduction in support tickets in Q1.',
  stack: ['Next.js', 'Postgres', 'Vercel'],
  repoUrl: 'https://github.com/Ad-Rem-Consulting/case-study-acme-portal',
  liveUrl: undefined,   // or 'https://acme-portal.example.com' if public
  year: 2026,
}
```

Push the Website change. The Selected Work section on adrem.services
auto-renders the new card.

## 5. Delete this HOW-TO-USE.md from the new repo

It's only here in the template; case-study repos shouldn't carry it.
