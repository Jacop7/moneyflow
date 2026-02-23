# CLAUDE.md - MoneyMoveLab (머니무브랩)

## Project Overview

**머니무브랩 (MoneyMoveLab)** is a Korean-language sector fund flow analysis platform. It tracks and displays sector trends, signal detection, and financial articles related to stock market movements across various technology and industry sectors.

## Tech Stack

- **Frontend**: Vanilla HTML/CSS/JavaScript (single-page, no build tools or frameworks)
- **Styling**: CSS custom properties (variables), responsive design with media queries
- **Fonts**: Google Fonts - Noto Sans KR
- **No backend**: Currently a static frontend with hardcoded data

## Repository Structure

```
moneyflow/
├── CLAUDE.md          # This file - project documentation for AI assistants
├── README.md          # Project readme
└── index.html         # Main page - single-file SPA with embedded CSS and JS
```

## Architecture

### Single-File Architecture
The entire application lives in `index.html` as a self-contained single-page application:
- **`<style>`** block: All CSS (~350 lines), including responsive breakpoints
- **`<body>`** markup: Semantic HTML structure with header, sidebar nav, content area, footer
- **`<script>`** block: All JavaScript (~120 lines), including data and rendering logic

### Key UI Sections
1. **Header** (`<header>`): Logo, navigation (머니무브, 이슈체크, 섹터 랭킹), login button, mobile menu
2. **Left Navigation** (`.left-nav`): Sticky sidebar with section filters (전체보기, 섹터 트렌드, 시그널 감지)
3. **Period Tabs** (`.period-tabs`): Time range filter (오늘, 1주, 1개월, 3개월)
4. **Sector Trend Card** (`#section-sector-trend`): Ranked sector trends with news headlines and related companies, paginated 3 per page
5. **Signal Detection Card** (`#section-signal`): Emerging sectors with reasoning and related companies, paginated 3 per page
6. **Quote Banner** (`.banner`): Rotating investment quotes with background images (30s interval)
7. **Article List** (`.article-list`): Curated article cards with tags, titles, descriptions, and author metadata
8. **Footer**: Site links and branding

### Data Architecture
All data is currently hardcoded in JavaScript objects:
- **`hotData`**: Sector trend data organized by period (`today`, `week`, `month`, `3month`), each containing 9 sectors with `sector`, `news`, and `companies` fields
- **`nextData`**: Signal detection data (6 items) with `sector`, `reason`, and `companies` fields
- **`quotes`**: Array of 10 investment quotes with `text`, `author`, and `img` (Unsplash URLs)

### JavaScript State
- `currentPeriod`: Active time period filter (default: `'today'`)
- `hotPage` / `nextPage`: Current pagination index for each section
- `PAGE_SIZE`: Items per page (constant: `3`)
- `currentQuote`: Index of currently displayed quote

### Key Rendering Functions
- `renderHotPage()`: Renders sector trend items for current page/period
- `renderNextPage()`: Renders signal detection items for current page
- `renderAll()`: Renders both sections
- `activateSection(section)`: Handles section navigation (scroll-to-section)
- `applyQuote()` / `rotateQuote()`: Quote banner cycling with fade animation

## CSS Design System

### CSS Variables (`:root`)
| Variable | Value | Usage |
|----------|-------|-------|
| `--accent` | `#4f46e5` | Primary brand color (indigo) |
| `--accent-light` | `#eef2ff` | Light accent backgrounds |
| `--accent-hover` | `#4338ca` | Hover state for accent |
| `--text-primary` | `#1a1a2e` | Main text color |
| `--text-secondary` | `#5a5a72` | Secondary text |
| `--text-tertiary` | `#8e8ea0` | Muted text |
| `--border` | `#e8e8ee` | Border color |
| `--radius` | `14px` | Card border radius |
| `--radius-sm` | `8px` | Small element radius |

### Responsive Breakpoints
- **> 900px**: Desktop - sidebar visible, two-column grid layout
- **<= 900px**: Tablet - sidebar hidden, horizontal scrollable mobile sub-menu appears
- **<= 600px**: Mobile - stacked card layout, login button hidden, hamburger menu visible

### Animations
- `fadeUp`: Article card entrance animation with staggered delays
- `flowSlide`: Sector/signal item entrance animation
- `spin`: Refresh button rotation animation

## Language

- All UI text is in **Korean** (한국어)
- The platform targets Korean stock market investors
- Sector names, company names, and news headlines are all in Korean
- Keep all user-facing strings in Korean when making changes

## Development Notes

### No Build System
This project has no package manager, bundler, or build step. Open `index.html` directly in a browser to develop.

### No External Dependencies (runtime)
The only external resource is Google Fonts (Noto Sans KR). All logic is self-contained.

### Future Considerations
- The hardcoded data in `hotData`, `nextData`, and `quotes` should eventually be fetched from an API
- Navigation links (`이슈체크`, `섹터 랭킹`) currently point to `#` (not yet implemented)
- Article cards link to `#` (no article detail pages yet)
- Login functionality is not implemented
- The sort dropdown (`최신순`, `조회수 높은순`) has no functional behavior yet

## Conventions for AI Assistants

- **Language**: Keep all user-facing text in Korean. Code comments and documentation can be in English.
- **Styling**: Use the existing CSS custom properties. Do not introduce a CSS framework.
- **No frameworks**: This is intentionally vanilla HTML/CSS/JS. Do not introduce React, Vue, or other frameworks unless explicitly requested.
- **Single-file**: Currently everything is in `index.html`. If the project grows, extract CSS to a separate file first, then JS.
- **Data format**: Follow the existing object structure (`{ sector, news, companies }` for trends, `{ sector, reason, companies }` for signals).
- **Responsive**: All changes must work across desktop (>900px), tablet (<=900px), and mobile (<=600px).
- **Color scheme**: Light-only. The `color-scheme: light` meta tag is set explicitly.
