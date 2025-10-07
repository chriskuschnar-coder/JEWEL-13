# Mobile-First UI Optimization Guide

## Overview
This document provides comprehensive guidelines for optimizing all components to match Fortune 500 mobile app standards (Coinbase, Robinhood, Crypto.com).

## Core Principles

### 1. Mobile-First Spacing System
```css
/* Use 8px grid system with mobile-first breakpoints */
- Mobile (< 768px): 8px, 12px, 16px, 24px
- Tablet (768-1200px): 12px, 16px, 24px, 32px
- Desktop (> 1200px): 16px, 24px, 32px, 48px
```

### 2. Typography Scale
```css
/* Mobile-first responsive typography */
- Headings: text-2xl sm:text-3xl md:text-4xl lg:text-5xl
- Subheadings: text-lg sm:text-xl md:text-2xl
- Body: text-sm sm:text-base
- Small: text-xs sm:text-sm
- Tiny: text-[11px] sm:text-xs
```

### 3. Component Sizing
```css
/* Buttons - Mobile optimized */
- Default: h-9 px-3 py-2 text-xs sm:h-10 sm:px-4 sm:text-sm
- Small: h-8 px-2.5 py-1.5 text-xs
- Large: h-10 px-4 text-sm sm:h-11 sm:px-6 sm:text-base
- Icon: h-9 w-9 sm:h-10 sm:w-10

/* Cards - Tighter mobile padding */
- Padding: p-3 sm:p-4 md:p-5 lg:p-6
- Border radius: rounded-xl sm:rounded-2xl
- Shadow: shadow-sm hover:shadow-md
```

### 4. Touch Targets
```css
/* Minimum 44px touch targets (Apple/Google guidelines) */
- Interactive elements: min-height: 44px (11 * 4px = 44px in Tailwind units)
- Add touch-manipulation class for better mobile feel
- Use active:scale-[0.97] for tactile feedback
```

## Component-Specific Optimizations

### ManagedAllocationOnboarding.tsx

#### Welcome Step
```tsx
<motion.div className="max-w-4xl mx-auto space-y-4 sm:space-y-6 md:space-y-8 px-3 sm:px-4 md:px-6 lg:px-0">
  {/* Hero Icon - Smaller on mobile */}
  <div className="rounded-full bg-gradient-to-br from-blue-500 via-purple-500 to-cyan-500 p-4 sm:p-6 md:p-8">
    <Brain className="h-12 w-12 sm:h-16 sm:w-16 md:h-20 md:w-20 lg:h-24 lg:w-24 text-white" />
  </div>

  {/* Title - Responsive scaling */}
  <h1 className="text-2xl sm:text-3xl md:text-4xl lg:text-5xl xl:text-6xl font-bold text-white mb-2 sm:mb-3 md:mb-4">
    Welcome to Guardian AI
  </h1>

  {/* Subtitle - Smaller baseline */}
  <p className="text-sm sm:text-base md:text-lg text-slate-300">
    Your intelligent portfolio guardian
  </p>

  {/* Feature Cards - Compact mobile layout */}
  <div className="grid grid-cols-1 md:grid-cols-3 gap-3 sm:gap-4 md:gap-6">
    <div className="rounded-xl sm:rounded-2xl border border-slate-700 bg-slate-800/50 p-3 sm:p-4 md:p-5">
      <div className="rounded-lg sm:rounded-xl bg-gradient-to-br from-emerald-500 to-teal-500 p-2.5 sm:p-3 w-fit mb-2 sm:mb-3 md:mb-4">
        <Shield className="h-5 w-5 sm:h-6 sm:w-6 md:h-7 md:w-7 lg:h-8 lg:w-8 text-white" />
      </div>
      <h3 className="text-sm sm:text-base md:text-lg font-bold text-white mb-1.5 sm:mb-2">Bank-Grade Security</h3>
      <p className="text-[11px] sm:text-xs md:text-sm text-slate-400">Multi-layer protection</p>
    </div>
  </div>

  {/* CTA Button - Full width on mobile */}
  <button className="w-full px-5 sm:px-6 md:px-8 py-2.5 sm:py-3 md:py-4 rounded-xl sm:rounded-2xl bg-gradient-to-r from-blue-600 to-purple-600 text-white font-semibold text-sm sm:text-base md:text-lg shadow-lg sm:shadow-xl">
    Begin Your Journey
    <ArrowRight className="inline-block ml-2 h-4 w-4 sm:h-5 sm:w-5" />
  </button>
</motion.div>
```

