# 🏎️ Kumar's F1 Dashboard — 2026 Season

[**Dashboard**](https://kumarsf1dashboard.vercel.app/)

> A production-grade, real-time Formula 1 dashboard built as a single-file web app. Live telemetry, standings, race calendar, team data, and paddock intel — all in one pit wall.

![Season](https://img.shields.io/badge/Season-2026-E8002D?style=flat-square&logo=data:image/svg+xml;base64,PHN2ZyB4bWxucz0iaHR0cDovL3d3dy53My5vcmcvMjAwMC9zdmciIHZpZXdCb3g9IjAgMCAyNCAyNCI+PHBhdGggZmlsbD0id2hpdGUiIGQ9Ik0xMiAyQzYuNDggMiAyIDYuNDggMiAxMnM0LjQ4IDEwIDEwIDEwIDEwLTQuNDggMTAtMTBTMTcuNTIgMiAxMiAyem0wIDE4Yy00LjQxIDAtOC0zLjU5LTgtOHMzLjU5LTggOC04IDggMy41OSA4IDgtMy41OSA4LTggOHoiLz48L3N2Zz4=)
![Data](https://img.shields.io/badge/Data-OpenF1%20%2B%20Jolpica-27F4D2?style=flat-square)
![License](https://img.shields.io/badge/License-MIT-green?style=flat-square)
![Built With](https://img.shields.io/badge/Built%20With-Vanilla%20JS-F7DF1E?style=flat-square&logo=javascript)
![Theme](https://img.shields.io/badge/Theme-Dark%20%2F%20Light-FF8000?style=flat-square)

---

## ✨ Features

### 🔴 Live Timing Tower
- Pulls real-time session data from **OpenF1.org** (free, no API key required)
- Auto-detects live sessions — activates automatically during Practice, Qualifying, and Race
- Displays: Position, Driver, Gap to leader, Interval, Last lap, Best lap, Speed, Tyre compound & age, DRS status
- Polls every **5 seconds** during live sessions
- Live race control messages (flags, safety car, penalties)
- Track conditions widget (air temp, track temp, wind, humidity, rainfall, pressure)
- Live gap intervals with animated bar chart

### 🏆 Standings
- **Driver Championship** — full 22-driver standings with team colour bars, animated points bars
- **Constructor Championship** — 11-team standings with live data from Jolpica API
- Points bars animate from 0 on load for visual impact
- Staggered row reveal for a dynamic feel

### 🗓️ Race Calendar
- Full 24-round 2026 season calendar (Bahrain & Saudi Arabia cancellations reflected)
- Visual status: ✓ completed, **NEXT** badge, cancelled overlay
- Session schedule preview (FP1, FP2, FP3, Quali, Race) with live countdown

### ⏱️ Race Countdown
- Real-time countdown to next Grand Prix (days · hours · minutes · seconds)
- Flipping digit animation
- Next session indicator within the weekend schedule

### 👥 Teams
- All 11 constructors including **new 2026 entrants** — Audi F1 and Cadillac
- Driver pairings, base location, founding year, championship position and points
- Team colour accent bars

### 🧠 Analysis Tab
- **Championship Calculator** — shows max possible points and contention status for top 5 drivers
- **Head-to-Head Comparator** — compare any two drivers across points, position, wins, and poles
- **Fastest Laps Wall** — season-best lap times per driver per circuit
- **Pole Positions** leaderboard

### 📡 Paddock Intel
- Curated team radio snippets, strategy desk updates, tyre wall info, and press room quotes

### 🔢 Live Ticker
- Scrolling top bar with dynamic WDC/WCC leader, fastest lap, round count, and next race info

---

## 🛠️ Tech Stack

| Layer | Technology |
|---|---|
| Frontend | Vanilla HTML5 / CSS3 / JavaScript (ES2020+) |
| Fonts | Orbitron · Rajdhani · Share Tech Mono (Google Fonts) |
| Live Telemetry | [OpenF1 API](https://openf1.org) — free, no key |
| Standings | [Jolpica F1 API](https://jolpi.ca) — Ergast replacement |
| Animations | CSS keyframes + Web Animations API |
| State | In-memory JS + `localStorage` for theme preference |
| Deployment | Single `.html` file — works anywhere |

---

## 🚀 Getting Started

No build step. No dependencies. No npm install.

```bash
# Clone the repo
git clone https://github.com/kumarmanik/f1-dashboard.git
cd f1-dashboard

# Open in browser
open index.html
```

Or just **drag `index.html` into any browser** and it works.

### Hosting Options

| Platform | Command / Method |
|---|---|
| GitHub Pages | Push to `main`, enable Pages in repo settings |
| Netlify | Drag & drop `index.html` into Netlify Drop |
| Vercel | `vercel --prod` from project root |
| Local server | `python3 -m http.server 3000` |

---

## 📁 Project Structure

```
f1-dashboard/
├── index.html          # Entire app — HTML + CSS + JS in one file
└── README.md           # This file
```

The entire application lives in `index.html`. This is intentional — it makes the project trivially deployable, shareable, and forkable.

---

## 🎨 Design System

### Colour Palette

| Token | Dark Mode | Light Mode | Usage |
|---|---|---|---|
| `--bg` | `#080808` | `#f4f4f4` | Page background |
| `--bg2` | `#0f0f0f` | `#ffffff` | Card background |
| `--red` | `#E8002D` | `#E8002D` | F1 accent |
| `--gold` | `#FFD700` | `#FFD700` | P1 / fastest |
| `--green` | `#00FF87` | `#00a855` | Live / safe |
| `--dim` | `#888888` | `#666666` | Muted text |

### Typography

| Font | Weight | Usage |
|---|---|---|
| **Orbitron** | 400 / 700 / 900 | Display headings, numbers, emblems |
| **Rajdhani** | 300 / 600 / 700 | Body text, driver names |
| **Share Tech Mono** | 400 | Telemetry data, timestamps, codes |

---

## ⚙️ Configuration

All seed data lives at the top of the `<script>` block in `index.html`. To customise:

### Update Driver Standings (seed data)

```javascript
let DRIVER_STANDINGS = [
  { pos:1, name:'Kimi Antonelli', team:'Mercedes', pts:72, wins:1, poles:1 },
  // ...
];
```

### Update Constructor Standings

```javascript
let CONSTRUCTOR_STANDINGS = [
  { pos:1, team:'Mercedes', color:'#27F4D2', pts:135, drivers:'RUS · ANT' },
  // ...
];
```

### Update Calendar

```javascript
const CALENDAR_2026 = [
  { round:1, name:'Australian GP', circuit:'Albert Park', date:'2026-03-15', done:true, winner:'NOR' },
  // ...
];
```

### Modify Ticker Messages

```javascript
const TICKER_STATS = [
  () => `🏆 WDC LEADER — ${DRIVER_STANDINGS[0]?.name} · ${DRIVER_STANDINGS[0]?.pts} PTS`,
  // Add your own lambda here
];
```

---

## 🔌 API Integration

### OpenF1 (Live Telemetry)

The dashboard polls [openf1.org](https://openf1.org) every 5 seconds during active sessions. No API key required.

**Endpoints used:**

| Endpoint | Data |
|---|---|
| `/sessions` | Detect live/upcoming sessions |
| `/drivers` | Driver details per session |
| `/position` | Live car positions |
| `/laps` | Lap times, best laps |
| `/car_data` | Speed, DRS, throttle, brake |
| `/stints` | Tyre compound and age |
| `/intervals` | Gaps to leader |
| `/race_control` | Flag messages, safety car |
| `/weather` | Track conditions |

When no live session is active, the telemetry panel displays the next scheduled session and retries every 2 minutes.

### Jolpica F1 API (Standings)

Standings are fetched on load from [jolpi.ca](https://jolpi.ca) — the community-maintained Ergast replacement. Falls back to seed data if the API is unavailable.

```
GET https://api.jolpi.ca/ergast/f1/2026/driverStandings/?format=json
GET https://api.jolpi.ca/ergast/f1/2026/constructorStandings/?format=json
```

---

## 🎬 Animations & Interactions

| Animation | Trigger | Description |
|---|---|---|
| **Stagger reveal** | On render | List items slide in 40ms apart |
| **Scroll reveal** | Intersection Observer | Sections fade up as they enter viewport |
| **Bar animation** | On load | Points bars grow from 0 to target width |
| **Number flash** | Data update | Values scale up briefly when changed |
| **Data flash** | Telemetry update | Timing rows pulse green on position change |
| **Skeleton loader** | While fetching | Shimmer placeholder rows in standings |
| **Theme transition** | Toggle click | Smooth CSS variable transition across all elements |
| **Ticker scroll** | Continuous | Seamless 40s loop of live stats |
| **Countdown flip** | Every second | Digit blocks update in real time |
| **Live dot blink** | Always | Green pulse on active session indicator |

---

## 📱 Responsive Breakpoints

| Breakpoint | Layout Changes |
|---|---|
| `> 900px` | Full 3-column grid, side-by-side panels |
| `≤ 900px` | Single column, scrollable tab nav, stacked countdown |
| `≤ 480px` | Compact cards, 2-column championship grid, hidden H2H VS divider |

---

## 🗺️ Roadmap

- [ ] **PWA support** — `manifest.json` + service worker for mobile install
- [ ] **Backend proxy** — FastAPI on Railway to cache OpenF1 responses and avoid CORS
- [ ] **Historical lap charts** — visualise lap-by-lap pace across a race
- [ ] **Tyre strategy visualiser** — per-driver stint timeline
- [ ] **Push notifications** — session start alerts via Web Push API
- [ ] **Driver profile pages** — click any driver to see full career stats
- [ ] **Dark/light auto-detect** — respect `prefers-color-scheme` on first visit
- [ ] **Offline mode** — serve cached standings and calendar via service worker
- [ ] **Claire integration** — voice query support via [Project Claire](https://github.com/kumarmanik/claire)

---

## 🤝 Contributing

Contributions, bug reports, and feature requests are welcome.

```bash
# Fork the repo, then:
git checkout -b feature/your-feature-name
# Make changes to index.html
git commit -m "feat: your change description"
git push origin feature/your-feature-name
# Open a Pull Request
```

Please keep the single-file architecture intact for core contributions. New features that require a build step should be discussed in an issue first.

---

## 📄 License

MIT License — see [LICENSE](LICENSE) for details.

Data provided by [OpenF1](https://openf1.org) and [Jolpica](https://jolpi.ca). This project is not affiliated with Formula 1, FOM, or any F1 team.

---

## 👨‍💻 Built By

**Kumar Manik** — AI Engineer

> *"Building in public. One lap at a time."*

[![YouTube](https://img.shields.io/badge/YouTube-Kumar%20Manik-FF0000?style=flat-square&logo=youtube)](https://youtube.com/@kumarmanik)
[![Project Claire](https://img.shields.io/badge/Project-Claire%20AI-E8002D?style=flat-square)](https://github.com/kumarmanik/claire)

---

<div align="center">
  <sub>KUMAR'S F1 DASHBOARD · 2026 SEASON · DATA: OPENF1 + JOLPICA · BUILT WITH ❤️ & SPEED</sub>
</div>
