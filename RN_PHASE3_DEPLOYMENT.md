# React Native Phase 3 - App Store & Google Play Deployment

## Overview

This guide covers the complete deployment process for the Global Markets Capital mobile app to both the Apple App Store and Google Play Store.

## Prerequisites

### Required Accounts
- [ ] Apple Developer Account ($99/year)
- [ ] Google Play Developer Account ($25 one-time)
- [ ] Expo Account (free or paid)
- [ ] EAS CLI installed (`npm install -g eas-cli`)

### Required Tools
- [ ] Xcode (Mac only, for iOS builds)
- [ ] Android Studio (for Android builds)
- [ ] Node.js 16+
- [ ] Git

## Phase 3 Completed Features

### ✅ Branding & Identity
- App configuration in `app.json`
- Splash screen configuration
- Dark/light mode consistency
- Brand colors defined

### ✅ iOS Configuration
**Permissions Configured:**
- Face ID / Touch ID (biometrics)
- Push Notifications
- Camera access (KYC documents)
- Photo library access
- Network access

**Info.plist Entries:**
```xml
<key>NSCameraUsageDescription</key>
<string>We need camera access for document scanning and KYC verification</string>

<key>NSFaceIDUsageDescription</key>
<string>Enable biometric authentication for secure access to your account</string>

<key>NSPhotoLibraryUsageDescription</key>
<string>Upload photos for KYC verification</string>

<key>ITSAppUsesNonExemptEncryption</key>
<false/>
```

**Bundle Identifier:** `com.globalmarketscapital.mobile`
**Build Number:** 1

### ✅ Android Configuration
**Permissions Configured:**
- Biometric authentication
- Push notifications
- Camera access
- Internet and network access
- Storage access
- Vibration

**Package Name:** `com.globalmarketscapital.mobile`
**Version Code:** 1

### ✅ Compliance
- Privacy policy constants defined
- Financial disclaimers component created
- Data collection documented
- App Store privacy labels prepared

### ✅ Build Configuration
- EAS Build configured for all environments
- Development, Preview, and Production profiles
- Submit configuration ready

## App Store Assets Needed

### Icons
Required icon sizes (all must be PNG, no transparency):

**iOS:**
- 1024x1024 (App Store)
- 180x180 (iPhone)
- 167x167 (iPad Pro)
- 152x152 (iPad)
- 120x120 (iPhone)
- 87x87 (iPhone)
- 80x80 (iPad)
- 76x76 (iPad)
- 60x60 (iPhone)
- 58x58 (iPhone)
- 40x40 (iPad/iPhone)
- 29x29 (iPhone)
- 20x20 (iPad/iPhone)

**Android:**
- 512x512 (Play Store)
- 192x192 (xxxhdpi)
- 144x144 (xxhdpi)
- 96x96 (xhdpi)
- 72x72 (hdpi)
- 48x48 (mdpi)

### Screenshots

**iOS (Required for each device type):**
- iPhone 6.7" (1290 x 2796) - 3-10 screenshots
- iPhone 6.5" (1242 x 2688) - 3-10 screenshots
- iPhone 5.5" (1242 x 2208) - 3-10 screenshots
- iPad Pro 12.9" (2048 x 2732) - 3-10 screenshots

**Android:**
- Phone (1080 x 1920 or higher) - 2-8 screenshots
- Tablet (1536 x 2048 or higher) - 2-8 screenshots

### Suggested Screenshots
1. Portfolio overview showing balance and performance
2. Markets screen with live prices
3. Asset detail with trading interface
4. AI Strategies marketplace
5. Security features (biometric login)
6. Trading execution panel

## Building for App Stores

### Step 1: Install EAS CLI

```bash
npm install -g eas-cli
```

### Step 2: Login to Expo

```bash
eas login
```

### Step 3: Configure EAS Project

```bash
cd mobile
eas build:configure
```

This will create/update `eas.json` and link your project to EAS.

### Step 4: Build for iOS

**Development Build (for testing):**
```bash
eas build --platform ios --profile development
```

**Preview Build (TestFlight internal):**
```bash
eas build --platform ios --profile preview
```

**Production Build (App Store):**
```bash
eas build --platform ios --profile production
```

The build will run in the cloud and generate an `.ipa` file.

### Step 5: Build for Android

**Development Build:**
```bash
eas build --platform android --profile development
```

**Preview Build (APK for testing):**
```bash
eas build --platform android --profile preview
```

**Production Build (AAB for Play Store):**
```bash
eas build --platform android --profile production
```

The production build generates an `.aab` (Android App Bundle) file.

### Step 6: Submit Builds