#### Risk Assessment Cards
```tsx
<div className="grid grid-cols-1 md:grid-cols-2 gap-3 sm:gap-4 md:gap-6">
  <button className="rounded-xl sm:rounded-2xl md:rounded-3xl border-2 p-4 sm:p-5 md:p-6 lg:p-8 text-left">
    {/* Icon with gradient */}
    <div className="rounded-xl sm:rounded-2xl bg-gradient-to-br from-emerald-500 to-teal-600 p-2.5 sm:p-3 md:p-4 w-fit mb-3 sm:mb-4 md:mb-6">
      <Shield className="h-6 w-6 sm:h-7 sm:w-7 md:h-8 md:w-8 lg:h-9 lg:w-9 text-white" />
    </div>

    {/* Title */}
    <h3 className="text-lg sm:text-xl md:text-2xl font-bold text-white mb-1.5 sm:mb-2">The Fortress Builder</h3>

    {/* Description */}
    <p className="text-xs sm:text-sm md:text-base text-slate-300 mb-3 sm:mb-4 md:mb-6">
      Your portfolio is a castle. Every brick matters.
    </p>

    {/* Stats - Compact mobile */}
    <div className="space-y-2 sm:space-y-2.5 md:space-y-3">
      <div className="flex items-center justify-between text-[11px] sm:text-xs md:text-sm">
        <span className="text-slate-400">Expected Risk:</span>
        <span className="font-semibold text-white">5-10% volatility</span>
      </div>
    </div>
  </button>
</div>
```

### AutomatedStrategiesLanding.tsx

```tsx
<div className="max-w-7xl mx-auto px-3 sm:px-4 md:px-6 py-8 sm:py-12 md:py-16 lg:py-20">
  {/* Back Button - Compact mobile */}
  <button className="flex items-center gap-2 text-xs sm:text-sm text-blue-200 hover:text-white mb-4 sm:mb-6 md:mb-8">
    <ArrowLeft className="h-4 w-4 sm:h-5 sm:w-5" />
    <span className="font-medium">Back to Portfolio</span>
  </button>

  {/* Hero Icon - Smaller mobile */}
  <div className="rounded-2xl sm:rounded-3xl bg-gradient-to-br from-blue-500 to-cyan-500 p-4 sm:p-5 md:p-6 mb-4 sm:mb-6 md:mb-8">
    <Bot className="h-12 w-12 sm:h-16 sm:w-16 md:h-20 md:w-20 text-white" />
  </div>

  {/* Title - Progressive scaling */}
  <h1 className="text-2xl sm:text-3xl md:text-4xl lg:text-5xl xl:text-6xl font-bold text-white mb-3 sm:mb-4 md:mb-6">
    Automated Trading Strategies
  </h1>

  {/* Stats Grid - 2 cols mobile, 4 desktop */}
  <div className="grid grid-cols-2 md:grid-cols-4 gap-2.5 sm:gap-3 md:gap-4 lg:gap-6">
    <div className="rounded-lg sm:rounded-xl border border-white/20 bg-white/10 p-2.5 sm:p-3 md:p-4">
      <div className="text-lg sm:text-xl md:text-2xl font-bold text-white mb-1">12</div>
      <div className="text-[10px] sm:text-[11px] md:text-sm text-blue-200">Active Algorithms</div>
    </div>
  </div>

  {/* Choice Cards - Stack on mobile */}
  <div className="grid grid-cols-1 md:grid-cols-2 gap-4 sm:gap-5 md:gap-6 lg:gap-8">
    <div className="rounded-2xl sm:rounded-3xl border-2 p-4 sm:p-5 md:p-6 lg:p-8">
      {/* Icon */}
      <div className="rounded-xl sm:rounded-2xl bg-gradient-to-br from-blue-500 to-cyan-500 p-2.5 sm:p-3 md:p-4 w-fit mb-4 sm:mb-5 md:mb-6">
        <BarChart3 className="h-6 w-6 sm:h-8 sm:w-8 md:h-10 md:w-10 text-white" />
      </div>

      {/* Title */}
      <h2 className="text-xl sm:text-2xl md:text-3xl font-bold text-slate-900 mb-2 sm:mb-3">
        Self-Managed Portfolio
      </h2>

      {/* Description */}
      <p className="text-xs sm:text-sm md:text-base text-slate-600 mb-4 sm:mb-5 md:mb-6">
        Choose your own algorithms and manage your automated trading
      </p>

      {/* Features - Tighter spacing mobile */}
      <div className="space-y-2 sm:space-y-2.5 md:space-y-3 mb-5 sm:mb-6 md:mb-8">
        <div className="flex items-start gap-2 sm:gap-3">
          <CheckCircle className="h-4 w-4 sm:h-5 sm:w-5 text-emerald-600 mt-0.5 flex-shrink-0" />
          <span className="text-[11px] sm:text-xs md:text-sm text-slate-700">
            Browse 12+ trading algorithms
          </span>
        </div>
      </div>

      {/* CTA - Full width mobile */}
      <button className="w-full rounded-lg sm:rounded-xl px-5 sm:px-6 md:px-8 py-2.5 sm:py-3 md:py-4 bg-gradient-to-r from-blue-600 to-cyan-600 text-white font-semibold text-sm sm:text-base">
        Get Started
        <ArrowRight className="inline-block ml-2 h-4 w-4 sm:h-5 sm:w-5" />
      </button>
    </div>
  </div>
</div>
```

