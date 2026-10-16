# Handoff: read this first

RR Academia & Industry Connect marketing site with an admin panel (React 19, Vite, Tailwind 4, Firebase/Firestore, Cloudinary, Vercel).

This file holds the working state between chats, so a new chat never needs the old one. The working rules (workflows, ultracode, effort, new chat or continue) live in `~/.claude/CLAUDE.md`, not here.

- **At the start of a chat:** read this file, then do the first open item under "Next steps", unless the user asks for something else.
- **At the end of a task:** update "State", "Next steps" and "Last updated".

Last updated: 2026-10-16 (UPL Limited partner replaced with UPL University of Sustainable Technology)

## State

- **Branch and last commit:** `main`, local commit "Replace UPL Limited partner with UPL University of Sustainable Technology" (pushed to origin/main 2026-10-16).
- **Done:** new logo `public/images/partners/upl-university-logo.png` (transparent cutout of the client's logo); seed partner `partner-upl` in `src/config/siteContent.ts` renamed, re-described and linked to https://upluniversity.ac.in; fallback emblem and section intro in `PartnersSection.tsx` updated; image logos may now use the full 56 px emblem height.
- **Unfinished:** the live Firestore doc `partners/partner-upl` overrides the code seed (see Next step 1).
- **How to run and check it:** `npm install`, `npm run build`, `npx vite preview`. Partners section is `#partners` on `/`. To see seed data instead of Firestore, block `firestore.googleapis.com` in Playwright.

## Next steps (in order)

| # | Step | Ultracode? | Effort |
|---|---|---|---|
| 1 | After deploying, in Admin → Industry Partners edit the UPL card: name "UPL University of Sustainable Technology", logo URL `/images/partners/upl-university-logo.png`, category "University", website `https://upluniversity.ac.in`, new description. Live Firestore currently has logo `/images/upl.png.jpeg` (missing file, broken image) and the old UPL Limited description. | No | Low |

**Message for the next chat:** `Read docs/HANDOFF.md and do Next step 1 (update the UPL partner in Firestore).`

## Waiting on the client or the user

- [NEED: client to confirm the UPL University card description ("collaborating on sustainable technology education, student internships and sustainability research") reflects the real partnership.]

## Decisions (and why)

- 2026-10-16: kept doc id `partner-upl`. Why: Firestore already has a doc with that id; a new id would show two UPL cards.

## Gotchas

- Firestore partner docs override `verifiedPartners` seeds by id, so code edits to a partner don't show on the live site once an admin has saved it.
- `vite preview` serves index.html (HTTP 200) for missing images, so a 200 doesn't prove a file exists.
