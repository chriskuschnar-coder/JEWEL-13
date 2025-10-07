# Research Tab Component Files

Here are the main files that create the Research tab's appearance:

## 1. Main Research Tab Component
**File: `src/components/research/ResearchTab.tsx`**
- Main container component that orchestrates all research sections
- Handles the gradient background with floating orbs
- Manages state for research data and modals
- Coordinates between different research sections

## 2. Research Hero Section
**File: `src/components/research/ResearchHero.tsx`**
- Top section with market sentiment analysis
- Large featured card with AI sentiment data
- Animated background elements and parallax effects

## 3. Key Drivers Section
**File: `src/components/research/KeyDrivers.tsx`**
- Grid of market driver cards using the dedicated `MarketDriverCard`
- Each card exposes confidence, timeframe, category, and impact treatments aligned with the dark research theme
- Tooltips with detailed information and consistent typography
- Parallax background animations and responsive layout updates

### Market Driver Card Component
**File: `src/components/research/MarketDriverCard.tsx`**
- Purpose-built card for key market drivers with gradient accents and CTA affordances
- Handles mobile navigation into the driver detail route while desktop keeps modal behaviour
- Encapsulates impact styling tokens and consistent metric presentation
- Provides hover/focus states that match the research visual language

## 4. Asset Signals Section
**File: `src/components/research/AssetSignals.tsx`**
- Grid of asset trading signals (BTC, ETH, stocks, etc.)
- Category filtering (crypto, stocks, forex, commodities)
- Real-time price data and sparkline charts
- Buy/sell/watch signal indicators

## 5. Macro Insights Section
**File: `src/components/research/MacroInsights.tsx`**
- Large cards with global economic insights
- Federal Reserve policy analysis
- China economic stimulus information
- Detailed market implications

## 6. Reusable Research Card Component
**File: `src/components/research/ResearchCard.tsx`**
- Base card component used throughout research sections
- Glassmorphism effects and hover animations
- Sparkline chart integration
- Confidence indicators and timeframes

## 7. Research Section Wrapper
**File: `src/components/research/ResearchSection.tsx`**
- Wrapper component for consistent section styling
- Section headers with icons and refresh buttons
- Staggered animation entrance effects
- Update counters and loading states

## 8. Research Detail Modal
**File: `src/components/research/ResearchDetailModal.tsx`**
- Modal that opens when clicking on research cards
- Tabbed interface for detailed analysis
- Technical, fundamental, and strategy tabs
- Historical data and actionable insights

## 9. Market Driver Dedicated Pages
**Files:**
- `src/components/mobile/pages/MobileDriverDetailPage.tsx`
- `src/components/pages/DriverDetailPage.tsx`

- Mobile and desktop-optimised pages that mirror the core GMC navigation shell
- Share the same data generator as the research cards for consistency
- Include CTA surfaces to launch the institutional terminal and smart alerts
- Reinforce macro analysis with contextual sections, historical trends, and actionable insights

## 10. Research Data Hook
**File: `src/hooks/useResearchData.ts`**
- Custom hook that provides research data to components
- Handles data fetching and refresh logic
- Auto-refresh every 2 minutes for live updates

## 11. Research Data Service
**File: `src/lib/researchData.ts`**
- Data generation service for research content
- Creates realistic market sentiment data
- Generates key market drivers and asset signals
- Provides macro economic insights

## Key Styling Features:

### Glassmorphism Cards
- `bg-white/5 backdrop-blur-xl border-white/10`
- Semi-transparent backgrounds with blur effects
- Subtle borders and shadows

### Gradient Backgrounds
- `bg-gradient-to-br from-slate-900 via-gray-900 to-black`
- Animated floating orbs with color gradients
- Parallax scrolling effects

### Hover Animations
- Scale transforms on hover (`hover:scale-1.02`)
- Glow effects with box-shadow
- Smooth transitions with `transition-all duration-300`

### Color System
- Blue theme: `text-blue-400`, `bg-blue-500/20`
- Success: `text-emerald-400`, `bg-emerald-500/20`
- Warning: `text-amber-400`, `bg-amber-500/20`
- Error: `text-red-400`, `bg-red-500/20`

### Typography
- Headers: `text-2xl font-bold text-white tracking-tight`
- Subtitles: `text-white/70 text-lg`
- Body text: `text-white/80 leading-relaxed`

### Responsive Design
- Grid layouts: `grid md:grid-cols-2 lg:grid-cols-3`
- Mobile-first approach with breakpoint modifiers
- Touch-friendly button sizes on mobile

The Research tab uses Framer Motion for animations, Recharts for sparklines, and a custom design system with Tailwind CSS for consistent styling across all components.