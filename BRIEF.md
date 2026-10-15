# Framewise.ai website: build brief

Source of truth for visuals: `design/Main.dc.html`, `design/About.dc.html`, `design/Blog.dc.html`.
These are design mockups in a custom format (`<x-dc>`, `<sc-for>`, `{{holes}}`, inline styles). They are NOT runnable. Read them as a visual and copy spec, then rebuild as real components. Open each file's markup for exact colours, spacing, type sizes and copy.

## Pages
1. `/` Homepage, in this exact order: header, hero, logo marquee, projects (4 cards), contact, footer. No other sections.
2. `/about` About Us.
3. `/blog` Blog posts plus a Gallery section (`#gallery`) filterable by project.

## Stack (recommended)
Next.js (App Router) + TypeScript + Tailwind. Blog posts as MDX files in `content/posts/`. Gallery driven by `content/gallery.json` plus images in `public/gallery/`, so photos can be added without touching components. Contact form posts to an API route (provider TBD).

## Design tokens
- Font: Manrope (400/500/600/700), the only typeface.
- Navy text `#14233B`, secondary text `#5B6B82` / `#3F4E66`.
- Logo blues: deep `#2E5391`, mid `#4775C9`. Hover/dark `#23437A`.
- Tints: `#F7FAFF`, `#EEF5FF`, `#DCEAFF`, `#9DB8E8`. Borders `#E3EAF4`, `#EDF1F7`.
- White dominates. No purple, no neon, no large dark sections.
- Radii: 8px buttons/inputs, 14-16px cards. Max content width 1264px, 40px gutters (20px mobile). Spacing in multiples of 8.
- Logo mark: three rounded bars (SVG in the header markup). Replace with the official asset when available.

## Behaviour requirements
- Header: logo, Projects, Blog, About Us, Contact. Sticky, translucent. Mobile: accessible menu button (aria-label, aria-expanded), closes after navigation, keyboard and touch friendly.
- Projects and Contact scroll smoothly to sections on the homepage; About and Blog are separate routes.
- Logo marquee: seamless infinite loop (duplicated track, translateX -50%), pauses on hover, honours `prefers-reduced-motion`. Currently placeholders only.
- Project cards: small, static (no card animations), GitHub link top right on VoicEra and Dhara only, opening in a new tab with rel="noopener".
- Visible focus states, real links/buttons, text contrast at least 4.5:1.

## Content rules (do not break these)
- Do not invent customers, partners, team bios, metrics or certifications.
- Do not write "on-prem" or make security/compliance guarantees. Hint at fit-to-environment only.
- Placeholders stay clearly marked until real assets exist: client logos, team section, gallery photos, blog post bodies.

## Open items to resolve with the owner before launch
1. VoicEra and Dhara are public projects launched by MeitY/BHASHINI and the Delhi government respectively. Framewise is not named in any public source found. Add a one-line role statement to each card (for example "Engineering partner") and confirm COSS is fine being linked.
2. Dhara's card copy is derived from the GitHub README. Confirm it.
3. "120,000+ minutes in conversation" (Mock Interviews) is unverified. Confirm it is an auditable number.
4. Confirm what the reinforcement learning improves (interviewer questions vs feedback).
5. Contact details currently use a personal address (kowshik@framewise.ai), a personal Calendly link and a LinkedIn page still named "cliqq-ai". Set up a general address and rename the page.
6. Gallery photos: only the Data DHARA logo (`assets/dhara-logo.png`, from the Dhara repo, Apache-2.0 project) is real. Use the team's own launch photos for the rest. Do not hotlink press images.
7. Contact form is design-only. Choose a handler (email service, CRM, or form backend).

## Suggested first steps
1. Scaffold the app, set up Tailwind tokens and the Manrope font.
2. Build shared Header, Footer and Section components, then the homepage.
3. Build About, then Blog with MDX + gallery filter.
4. Add the contact API route, metadata/OG tags, sitemap, and a Lighthouse pass.
