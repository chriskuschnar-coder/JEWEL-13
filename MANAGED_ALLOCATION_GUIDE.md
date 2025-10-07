# Guardian AI - Managed Allocation System

## Overview
Revolutionary managed portfolio allocation system with AI-powered strategy generation and institutional-grade protection.

## Key Features

### 🧠 AI Personality Assessment
- Gamified risk profiling with 4 unique investor archetypes
- Real-time risk/reward visualization
- Personality-based strategy matching

### 🎯 Investment Goal Selection
- Capital Preservation
- Steady Income
- Wealth Growth
- Maximum Returns

### ⏰ Time Horizon & Portfolio Sizing
- Short-term (< 1 year)
- Medium-term (1-3 years)
- Long-term (3+ years)
- Custom investment amounts (min $1,000)

### 🛡️ Guardian Protection Levels
1. **Standard Guardian** - Included
   - Real-time risk monitoring
   - Automated stop-loss
   - Daily rebalancing
   - Basic fraud detection

2. **Enhanced Guardian** - +0.1% fee (POPULAR)
   - AI anomaly detection
   - Dynamic position sizing
   - Instant rebalancing
   - Priority execution
   - 24/7 monitoring

3. **Maximum Guardian** - +0.25% fee (PREMIUM)
   - Dedicated account manager
   - Custom risk parameters
   - Flash crash protection
   - Tax-loss harvesting
   - Quarterly reviews
   - White-glove support

### ✨ AI Strategy Generation
- Real-time algorithm allocation
- Multi-asset portfolio construction
- Risk-optimized distributions
- Projected return modeling

### 🔒 Integrated KYC & Funding
- Seamless Didit KYC verification
- Multiple funding options
- Secure document signing
- Bank-grade security

## User Flow

1. **Welcome** → AI introduction and value proposition
2. **Risk Assessment** → Choose investor archetype
3. **Investment Goal** → Define objectives
4. **Time & Size** → Set timeline and amount
5. **Protection Level** → Select guardian tier
6. **Strategy Generation** → AI creates custom portfolio
7. **Finalization** → Document signing → KYC verification → Funding

### Step 7 Breakdown (Finalization)
The final step has three sequential substeps that must be completed in order:

**📄 Document Review & Signing** (Step 1)
   - Review LPA, PPM, and Subscription Agreement
   - Complete all required exhibits and signatures
   - Must be completed before proceeding to KYC
   - Amber-colored card with FileText icon

**🛡️ Identity Verification - KYC** (Step 2)
   - Didit-powered identity verification
   - Government ID and selfie verification
   - Only unlocks after documents are signed
   - Blue-colored card with Shield icon

**💰 Account Funding** (Step 3)
   - Multiple funding options (crypto, card, bank, wire transfer)
   - Investment amount based on Step 4 selection
   - Only unlocks after KYC is complete
   - Purple-colored card with DollarSign icon

Each step shows a locked/disabled state until prerequisites are met. Completed steps display a green checkmark.

## Database Schema

```sql
user_managed_profiles (
  - risk_tolerance: conservative | balanced | aggressive | ultra
  - investment_goal: preservation | income | growth | maximum
  - time_horizon: short | medium | long
  - initial_investment: decimal
  - protection_level: standard | enhanced | maximum
  - strategy_data: jsonb (algorithm allocations)
  - status: active | paused | closed
)
```

## Routes

- `/algorithms` - Landing page with options
- `/algorithms/managed-onboarding` - Full onboarding flow
- `/algorithms/managed-dashboard` - Active portfolio dashboard

## Design Philosophy

### Innovation
- **Gamification**: Risk assessment as personality quiz
- **AI Theatre**: Visible "thinking" and strategy generation
- **Trust Building**: Transparent algorithm allocation
- **Emotional Connection**: "Guardian" metaphor for protection

### User Psychology
- **Paradox of Choice**: Guided decision making
- **Loss Aversion**: Multiple protection tiers
- **Social Proof**: Performance metrics and stats
- **Progress Tracking**: Clear step indicators

### Technical Excellence
- Framer Motion animations throughout
- Real-time AI strategy generation simulation
- Responsive design for all devices
- Integrated with existing auth/funding systems

## What Makes This Unique

1. **Investor Archetypes** - Not just risk scores, but personalities
2. **Guardian Metaphor** - Emotional safety through branding
3. **Live Strategy Generation** - Users see AI "thinking"
4. **Multi-tier Protection** - Gamified safety levels
5. **Zero Marketplace Friction** - No algorithm selection paralysis

## Testing

1. Navigate to `/algorithms`
2. Click "Managed Allocation" card
3. Complete 7-step onboarding process
4. Verify profile saved to database
5. Redirected to managed dashboard

## Future Enhancements

- Real algorithm backtesting integration
- Live performance tracking
- Dynamic rebalancing notifications
- AI chat assistant for questions
- Portfolio simulation tools
- Tax optimization reports
