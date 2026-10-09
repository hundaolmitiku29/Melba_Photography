# Melba Photography — Marketing Website

Phase 1 build: a complete, production-quality marketing site for Melba Photography.
No backend yet — booking, contact, and newsletter forms are fully interactive UI that
currently resolve locally rather than hitting a server. See "Next phase" below.

## Stack

- Next.js 16 (App Router) + TypeScript
- Tailwind CSS v4
- Framer Motion (hero + counter animations)
- lucide-react (icons) + a few hand-rolled SVGs for brand/social icons
- Self-hosted fonts via `@fontsource` (Fraunces + Manrope) — no runtime call to
  Google Fonts, matching the no-build-time-network-dependency approach used on the
  SaaS project.

## Getting started

\`\`\`bash
npm install
npm run dev       # http://localhost:3000
npm run build     # production build — verified clean, 20 static routes
\`\`\`

## Pages

Home, About, Services (all 12, deep-linkable via #slug), Portfolio (filterable
masonry + lightbox + before/after slider), Pricing, Booking (6-step form), Blog +
5 sample posts, Testimonials, FAQ, Contact, Privacy, Terms.

## Design system

Palette, type pairing, and the "viewfinder corner" hover signature are defined as
CSS variables and utility classes in `app/globals.css`. Light mode is a token swap
on `html.light` — no component-level branching.

## Placeholder imagery

There's no image source or CDN wired up yet, so every "photo" in the site
(`components/PhotoFrame.tsx`) is a deterministic CSS gradient + grain placeholder —
same aspect ratios and hover behavior real photography will use. Swapping in real
images later means replacing `<PhotoFrame seed={n} />` with `<Image src=... />` in
each usage; no layout changes needed.

## Next phase (not built yet)

- Backend: Supabase or Firebase (auth, Firestore/Postgres for bookings, storage for
  galleries and uploads)
- Payments: Stripe deposit checkout on the Booking flow
- Cloudinary (or equivalent) for real image hosting + optimization
- Client login, password-protected galleries, favorites/downloads, invoicing
- Admin dashboard (bookings calendar, portfolio management, CRM)
- Multi-language (English / Amharic / Afaan Oromo), AI chatbot, PWA/offline support

Each of these needs real credentials and a couple of scoping decisions (e.g.
Supabase vs Firebase) before it can be wired in.
