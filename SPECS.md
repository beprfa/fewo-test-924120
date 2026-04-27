# SPECS — Sonnenhof Alpenblick

## What the site does

Marketing and booking-inquiry website for **Sonnenhof Alpenblick**, a vacation rental property in Aschau im Chiemgau, Bavaria. The site presents two holiday apartments ("Alpenpanorama" and "Bergwiese") to prospective guests and lets them send a booking request.

### Pages

| Route | Purpose |
|---|---|
| `/` | German landing page — hero, apartment cards, estate info, directions, FAQ, CTA |
| `/en` | English landing page (same structure, translated) |
| `/contact` | Booking request form with price table and terms (DE) |
| `/en/contact` | Booking request form (EN) |
| `/privacy`, `/en/privacy` | Privacy policy |
| `/terms`, `/en/terms` | Legal notice / imprint |

### Key features

- **Bilingual (DE / EN)** — separate page trees under `/` and `/en`, with dedicated navigation and layout per language.
- **Apartment listings** — each apartment card shows an image carousel, amenity icons, nightly prices, and an availability calendar.
- **Image carousel** — client-side vanilla JS with prev/next buttons, touch-swipe support, lazy preloading of adjacent images.
- **Availability calendar** — month-view grid rendered client-side; marks days as available (green), booked (red), or past (dimmed). Accepts booking data via `data-bookings` attribute. Supports Astro View Transitions re-init.
- **Booking request form** — collects name, email, phone (with country-code selector), apartment, guest count, arrival/departure dates, and a message. Client-side date validation. No backend in demo — shows a success message on submit.
- **Directions section** — embedded OpenStreetMap iframe, Google Maps "plan route" link, and transport options (car, train, airport).
- **FAQ** — accordion-style frequently asked questions.
- **Dark mode** — follows system preference; Tailwind `dark:` variants throughout.
- **SEO** — Open Graph tags, sitemap generation, configurable robots meta.
- **Static output** — the entire site is pre-rendered at build time (no SSR).

### Content model

All page content is inline in `.astro` files (no CMS). The blog subsystem inherited from AstroWind is present but disabled (`isEnabled: false`).

### Navigation

Defined in `src/navigation.ts`. Each language has its own `headerData` / `footerData` export with links pointing to anchor sections on the landing page or to subpages.