### AlgorithmMarketplace.tsx

```tsx
<div className="min-h-screen bg-gradient-to-br from-slate-50 via-white to-slate-50">
  {/* Header - Compact mobile */}
  <div className="border-b border-slate-200 bg-white">
    <div className="max-w-7xl mx-auto px-3 sm:px-4 md:px-6 py-6 sm:py-8 md:py-10 lg:py-12">
      {/* Back Button */}
      <button className="flex items-center gap-2 text-xs sm:text-sm text-slate-600 mb-4 sm:mb-5 md:mb-6">
        <ArrowLeft className="h-4 w-4 sm:h-5 sm:w-5" />
        <span className="font-medium">Back to Portfolio</span>
      </button>

      {/* Hero Icon */}
      <div className="rounded-xl sm:rounded-2xl bg-gradient-to-br from-blue-500 to-cyan-500 p-3 sm:p-4 mb-3 sm:mb-4">
        <Bot className="h-10 w-10 sm:h-12 sm:w-12 text-white" />
      </div>

      {/* Title */}
      <h1 className="text-2xl sm:text-3xl md:text-4xl font-bold text-slate-900 mb-3 sm:mb-4">
        Algorithm Marketplace
      </h1>

      {/* Description */}
      <p className="text-sm sm:text-base md:text-lg text-slate-600 mb-5 sm:mb-6 md:mb-8">
        Choose from our curated selection of trading algorithms
      </p>

      {/* Stats - 2x2 grid on mobile */}
      <div className="grid grid-cols-2 sm:grid-cols-4 gap-2.5 sm:gap-3 md:gap-4 mb-5 sm:mb-6 md:mb-8">
        <div className="rounded-lg sm:rounded-xl border border-slate-200 bg-white p-3 sm:p-4 text-center">
          <div className="text-xl sm:text-2xl font-bold text-slate-900 mb-1">12</div>
          <div className="text-[10px] sm:text-xs text-slate-600">Active Strategies</div>
        </div>
      </div>

      {/* Search - Compact mobile */}
      <div className="relative mb-3 sm:mb-4">
        <Search className="absolute left-3 sm:left-4 top-1/2 -translate-y-1/2 h-4 w-4 sm:h-5 sm:w-5 text-slate-400" />
        <input
          className="w-full rounded-lg sm:rounded-xl border border-slate-300 pl-10 sm:pl-12 pr-3 sm:pr-4 py-2.5 sm:py-3 text-sm sm:text-base"
          placeholder="Search algorithms..."
        />
      </div>

      {/* Filters - Wrap on mobile */}
      <div className="flex flex-wrap gap-2 sm:gap-3">
        <Filter className="h-4 w-4 text-slate-600 mt-2" />
        <select className="rounded-md sm:rounded-lg border px-3 py-2 text-xs sm:text-sm font-medium">
          <option>All Assets</option>
        </select>
      </div>
    </div>
  </div>

  {/* Algorithm Grid - Single col mobile */}
  <div className="max-w-7xl mx-auto px-3 sm:px-4 md:px-6 py-5 sm:py-6 md:py-8">
    <div className="grid grid-cols-1 md:grid-cols-2 lg:grid-cols-3 gap-4 sm:gap-5 md:gap-6">
      <div className="rounded-xl sm:rounded-2xl border border-slate-200 bg-white p-4 sm:p-5 md:p-6 shadow-sm hover:shadow-md">
        {/* Header - Compact */}
        <div className="flex items-start justify-between mb-3 sm:mb-4">
          <div className="flex-1">
            <div className="flex items-center gap-2 mb-1.5 sm:mb-2">
              <span className="rounded-md px-2 py-0.5 text-[10px] sm:text-xs font-medium bg-orange-100 text-orange-700">
                CRYPTO
              </span>
              <span className="text-[10px] sm:text-xs font-medium text-slate-500">BTC/USD</span>
            </div>
            <h3 className="text-base sm:text-lg font-bold text-slate-900">Momentum Master</h3>
          </div>
          <div className="rounded-full bg-gradient-to-br from-blue-100 to-cyan-100 p-2">
            <Bot className="h-4 w-4 sm:h-5 sm:w-5 text-blue-600" />
          </div>
        </div>

        {/* Description - Compact */}
        <p className="text-xs sm:text-sm text-slate-600 mb-3 sm:mb-4 line-clamp-2">
          Advanced momentum strategy for trending markets
        </p>

        {/* Stats Grid - Tight spacing */}
        <div className="grid grid-cols-2 gap-2 sm:gap-3 mb-3 sm:mb-4">
          <div className="rounded-lg bg-emerald-50 p-2.5 sm:p-3">
            <div className="flex items-center gap-1 mb-1">
              <TrendingUp className="h-3 w-3 text-emerald-600" />
              <span className="text-[10px] sm:text-xs text-emerald-700">Avg Return</span>
            </div>
            <div className="text-base sm:text-lg font-bold text-emerald-700">+24.7%</div>
          </div>
          <div className="rounded-lg bg-blue-50 p-2.5 sm:p-3">
            <div className="flex items-center gap-1 mb-1">
              <BarChart3 className="h-3 w-3 text-blue-600" />
              <span className="text-[10px] sm:text-xs text-blue-700">Win Rate</span>
            </div>
            <div className="text-base sm:text-lg font-bold text-blue-700">68%</div>
          </div>
        </div>

        {/* Footer - Compact */}
        <div className="flex items-center justify-between pt-3 sm:pt-4 border-t border-slate-100">
          <div>
            <div className="inline-block rounded-md border px-2 py-0.5 text-[10px] sm:text-xs font-medium bg-amber-100 text-amber-700 border-amber-200">
              MEDIUM RISK
            </div>
            <div className="flex items-center gap-1 text-[10px] sm:text-xs text-slate-600 mt-1">
              <DollarSign className="h-3 w-3" />
              Min: $1,000
            </div>
          </div>
          <button className="rounded-lg bg-blue-600 px-3 py-1.5 sm:px-4 sm:py-2 text-xs sm:text-sm font-semibold text-white">
            View
            <ArrowRight className="inline-block ml-1 h-3 w-3 sm:h-4 sm:w-4" />
          </button>
        </div>
      </div>
    </div>
  </div>
</div>
```

