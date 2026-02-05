
# 🧠 Copilot Instructions — TradingView-Style Chart Analyzer

## Project Overview
You are assisting with building a **TradingView-style charting application** using **Next.js 14 (App Router)**, **TypeScript**, and **Lightweight Charts**.
The application supports **technical indicators**, **event-based chart saving**, and a **professional dark UI**.

Your goal is to generate **production-ready, type-safe, idiomatic React + TypeScript code** that follows the architecture and conventions defined below.

---

## Tech Stack & Constraints

### Framework & Core
- Next.js 14
- App Router (`/app`)
- TypeScript (strict mode)
- React Server Components by default
- Client components only when required (`"use client"`)

### UI & Styling
- Tailwind CSS with custom dark theme
- Font: Inter (Google Fonts)
- Icons: Lucide React

### Charting
- `lightweight-charts`
- Candlestick, Line, Area charts
- Multiple panes for indicators
- Overlays for SMA, EMA, Bollinger Bands

### State Management
- Zustand for global state
- LocalStorage persistence

### Utilities
- `date-fns` for all date handling

---

## Design System

### Colors
```ts
background: {
  primary: "#0f1419",
  secondary: "#1a1f2e",
  elevated: "#232831"
},
accent: {
  primary: "#2962ff",
  bullish: "#26a69a",
  bearish: "#ef5350"
},
text: {
  primary: "#e1e3e8",
  secondary: "#8b92a6",
  muted: "#5a5f73"
}
```

### UI Rules
- Subtle borders: `1px solid rgba(255,255,255,0.1)`
- Rounded corners:
  - Cards: `8px`
  - Buttons: `4px`
- Transitions: `150ms ease-in-out`
- Dark mode only

---

## File & Folder Structure

```
/app
  /page.tsx
  /library/page.tsx
  /timeline/page.tsx
  /favorites/page.tsx
  /settings/page.tsx

/components
  /chart
    ChartCanvas.tsx
    ChartToolbar.tsx
    PriceInfo.tsx
    IndicatorPanel.tsx
    SaveEventModal.tsx
    SymbolSearch.tsx
  /library
    ChartCard.tsx
    ChartLibrary.tsx

/store
  useChartStore.ts
  useLibraryStore.ts

/types
  chart.ts
  indicator.ts
  saved-event.ts

/utils
  indicators.ts
  chartState.ts
  storage.ts
```

---

## Core Types

```ts
type IndicatorConfig = {
  id: string
  type: "SMA" | "EMA" | "RSI" | "MACD" | "BB"
  settings: Record<string, number>
  visible: boolean
}

type SavedChart = {
  id: string
  eventName: string
  eventDate: string
  marketType: "Stock" | "Crypto" | "Forex" | "Commodity"
  tags: string[]
  notes?: string
  symbol: string
  timeframe: string
  chartType: "candlestick" | "line" | "area"
  indicators: IndicatorConfig[]
  chartState: unknown
  thumbnail: string
  favorite: boolean
  createdAt: string
}
```

---

## Copilot Behavior Guidelines
- Prefer small, composable components
- Avoid `any`
- Clean up chart instances on unmount
- Follow TradingView UX conventions
- Favor clarity and extensibility

---

## Non-Goals
- No authentication
- No backend or database
- No real trading or order execution
