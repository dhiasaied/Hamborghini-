# Hamborghini — Sant'Agata Gourmet Platform

Premium, dark-themed front-end for **Hamborghini**, a fictional gourmet burger atelier that blends hypercar aesthetics with Michelin-inspired culinary branding. The experience is built as a multi-page static website: HTML, Tailwind CSS (CDN), vanilla JavaScript, and an interactive Three.js burger visualizer on the home page.

There is no backend, build toolchain, or package manager in this repository. Pages run in the browser with CDN-hosted assets.

---

## Purpose

Hamborghini presents a full marketing and ordering journey for a luxury “scuderia” burger brand rooted in Sant'Agata Bolognese:

- Showcase signature “fleet” burgers with telemetry-style product storytelling
- Browse and configure items in a showroom-style menu
- Manage a client-side cart and checkout flow
- Explore brand story, pit-stop locations, and VIP membership
- Authenticate through cockpit-themed login, registration, and password recovery screens

The UI uses automotive metaphors (paddock, chassis, ignition, telemetry) consistently across navigation, copy, and interactive controls.

---

## Features

### Marketing & discovery

- **Home (`index.html`)** — Hero manifesto, live “grill pit” status indicators, interactive **Three.js** 3D burger scene (orbit / pointer control), fleet gallery with category filters (All / V12 Smash / Hot-Lap Poultry / Green Hybrid), inspect modal with bun options and quantity, and a sliding **Cockpit Bay** cart drawer
- **Menu / Showroom (`menu_showroom.html`)** — Full showroom catalog with product cards, hover imagery, and ordering CTAs
- **Our Story (`our_story.html`)** — Brand narrative, interactive timeline milestones, and live pit telemetry HUD
- **Pit Stop Locations (`pit_stop_locations.html`)** — Geo-tactical location finder with search/filter matrix, live paddock status, and expansion roadmap
- **VIP Lounge (`vip_lounge.html`)** — Membership tiers, benefits, pilot enrollment / sign-in tabs, and exclusive lounge content

### Commerce flow

- **Checkout cart (`checkout.html`)** — Fleet Staging Bay: line-item quantities, combo options, shipping estimate, promo codes (`APEX10`, `VIPSCUDERIA`), and live order summary totals
- **Streamlined checkout (`streamlined.html`)** — Multi-step paddock checkout form (pilot details, dispatch mode, payment), client-side field validation, and order submission simulation
- **Order confirmation (`order_confirmation.html`)** — Allocation confirmation, delivery telemetry, countdown helpers, and return-to-menu actions

### Account / access portal

- **Login Cockpit (`login_cockpit.html`)** — Pilot authentication UI
- **Register Scuderia (`register_scuderia.html`)** — New pilot homologation / registration
- **Forgot Password (`forgot_password.html`)** — Credential recovery request
- **Reset Password (`reset_password.html`)** — New password set flow

### Technical extras

- Shared dark design system (Material-inspired color tokens) via Tailwind `theme.extend`
- Responsive layouts for mobile, tablet, and desktop
- Google Fonts (**Syne**, **Space Grotesk**) and **Material Symbols Outlined**
- Hover transitions and soft motion on cards, buttons, and images
- Standalone Three.js demo at `three.js/code.html`

> **Note:** Forms and cart logic are front-end demonstrations. They do not persist to a server; submission handlers prevent default and run in-page JavaScript.

---

## Tech stack

