# A One Down — Website

A complete, production-ready marketing website for the "A One Down" Android app, built with
Next.js 14 (App Router), TypeScript, and Tailwind CSS.

## Getting started

```bash
npm install
npm run dev
```

Open http://localhost:3000 in your browser.

## Build for production

```bash
npm run build
npm run start
```

The site is a standard Next.js app and deploys to Vercel, Netlify, or any Node.js host with
zero extra configuration.

## Before you launch — things to update

1. **`lib/site-config.ts`**
   - `url`: replace with your real domain (used for SEO metadata, sitemap, and Open Graph tags).
   - `apkDownloadUrl`: point this to your actual APK file (e.g. upload it to `/public/downloads/`
     and set the path, or link to your own file host).
   - `supportEmail` / `contactEmail` / `websiteDisplay`: replace with your real support inbox and
     domain if different from what's already set.

2. **APK file** — place your real `.apk` file at `public/downloads/a-one-down.apk` (create the
   folder), matching the `apkDownloadUrl` in `site-config.ts`. The Download APK buttons link
   directly to this path.

3. **Images**
   - Add a real `favicon.ico` to `/app/favicon.ico`.
   - Add a 1200×630 Open Graph image at `/public/og-image.png` for social link previews.
   - The "Screenshots" section currently uses stylized illustrated mockups (no image files
     required). Swap in real app screenshots by replacing `components/ScreenshotsSlider.tsx`
     with an `<Image>` gallery if you'd prefer real captures.

4. **Legal pages** — the Privacy Policy, Terms of Use, Disclaimer, and Cookie Policy contain
   complete, ready-to-use copy based on the details you provided. Have them reviewed by a
   qualified professional before publishing if you plan to distribute the app widely.

5. **Contact form** — `app/contact/ContactClient.tsx` currently simulates a successful submission
   on the client. Wire it up to your email service or backend (e.g. an API route, Formspree, or
   a serverless function) to actually deliver messages.

## Project structure

```
app/
  page.tsx                Home page (hero, features, screenshots, how it works, FAQ, CTA)
  privacy-policy/         Privacy Policy
  terms-of-use/           Terms of Use
  disclaimer/             Disclaimer
  cookie-policy/          Cookie Policy
  help-center/            Searchable Help Center
  contact/                Contact form + support details
  not-found.tsx           Custom animated 404 page
  sitemap.ts              Auto-generated sitemap.xml
  robots.ts               Auto-generated robots.txt
  layout.tsx              Root layout, fonts, global SEO metadata
  globals.css             Design tokens and shared utility classes
components/               Reusable UI components (Header, Footer, PhoneMockup, cards, etc.)
lib/site-config.ts        Central site configuration (edit this first)
```

## Design system

- **Palette:** near-black background, dark gray panels, blue → violet gradient accents, cyan
  used sparingly as the "active" signal color.
- **Type:** Space Grotesk (headings), Inter (body copy), JetBrains Mono (small technical labels).
- **Motion:** respects `prefers-reduced-motion`; the hero phone mockup animates through the app's
  real download flow (paste → process → choose quality → download → done).