### HedgeFundDashboard.tsx

```tsx
<div className="min-h-screen bg-gradient-to-br from-slate-900 via-blue-900 to-slate-900">
  {/* Header - Compact */}
  <div className="border-b border-white/10 bg-slate-900/50">
    <div className="max-w-7xl mx-auto px-3 sm:px-4 md:px-6 py-4 sm:py-5 md:py-6">
      {/* Back Button */}
      <button className="flex items-center gap-2 text-xs sm:text-sm text-slate-300 mb-3 sm:mb-4">
        <ArrowLeft className="h-4 w-4" />
        Back to Portfolio
      </button>

      {/* Header Content - Stack on mobile */}
      <div className="flex flex-col sm:flex-row items-start sm:items-center justify-between gap-3 sm:gap-4">
        <div className="flex items-center gap-2.5 sm:gap-3 md:gap-4">
          <div className="rounded-xl sm:rounded-2xl bg-gradient-to-br from-blue-500 to-cyan-500 p-2.5 sm:p-3 md:p-4">
            <Building2 className="h-6 w-6 sm:h-8 sm:w-8 md:h-10 md:w-10 text-white" />
          </div>
          <div>
            <h1 className="text-xl sm:text-2xl md:text-3xl font-bold text-white mb-0.5 sm:mb-1">Hedge Fund LP Portal</h1>
            <p className="text-[10px] sm:text-xs md:text-sm text-blue-200">Global Markets Consulting Fund I, LP</p>
          </div>
        </div>

        {/* Status Badge */}
        <div className="text-left sm:text-right">
          <div className="text-[10px] sm:text-xs text-slate-400 mb-1">LP Status</div>
          <div className="inline-flex items-center gap-1.5 sm:gap-2 rounded-lg bg-emerald-500/20 border border-emerald-500/30 px-2 sm:px-2.5 py-1">
            <div className="h-1.5 w-1.5 sm:h-2 sm:w-2 rounded-full bg-emerald-400"></div>
            <span className="text-[10px] sm:text-xs font-semibold text-emerald-300">Active</span>
          </div>
        </div>
      </div>
    </div>
  </div>

  {/* Content - Reduced padding */}
  <div className="max-w-7xl mx-auto px-3 sm:px-4 md:px-6 py-4 sm:py-6 md:py-8">
    {/* Stats Grid - 2 cols mobile, 4 desktop */}
    <div className="grid grid-cols-2 md:grid-cols-4 gap-2.5 sm:gap-3 md:gap-4 lg:gap-6 mb-5 sm:mb-6 md:mb-8">
      <div className="rounded-xl sm:rounded-2xl border border-white/10 bg-white/5 p-3 sm:p-4 md:p-5 lg:p-6">
        <div className="flex items-center justify-between mb-2 sm:mb-3 md:mb-4">
          <span className="text-[10px] sm:text-xs md:text-sm text-slate-400">Your Investment</span>
          <DollarSign className="h-4 w-4 sm:h-4.5 sm:w-4.5 md:h-5 md:w-5 text-blue-400" />
        </div>
        <div className="text-xl sm:text-2xl md:text-3xl font-bold text-white mb-1 sm:mb-2">
          $125,000
        </div>
        <div className="text-[10px] sm:text-xs md:text-sm text-emerald-400">
          +$25,000 gain
        </div>
      </div>
    </div>

    {/* Main + Sidebar - Stack on mobile */}
    <div className="grid grid-cols-1 lg:grid-cols-3 gap-4 sm:gap-5 md:gap-6 lg:gap-8">
      {/* Main Content */}
      <div className="lg:col-span-2 space-y-4 sm:space-y-5 md:space-y-6">
        {/* Performance Chart */}
        <div className="rounded-xl sm:rounded-2xl border border-white/10 bg-white/5 p-4 sm:p-5 md:p-6">
          <div className="flex flex-col sm:flex-row items-start sm:items-center justify-between gap-3 mb-4 sm:mb-5 md:mb-6">
            <h2 className="text-base sm:text-lg md:text-xl font-bold text-white flex items-center gap-2">
              <Activity className="h-4 w-4 sm:h-5 sm:w-5 text-blue-400" />
              NAV Performance
            </h2>

            {/* Period Selector - Compact mobile */}
            <div className="flex flex-wrap gap-1 sm:gap-1.5 md:gap-2">
              {['1M', '3M', '6M', 'YTD', '1Y', 'ALL'].map(period => (
                <button key={period} className="rounded-md px-2 py-1 text-[10px] sm:text-xs font-medium">
                  {period}
                </button>
              ))}
            </div>
          </div>

          {/* Chart - Smaller mobile height */}
          <div className="h-48 sm:h-56 md:h-64 lg:h-80 bg-slate-800/30 rounded-lg sm:rounded-xl" />
        </div>

        {/* Monthly Returns - Compact grid */}
        <div className="rounded-xl sm:rounded-2xl border border-white/10 bg-white/5 p-4 sm:p-5 md:p-6">
          <h2 className="text-base sm:text-lg md:text-xl font-bold text-white mb-4 sm:mb-5 md:mb-6">
            Monthly Returns (2024)
          </h2>
          <div className="grid grid-cols-3 sm:grid-cols-5 gap-2 sm:gap-2.5 md:gap-3">
            <div className="text-center">
              <div className="text-[9px] sm:text-[10px] md:text-xs text-slate-400 mb-1.5 sm:mb-2">Jan</div>
              <div className="rounded-md sm:rounded-lg px-1.5 py-1 sm:px-2 sm:py-1.5 bg-emerald-500/20 text-emerald-300 text-[11px] sm:text-xs md:text-sm font-semibold">
                +2.1%
              </div>
            </div>
          </div>
        </div>
      </div>

      {/* Sidebar - Stack on mobile */}
      <div className="space-y-4 sm:space-y-5 md:space-y-6">
        {/* Fund Stats */}
        <div className="rounded-xl sm:rounded-2xl border border-white/10 bg-white/5 p-4 sm:p-5 md:p-6">
          <h3 className="text-sm sm:text-base md:text-lg font-bold text-white mb-3 sm:mb-4">
            Fund Statistics
          </h3>
          <div className="space-y-2">
            <div className="flex justify-between py-2 border-b border-white/10 text-[11px] sm:text-xs md:text-sm">
              <span className="text-slate-400">Current NAV</span>
              <span className="font-semibold text-white">$1,245.67</span>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</div>
```