| Layer | Technology |
| --- | --- |
| Markup | HTML5 |
| Styling | [Tailwind CSS](https://tailwindcss.com/) via CDN (`cdn.tailwindcss.com`) |
| Scripting | Vanilla JavaScript (inline per page) |
| 3D | [Three.js](https://threejs.org/) r125 (`ajax.googleapis.com/ajax/libs/threejs/r125/three.min.js`) |
| Typography | Google Fonts — Syne (headlines), Space Grotesk (body / labels) |
| Icons | Material Symbols Outlined |
| Imagery | Hosted remote assets (Googleusercontent / AIDA public URLs) |

**Runtime requirements**

- A modern browser with WebGL (for the Three.js scenes)
- Network access to load Tailwind, fonts, Three.js, and remote images

---

## Project structure

```text
shamborghini_plataforme/
├── index.html                 # Home + 3D visualizer + cart drawer
├── menu_showroom.html         # Menu / showroom catalog
├── our_story.html             # Brand story & timeline
├── pit_stop_locations.html    # Locations finder
├── vip_lounge.html            # VIP membership & enrollment
├── checkout.html              # Cart / staging bay
├── streamlined.html           # Detailed checkout form
├── order_confirmation.html    # Post-order confirmation
├── login_cockpit.html         # Sign-in
├── register_scuderia.html     # Registration
├── forgot_password.html       # Password recovery request
├── reset_password.html        # Password reset
├── three.js/
│   └── code.html              # Standalone 3D burger scene
└── README.md
```

Each marketing page shares a fixed header (brand, primary nav, search, Cockpit Bay, Configure & Order) and a multi-column footer. Auth pages use a lighter portal chrome with return-to-showroom affordances.

---

## Installation

No npm/pip install or compile step is required.

### 1. Get the project

Clone or copy the project folder to your machine:

```bash
git clone <repository-url> shamborghini_plataforme
cd shamborghini_plataforme
```

### 2. Open the site

**Option A — Direct file open**

Open `index.html` in a browser (double-click or File → Open).  
Some browsers restrict certain features when using the `file://` protocol; prefer Option B for a closer-to-production experience.

**Option B — Local static server (recommended)**

Using Node.js (if installed):

```bash
npx --yes serve .
```

Using PHP:

```bash
php -S localhost:8000
```

Using VS Code / Cursor: install a “Live Server” extension and serve the project root.

Then visit the printed local URL (for example `http://localhost:3000` or `http://localhost:8000`) and open `index.html`.

---

## Configuration

There is no `.env` or central config file. Behavior is controlled inside each HTML document:

| Concern | Where it lives | What you can change |
| --- | --- | --- |
| Design tokens (colors, type, spacing, radii) | `tailwind.config` script in each page `<head>` | Brand colors (`primary-container` `#ff5708`, `secondary` `#ffb95f`, surfaces, etc.) |
| Dark mode | `<html class="dark">` + `darkMode: "class"` | Keep or remove the `dark` class |
| Fonts & icons | Google Fonts / Material Symbols `<link>` tags | Swap families or icon sets |
| Three.js scene | Inline script in `index.html` (and `three.js/code.html`) | Camera, lights, materials, animation |
| Promo codes | `checkout.html` (`validatePromo`) | Codes such as `APEX10` (10%) and `VIPSCUDERIA` (20%) |
| Cart / checkout UX | Inline JS on `index.html`, `checkout.html`, `streamlined.html` | Prices, shipping, validation rules |

CDN endpoints used by the project:

- `https://cdn.tailwindcss.com`
- `https://fonts.googleapis.com` / `https://fonts.gstatic.com`
- `https://ajax.googleapis.com/ajax/libs/threejs/r125/three.min.js`

Offline use requires downloading these assets and updating the script/link URLs accordingly.

---

## Usage

### Suggested user journey

1. Start on **`index.html`** — explore the 3D burger, filter the fleet, inspect a platter, and add items via the Cockpit Bay drawer.
2. Open **`menu_showroom.html`** for the full catalog.
3. Review **`checkout.html`** for cart quantities and promo application, then continue through **`streamlined.html`** for delivery and payment details.
4. Land on **`order_confirmation.html`** after a simulated ignition / submit.
5. Visit **`our_story.html`**, **`pit_stop_locations.html`**, and **`vip_lounge.html`** for brand, map, and membership content.
6. Use **`login_cockpit.html`** / **`register_scuderia.html`** (and the forgot/reset pages) for the access-portal experience.

### Page reference

| File | Role |
| --- | --- |
| `index.html` | Home / showroom landing |
| `menu_showroom.html` | Menu catalog |
| `our_story.html` | Brand story |
| `pit_stop_locations.html` | Locations |
| `vip_lounge.html` | VIP membership |
| `checkout.html` | Cart staging |
| `streamlined.html` | Checkout form |
| `order_confirmation.html` | Order success |
| `login_cockpit.html` | Login |
| `register_scuderia.html` | Register |
| `forgot_password.html` | Forgot password |
| `reset_password.html` | Reset password |
| `three.js/code.html` | Isolated 3D demo |

### Interactive highlights

- **Fleet filters** on the home page toggle product categories without a page reload.
- **Inspect modal** lets users choose bun style and quantity before adding to cart.
- **Cart drawer** updates item counts, subtotals, and dispatch mode in the browser.
- **Checkout promos** recalculate discounts and shipping in real time on `checkout.html`.
- **Streamlined checkout** validates email/required fields client-side before the simulated submit.
- **VIP Lounge** switches between enrollment and pilot sign-in panels and scrolls to tier selection.

### Design notes

- Primary accent: orange (`#ff5708`) with amber secondary highlights
- Background: near-black surfaces (`#131315` and related containers)
- Headlines: Syne; UI copy and labels: Space Grotesk
- Dense “telemetry” micro-copy and status pills reinforce the racing / paddock theme

---

## Browser support

Tested conceptually against current Chromium, Firefox, and Safari releases. WebGL is required for Three.js scenes. If WebGL is unavailable, the rest of the static UI remains usable; only the 3D viewport will fail to render.

---

## Limitations

- No server-side API, database, authentication, or payment processing
- Navigation `data-path` attributes describe routes; some header/footer links may still use `#` placeholders depending on how pages were exported — open target HTML files directly when needed
- Cart state is page-local (not shared across files via storage unless you extend the scripts)
- Remote images and CDNs require internet connectivity
