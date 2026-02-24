# UMassive

> Unofficial UMass Amherst dining companion — browse live menus, filter by allergens/diets, save favorites, and get notified when preferred dishes appear.

**Live site:** [umassive.space](https://umassive.space) &nbsp;·&nbsp; Used by 100+ students &nbsp;·&nbsp; Not affiliated with UMass Dining Services

---

## Features

- **Live menus** across all dining halls (Worcester, Franklin, and more)
- **Smart filtering** by allergens and dietary preferences (Vegetarian, Halal, etc.)
- **Saved favorites** with push notifications when preferred dishes are available
- **Meal logging** and social like counts
- **Google Sign-in** with `@umass.edu` account sync

---

## Tech Stack

### Frontend
| | |
|---|---|
| Web | React 19 + TypeScript + Tailwind CSS |
| Mobile | Expo / React Native |

### Backend
| | |
|---|---|
| Runtime | Node.js + Express |
| Scraping | Cheerio |
| Storage | better-sqlite3 + Firebase |
| Telemetry | Google BigQuery |

---

## Architecture Highlights

**3-tier cache** (memory → SQLite → API) with in-flight request deduplication and TTL-based invalidation — reduced upstream API calls by ~80%.

**Telemetry pipeline** processes millions of events with <5ms overhead via BigQuery.

**Reverse-engineered** undocumented UMass dining APIs and built a throttling layer to handle brittle upstream systems reliably.

---

## Project Structure

```
backend/          # API server, scraping, caching, push notifications
umassdining/      # React web app
native-mobile/    # Expo React Native app
```

---

## Getting Started

### Prerequisites
- Node.js 18+
- Firebase project credentials
- Google BigQuery credentials (for telemetry)

### Backend
```bash
cd backend
npm install
npm start
```

### Web
```bash
cd umassdining
npm install
npm run dev
```

### Mobile
```bash
cd native-mobile
npm install
npx expo start
```

---

## Why This Project?

UMass dining menus are hard to navigate — especially for students with dietary restrictions. UMassive was built to solve that problem with a fast, reliable interface backed by careful reverse-engineering and performance engineering.

---

*Built in March 2026. Not affiliated with UMass Dining Services.*