### FundingFlow Pages

```tsx
{/* FundingPageLayout - Already optimized */}
<FundingPageLayout
  title="Fund Your Account"
  subtitle="Welcome to your capital contribution experience"
  currentStep="start"
>
  <FundingCompactCard
    eyebrow="Funding Overview"
    title="Move through your funding journey"
    description="We guide you step by step"
  >
    <ul className="space-y-2 text-[12.5px] text-slate-600">
      <li className="flex items-start gap-2">
        <span className="mt-0.5 inline-flex h-5 w-5 items-center justify-center rounded-full bg-blue-50">
          <Icon className="h-3.5 w-3.5" />
        </span>
        <span>Sign the subscription agreements</span>
      </li>
    </ul>
  </FundingCompactCard>
</FundingPageLayout>

{/* FundingMethodPage - Compact */}
<div className="rounded-2xl sm:rounded-3xl border p-4 sm:p-5 md:p-7">
  {/* Summary Grid */}
  <div className="grid gap-3 sm:gap-4 rounded-xl sm:rounded-2xl border bg-slate-50/70 p-3 sm:p-4 text-sm">
    <div>
      <p className="text-[10px] sm:text-xs font-semibold uppercase tracking-wider text-slate-400">
        Contribution
      </p>
      <p className="mt-1.5 sm:mt-2 text-lg sm:text-xl font-semibold text-slate-900">
        $10,000
      </p>
    </div>
  </div>

  {/* Payment Methods - 1 col mobile, 2 desktop */}
  <div className="grid gap-3 sm:gap-4 sm:grid-cols-2 mt-4 sm:mt-5 md:mt-6">
    <button className="flex flex-col rounded-xl sm:rounded-2xl border px-4 py-4 sm:px-5 sm:py-5 text-left">
      <div className="flex items-center gap-2.5 sm:gap-3">
        <div className="flex h-9 w-9 sm:h-10 sm:w-10 items-center justify-center rounded-lg sm:rounded-xl bg-slate-100">
          <CreditCard className="h-4 w-4 sm:h-5 sm:w-5" />
        </div>
        <div>
          <p className="text-sm sm:text-base font-semibold text-slate-900">Credit / Debit Card</p>
          <p className="text-[10px] sm:text-xs text-slate-500">Instantly post funds</p>
        </div>
      </div>
      <span className="mt-3 sm:mt-4 text-[10px] sm:text-xs font-semibold uppercase tracking-wider text-blue-600">
        Best for rapid allocations
      </span>
    </button>
  </div>
</div>
```

