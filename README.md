# MetroMate — Namma Metro Route Planner, Bengaluru

**Live:** https://abhiramunni.github.io/metromate/

Plan any journey on Bengaluru's Namma Metro in seconds — stops, interchanges, fare and travel time — across all three live lines. Single self-contained HTML file, no backend, no signup, everything saved on your device only.

## What it does

- **Journey planner** — type any two of the 83 stations (with autocomplete) and get a ticket-style result: token fare, smart-card/QR fare, off-peak fare, travel time, distance, and a stop-by-stop timeline with interchange markers.
- **Smart routing** — Dijkstra search over the real network graph, minimising stops with a penalty for line changes, so it picks the sensible route (e.g. BTM Layout → MG Road via RV Road and Majestic, 13 stops, 2 changes, ₹60).
- **Network explorer** — all 83 stations on three line cards (Purple 37, Green 32, Yellow 16). Tap a station to see what's nearby, then tap another to build a journey. Dashed rings mark the two live interchanges: Majestic (Purple ↔ Green) and RV Road (Green ↔ Yellow).
- **Fares & timings** — the full BMRCL distance-slab fare chart (₹10–₹90), smart-card 5% discount, off-peak extra 5% (10% total), and first/last trains per line.
- **Live service status** — a real IST clock in the status strip that says whether trains are running now, with peak-hour frequency.
- **Saved & recent routes** — save up to 5 daily commutes, one tap to plan them again. Kept in `localStorage` only.
- **Coming soon** — Pink Line first stretch (Kalena Agrahara–Tavarekere, opening 13 Nov 2026 per reports) and the Blue Line to Kempegowda International Airport.
- **Guided first run** — cinematic golden-hour intro (tap to skip; quick version on return visits) and a 3-step onboarding coach.

## Data & accuracy

- Station lists, line lengths (Purple 42.17 km, Green 33.46 km, Yellow 18.82 km) and interchange points from BMRCL-published information and public reports, checked November 2026.
- Fares are estimates from BMRCL distance slabs (Feb 2025): 0–2 km ₹10, 2–4 ₹20, 4–6 ₹30, 6–8 ₹40, 8–10 ₹50, 10–15 ₹60, 15–20 ₹70, 20–25 ₹80, 25+ ₹90. Smart card / QR: 5% off. The fare at the station is final.
- Travel time is an estimate: about 2 minutes per stop plus 4 minutes per interchange.
- First trains 5:00 AM (Yellow 6:30 AM), last trains 11:00 PM (Yellow 11:15 PM); Sundays from 7:00 AM. Verify on the BMRCL app or station display before travelling late or early.
- MetroMate is an independent, unofficial guide and is not affiliated with BMRCL.

## Tech

- One file (`index.html`, ~750 KB including two embedded AI-generated photos) — HTML + CSS + vanilla JS, no build step.
- Fonts: Fraunces + Inter (Google Fonts CDN). No other external requests.
- State in `localStorage` under `metromate.v1.*` (saved routes, recents, visited, onboarding).
- QA: `qa-test.js` — 54 headless jsdom assertions (routing math for 6 known journeys, edge cases, autocomplete, save/plan-again, network explorer, intro & coach, zero uncaught errors) — all passing, plus `node --check`.

## Run locally

Open `index.html` in any browser, or serve the folder (`python3 -m http.server`) — no build step needed.
