# Magkano ang Puhunan? — Sariling Kape Blueprint

A single-file landing page + capital calculator that works as a top-of-funnel
**lead magnet** for a Filipino coffee-shop audience. The visitor answers three
questions, gets an honest startup-capital estimate, then opts in for a free
"Starter Kit."

- **One file**, no build step: [`Puhunan_Calculator_MVP.html`](Puhunan_Calculator_MVP.html)
- Plain HTML + CSS + vanilla JS. Only external resource is Google Fonts.
- Mobile-first, dark/editorial brand system. Copy is conversational Taglish.

---

## Run it

Double-click `Puhunan_Calculator_MVP.html` to open it in any browser. That's it —
nothing to install.

## Deploy (no build step)

1. Go to **https://app.netlify.com/drop**
2. Drag **only** `Puhunan_Calculator_MVP.html` onto the page.

Your live URL is ready in seconds.

## Go live — capture leads to a backend

By default, every opt-in is saved **on-device** (localStorage). To also send leads
to a real backend, open the file and find the `Store` module near the top of the
`<script>`:

```js
const ENDPOINT = ''; // paste your inbound webhook URL (GHL / Make / Zapier)
```

Paste your webhook URL, e.g.:

```js
const ENDPOINT = 'https://hooks.zapier.com/hooks/catch/xxxx/yyyy/';
```

Each lead is then POSTed as JSON (with `keepalive`) **and** still stored on-device.
All lead I/O lives inside that single isolated `Store` module, so swapping in a
real backend later doesn't touch the rest of the app.

**Lead payload:**

```json
{ "ts": 0, "name": "", "email": "", "viber": "", "format": "", "location": "", "equip": "", "source": "puhunan-calculator" }
```

## Private demand dashboard

Append `#leads` to the page URL (e.g. `yoursite.netlify.app/#leads`) to open the
demand panel. It is **never linked** from the page — share the `#leads` URL only
with yourself. It shows:

- Total opt-in count
- A pre-sale **gate verdict**: `0–9` = fix messaging, `10–24` = lean green light,
  `25+` = strong demand
- A reverse-chronological list of captured leads
- **Export CSV** and **Clear**

## Tuning the cost model

All figures are editable PHP constants near the top of the `<script>`
(`FORMATS`, `RENT_PER_SQM`, `CART_RENT`, `LOC_MULT`, plus `STAFF_COST`,
`AVG_TICKET`, `MARGIN`, `OPEN_DAYS`). The shipped numbers are reasonable
placeholders — replace them with your real supplier/contractor quotes.

---

_A CLMA Training & Assessment Center × Mentors Business Café initiative._