## Global CSS Improvements

Add these to `index.css`:

```css
/* Mobile-first base styles */
* {
  -webkit-tap-highlight-color: transparent;
}

html {
  font-size: 16px; /* Base 16px for better mobile readability */
}

body {
  font-size: 0.875rem; /* 14px base on mobile */
  line-height: 1.5;
}

@media (min-width: 640px) {
  body {
    font-size: 1rem; /* 16px on tablet+ */
  }
}

/* Touch-friendly scrolling */
* {
  -webkit-overflow-scrolling: touch;
  scroll-behavior: smooth;
}

/* Improved button/link touch targets */
button, a {
  min-height: 44px;
  min-width: 44px;
  touch-action: manipulation;
}

/* Reduce motion for accessibility */
@media (prefers-reduced-motion: reduce) {
  *,
  *::before,
  *::after {
    animation-duration: 0.01ms !important;
    animation-iteration-count: 1 !important;
    transition-duration: 0.01ms !important;
  }
}

/* Safe area insets for notched devices */
@supports (padding: env(safe-area-inset-top)) {
  .safe-area-top {
    padding-top: env(safe-area-inset-top);
  }
  .safe-area-bottom {
    padding-bottom: env(safe-area-inset-bottom);
  }
  .safe-area-left {
    padding-left: env(safe-area-inset-left);
  }
  .safe-area-right {
    padding-right: env(safe-area-inset-right);
  }
}
```