**iOS (TestFlight):**
```bash
eas submit --platform ios --latest
```

**Android (Internal Testing):**
```bash
eas submit --platform android --latest
```

## App Store Connect Setup (iOS)

### 1. Create App Record
1. Log in to [App Store Connect](https://appstoreconnect.apple.com)
2. Go to "My Apps" → "+" → "New App"
3. Fill in details:
   - **Name:** Global Markets Capital
   - **Primary Language:** English (U.S.)
   - **Bundle ID:** com.globalmarketscapital.mobile
   - **SKU:** GMC-MOBILE-001

### 2. App Information
- **Category:** Finance
- **Secondary Category:** Business (optional)
- **Content Rights:** Contains third-party content
- **Age Rating:** 17+ (due to financial content)

### 3. Privacy Policy
Upload your privacy policy URL:
```
https://globalmarketscapital.com/privacy-policy
```

### 4. App Privacy
Configure data collection (from `privacy.ts`):
- **Contact Information:** Collected, linked to user
- **Financial Information:** Collected, linked to user
- **Location:** Collected (approximate), linked to user
- **User Content:** Collected, linked to user
- **Identifiers:** Collected, linked to user
- **Usage Data:** Collected, linked to user
- **Diagnostics:** Collected, not linked to user

### 5. Pricing
- **Price:** Free
- **In-App Purchases:** None initially

### 6. App Review Information
Provide demo account for review:
```
Username: reviewer@globalmarketscapital.com
Password: [Secure demo password]

Notes: This is a financial services app. The demo account has limited functionality
for review purposes. Full functionality requires KYC verification.
```

### 7. Version Information
- **Version:** 1.0.0
- **Copyright:** 2025 Global Markets Capital
- **Promotional Text:** Professional hedge fund and AI-powered trading platform
- **Description:** (See App Store Description below)
- **Keywords:** trading, crypto, hedge fund, investment, finance, AI strategies
- **Support URL:** https://globalmarketscapital.com/support
- **Marketing URL:** https://globalmarketscapital.com

### 8. Build
Select the uploaded build from TestFlight.

### 9. Screenshots & Previews
Upload screenshots for all required device sizes.

### 10. Submit for Review
Click "Submit for Review" and wait 1-3 days for Apple's review.

## Google Play Console Setup (Android)

### 1. Create App
1. Log in to [Google Play Console](https://play.google.com/console)
2. Click "Create app"
3. Fill in details:
   - **App name:** Global Markets Capital
   - **Default language:** English (United States)
   - **App or game:** App
   - **Free or paid:** Free

### 2. Store Listing
- **Short description:** (50 characters)
  ```
  Professional trading & hedge fund platform
  ```

- **Full description:** (See Play Store Description below)

- **App icon:** 512x512 PNG

- **Feature graphic:** 1024x500 PNG

- **Screenshots:** 2-8 phone screenshots

- **Category:** Finance

- **Contact details:**
  ```
  Email: support@globalmarketscapital.com
  Phone: [Your support phone]
  Website: https://globalmarketscapital.com
  ```

### 3. Content Rating
Complete questionnaire:
- **Category:** Financial app with trading
- Age rating will likely be 18+ due to financial content

### 4. Target Audience
- **Target age:** 18+
- **Ads:** No (unless you add ads later)

### 5. Data Safety
Configure data collection (from `privacy.ts`):
- **Location:** Approximate location, required
- **Personal info:** Name, email, address, financial info
- **Financial info:** Payment info, transaction history
- **App activity:** In-app actions
- **Device or other IDs:** Required for analytics

All data is collected, encrypted in transit, and users can request deletion.

### 6. App Access
Provide demo credentials for review:
```
Username: reviewer@globalmarketscapital.com
Password: [Secure demo password]

Instructions:
1. Login with provided credentials
2. Explore Markets, Portfolio, and Trading features
3. KYC verification is required for real trading (demo account bypasses this)
```

### 7. Privacy Policy
```
https://globalmarketscapital.com/privacy-policy
```

### 8. Create Release
1. Go to "Production" → "Create new release"
2. Upload the `.aab` file from EAS build
3. Enter release notes
4. Review and roll out

## App Store Description Template

### Short Description (Apple Promotional Text)
```
Access institutional-grade hedge fund strategies and AI-powered trading from anywhere. Professional portfolio management in your pocket.
```

### Full Description
```
GLOBAL MARKETS CAPITAL - Professional Investment Platform

Invest like the institutions. Access hedge fund strategies, AI-powered trading algorithms, and self-directed trading all in one powerful mobile platform.

🏦 HEDGE FUND ACCESS
• Invest in professionally managed portfolios
• Transparent NAV/unit tracking
• Institutional-grade risk management
• Quarterly statements and tax documents

🤖 AI-POWERED STRATEGIES
• Choose from multiple AI trading algorithms
• Automated rebalancing
• Real-time performance tracking
• Risk-adjusted returns

📊 SELF-DIRECTED TRADING
• Trade cryptocurrencies with advanced tools
• Real-time market data and charts
• Multiple order types (Market, Limit, Stop)
• Leverage trading up to 100x
• Deep order books and recent trades

💼 COMPLETE PORTFOLIO MANAGEMENT
• Unified view of all investments
• Real-time P&L tracking
• Performance charts and analytics
• Detailed transaction history

🔐 BANK-LEVEL SECURITY
• Face ID / Touch ID authentication
• Two-factor authentication
• Encrypted data storage
• SOC 2 compliant infrastructure

📱 PROFESSIONAL FEATURES
• Live market data and alerts
• Push notifications for order fills
• Dark mode support
• Offline access to portfolio

INVESTOR REQUIREMENTS
• Must be 18+ and an accredited investor
• KYC verification required
• Minimum investment amounts apply

IMPORTANT DISCLAIMERS
All investments involve risk including loss of principal. Cryptocurrency trading is highly volatile. Past performance does not guarantee future results. This app is not investment advice.

Global Markets Capital is a registered investment adviser. Securities offered through licensed broker-dealers.

Support: support@globalmarketscapital.com
Website: https://globalmarketscapital.com
```

### Keywords (iOS)
```
trading, crypto, cryptocurrency, bitcoin, ethereum, investment, hedge fund, portfolio, finance, stocks, AI trading, automated trading, wealth management, fintech
```

## Play Store Description Template

### Short Description
```
Professional hedge fund access, AI trading strategies, and cryptocurrency trading platform.
```

### Full Description
```
(Same as App Store full description above)
```

## App Review Guidelines Compliance

### Apple App Store
✅ **Guideline 2.1 - App Completeness**
- App is fully functional
- Demo account provided for review
- All features accessible

✅ **Guideline 3.1 - In-App Purchase**
- No in-app purchases required
- External payment methods disclosed

✅ **Guideline 3.2 - Other Business Model Issues**
- Clear pricing and fee structure
- Terms disclosed before purchase

✅ **Guideline 4.0 - Design**
- Native iOS UI patterns
- Face ID integration
- Dark mode support

✅ **Guideline 5.1.1 - Data Collection and Storage**
- Privacy policy provided
- Data collection disclosed
- Encryption in transit and at rest

### Google Play Store
✅ **Financial Services Policy**
- Clear disclosure of investment risks
- Terms of service provided
- Proper licensing information

✅ **User Data Policy**
- Privacy policy accessible
- Data usage disclosed
- Secure data handling

✅ **Permissions**
- Only necessary permissions requested
- Permissions explained in-app

## Compliance Checklist

### Before Submission
- [ ] Privacy policy published and linked
- [ ] Terms of service published
- [ ] All required disclaimers added to app
- [ ] Demo/test account created for reviewers
- [ ] Screenshots captured for all device sizes
- [ ] App icon finalized (1024x1024 PNG)
- [ ] Support email set up and monitored
- [ ] Website has mobile app section
- [ ] Legal review of all disclosures
- [ ] Security audit completed

### iOS Specific
- [ ] Apple Developer account active
- [ ] Bundle ID registered
- [ ] App Store Connect app created
- [ ] TestFlight build uploaded and tested
- [ ] All required device screenshots
- [ ] Privacy labels configured
- [ ] Age rating set to 17+
- [ ] Export compliance confirmed (No encryption)

### Android Specific
- [ ] Google Play Developer account active
- [ ] App signed with production keystore
- [ ] Content rating questionnaire completed
- [ ] Data safety form filled out
- [ ] Target API level meets requirements
- [ ] Screenshots for phone and tablet

## Post-Submission

### iOS Timeline
- **TestFlight:** Available immediately after upload
- **App Review:** 1-3 days typically
- **If Rejected:** Address issues and resubmit
- **If Approved:** Live on App Store within 24 hours

### Android Timeline
- **Internal Testing:** Available immediately
- **Review:** 1-7 days typically
- **Rolling Release:** Can release to % of users
- **Full Release:** Available within hours

## Continuous Deployment

### Versioning Strategy
```
MAJOR.MINOR.PATCH

1.0.0 - Initial release
1.0.1 - Bug fixes
1.1.0 - New features
2.0.0 - Major redesign
```

### Release Process
1. Update version in `app.json`
2. Update build number/version code
3. Build with EAS
4. Test internally (TestFlight / Internal Testing)
5. Submit for review
6. Roll out gradually (Android) or full release (iOS)

### Hotfix Process
1. Create hotfix branch
2. Increment patch version
3. Build and test
4. Expedited review request (if critical)
5. Release immediately upon approval

## Monitoring & Analytics

### Recommended Tools
- **Crash Reporting:** Sentry or Bugsnag
- **Analytics:** Mixpanel or Amplitude
- **Performance:** Firebase Performance
- **Push Notifications:** OneSignal or Firebase

### Key Metrics to Track
- Daily/Monthly Active Users (DAU/MAU)
- Session duration
- Feature adoption rates
- Crash-free rate
- App store ratings
- Conversion rate (download → KYC → funded)

## Support Infrastructure

### Required Support Channels
- **Email:** support@globalmarketscapital.com
- **In-App:** Help/Support section
- **Website:** FAQ and knowledge base
- **Phone:** For high-value clients

### Response Time SLAs
- Critical issues: 1 hour
- Account issues: 4 hours
- General inquiries: 24 hours

## Legal Requirements

### United States
- SEC registration (if applicable)
- FinCEN compliance for crypto
- State money transmitter licenses
- Privacy compliance (CCPA, etc.)

### International
- GDPR compliance (EU)
- Data localization requirements
- Local financial regulations
- Know Your Customer (KYC) requirements

## Marketing Launch Plan

### Pre-Launch (2 weeks before)
- [ ] Press release drafted
- [ ] Social media accounts ready
- [ ] Landing page optimized
- [ ] Email campaign prepared
- [ ] Influencer outreach completed

### Launch Day
- [ ] Submit apps for review
- [ ] Send press release
- [ ] Post on social media
- [ ] Email existing users
- [ ] Monitor app store reviews

### Post-Launch (First Week)
- [ ] Respond to all reviews
- [ ] Monitor crash reports
- [ ] Track key metrics
- [ ] Gather user feedback
- [ ] Plan first update

## Troubleshooting Common Issues

### iOS Build Fails
- Ensure Xcode version is up to date
- Check bundle identifier matches Apple Developer portal
- Verify all required entitlements are configured
- Review build logs in EAS dashboard

### Android Build Fails
- Check Android SDK version compatibility
- Verify package name is unique
- Ensure all permissions are declared
- Review Gradle build logs

### App Rejected by Apple
- Review rejection message carefully
- Check App Review Guidelines
- Provide additional documentation if needed
- Use developer forums for guidance
- Resubmit after addressing issues

### App Rejected by Google
- Review Policy Center violations
- Update content or functionality as needed
- Appeal if rejection seems incorrect
- Respond to review team queries promptly

## Resources

### Official Documentation
- [Expo EAS Build](https://docs.expo.dev/build/introduction/)
- [Apple App Store Guidelines](https://developer.apple.com/app-store/review/guidelines/)
- [Google Play Policies](https://play.google.com/about/developer-content-policy/)
- [React Native Docs](https://reactnative.dev/)

### Helpful Tools
- [App Icon Generator](https://appicon.co/)
- [Screenshot Builder](https://www.screenshotbuilder.com/)
- [ASO Tools](https://www.mobileaction.co/)

### Community
- [Expo Discord](https://chat.expo.dev/)
- [React Native Community](https://reactnative.dev/community/overview)
- [Stack Overflow](https://stackoverflow.com/questions/tagged/react-native)

## Success Criteria

### Phase 3 Complete When:
- ✅ iOS build compiles successfully
- ✅ Android build compiles successfully
- ✅ All permissions configured
- ✅ Privacy disclosures in place
- ✅ Financial disclaimers added
- ✅ EAS Build configuration complete
- ✅ Documentation published

### Ready for Submission When:
- [ ] TestFlight build tested internally
- [ ] Internal testing completed on Android
- [ ] All assets prepared (icons, screenshots)
- [ ] Privacy policy and terms published
- [ ] Demo account created and verified
- [ ] Legal review completed
- [ ] Support infrastructure ready

## Conclusion

Phase 3 provides all the necessary configurations, compliance features, and documentation to deploy the Global Markets Capital mobile app to both the Apple App Store and Google Play Store.

The app is now configured with:
- ✅ Complete iOS and Android build settings
- ✅ All required permissions
- ✅ Privacy and financial disclosures
- ✅ EAS Build pipeline
- ✅ App Store submission guidelines
- ✅ Marketing and support infrastructure

Next step: Generate required assets (icons, screenshots), create app store accounts, and submit for review.
