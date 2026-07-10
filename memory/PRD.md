# Weather Dashboard — PRD

## Original Problem Statement
> "I have been given a task to make the homepage and search UI of a weather Dashboard that shows the weather of any city. Users should be able to search for a city and view the current weather and forecast using a free Weather API. Features: search city, current weather, 5-day forecast, weather icons, recent searches."

## Scope (as clarified by user)
- Focus: Homepage + Search UI only
- Delivered as a **static HTML / CSS / JS** project (no React, no backend)

## Architecture
- `/app/frontend/index.html` — markup (Tailwind CDN, Google Fonts, Lucide icons)
- `/app/frontend/style.css` — brutalist meteorological theme, grain overlay, animations
- `/app/frontend/script.js` — search, geocoding, weather fetch, recent searches (localStorage)
- Served on port 3000 via `serve` package (supervisor `yarn start`)

## Design System (from `design_guidelines.json`)
- Theme: Meteorological Brutalism / High-Contrast Swiss (dark)
- Palette: `#050505` ink · `#121212` surface · `#CCFF00` volt accent
- Typography: **Outfit** (headings/UI) + **JetBrains Mono** (data/labels)
- Layout: bento grid, sharp edges (no border-radius), left-aligned data
- Icons: Lucide via CDN

## Integrations
- **Open-Meteo Geocoding API** — city search (no API key)
- **Open-Meteo Forecast API** — current + 5-day daily forecast (no API key)

## Implemented Features (2026-01-10)
- [x] Prominent city search bar with keyboard (Arrow/Enter/Escape) + mouse autocomplete
- [x] Debounced live suggestions (min 2 chars) showing city, region, country, code
- [x] Current weather panel: city, coords, local time, temp, condition, feels-like, ambient icon
- [x] Detail widgets: humidity, wind (km/h or mph), pressure (hPa), UV index
- [x] 5-day forecast cards with weather icons + hi/lo temperatures
- [x] Weather icons dynamically mapped from WMO codes (sun, cloud, rain, drizzle, snow, thunder, fog)
- [x] Recent searches (localStorage, max 6) rendered as clickable chips with remove `×`
- [x] Empty state with atmospheric dark cloud background
- [x] Live clock + date in header
- [x] Loading + error states
- [x] Fully responsive (mobile → desktop)
- [x] `data-testid` attributes on all interactive/critical elements
- [x] **°C ↔ °F unit toggle** (also switches wind km/h ↔ mph), persisted in localStorage
- [x] **Hourly (next 24h) strip** — scrollable, with "Now" highlight + precipitation %
- [x] **"Use my location" button** — browser Geolocation + reverse geocoding
- [x] **Favorites** — separate storage, gold star chip, save/unsave from active city
- [x] **Shareable URL** — `?city=&lat=&lon=&cc=` auto-loads city on visit, one-click copy link

## User Personas
- **Casual user** — needs to quickly check weather of any city (search + read + go)
- **Frequent user** — checks the same handful of cities daily (recent chips)

## Backlog / Nice-to-haves (P2/P3)
- P2: Sunrise/sunset visualization (dawn/dusk arc)
- P2: Air quality index (Open-Meteo AQI endpoint)
- P2: Precipitation/wind mini-charts on the current card
- P2: Compare-mode (side-by-side two cities)
- P3: Weather alerts / severe warnings banner
- P3: PWA / installable + offline last-search caching
- P3: Language switcher (Open-Meteo geocoding `language=` param)

## Next Action Items
- Await user feedback / next feature request