## Testing Checklist

### Mobile (< 768px)
- [ ] All text is readable at base font sizes
- [ ] Touch targets are minimum 44px
- [ ] Cards fit content without excessive scrolling
- [ ] Forms are single-column and keyboard-friendly
- [ ] Images scale appropriately
- [ ] Navigation is thumb-accessible
- [ ] Modals/dialogs fit within viewport

### Tablet (768-1200px)
- [ ] Two-column layouts work correctly
- [ ] Typography scales proportionally
- [ ] Touch targets remain accessible
- [ ] Side-by-side comparisons are readable

### Desktop (> 1200px)
- [ ] Full layouts display with proper spacing
- [ ] Hover states work correctly
- [ ] Content is centered with max-width
- [ ] No excessive whitespace

### Cross-Browser
- [ ] iOS Safari (notch handling)
- [ ] Android Chrome
- [ ] Desktop browsers
- [ ] PWA/standalone mode

## Performance Optimizations

1. **Reduce Shadow Usage**: Use `shadow-sm` and `shadow-md` instead of `shadow-2xl` on mobile
2. **Minimize Animations**: Use `motion.div` sparingly on mobile, prefer CSS transitions
3. **Optimize Images**: Ensure all images have proper responsive sizing
4. **Lazy Load**: Implement lazy loading for below-the-fold content
5. **Reduce Bundle Size**: Code-split large components

## Implementation Priority

1. ✅ **DONE**: Core UI components (Button, Card)
2. **HIGH**: Onboarding flows (ManagedAllocationOnboarding, AutomatedStrategiesLanding)
3. **HIGH**: Marketplace (AlgorithmMarketplace)
4. **MEDIUM**: Dashboard views (HedgeFundDashboard, LivePortfolioDashboard)
5. **MEDIUM**: Funding flow pages
6. **LOW**: Admin/settings pages
7. **LOW**: Documentation pages

## Next Steps

1. Apply these patterns systematically to each component
2. Test on real devices (iPhone, Android)
3. Run Lighthouse audits for mobile performance
4. Gather user feedback on mobile experience
5. Iterate based on analytics data
