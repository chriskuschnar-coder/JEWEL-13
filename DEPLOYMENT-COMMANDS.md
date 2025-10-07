# Deployment Commands

## ✅ Verification Complete - Build Successful!

The app is production-ready. Follow these commands to deploy:

---

## 📦 Web App Deployment

### Local Verification
```bash
# Install dependencies (if needed)
npm install

# Run linter
npm run lint

# Build for production
npm run build

# Preview production build locally
npm run preview
```

### Deploy to Production
```bash
# Option 1: Deploy to Netlify
netlify deploy --prod --dir=dist

# Option 2: Deploy to Vercel
vercel --prod

# Option 3: Custom server (via rsync)
rsync -avz dist/ user@server:/var/www/html/
```

---

## 📱 Mobile App Deployment

### Setup (First Time Only)
```bash
# Install EAS CLI globally
npm install -g eas-cli

# Navigate to mobile directory
cd mobile

# Install dependencies
npm install

# Verify dependencies are compatible
npx expo install --check

# Login to Expo
eas login

# Initialize EAS project
eas init
```

### Environment Configuration
```bash
# Create environment file
cp .env.example .env

# Edit with your values (required):
# EXPO_PUBLIC_SUPABASE_URL=https://your-project.supabase.co
# EXPO_PUBLIC_SUPABASE_ANON_KEY=your-anon-key-here
```

### Development Builds (Testing)
```bash
# iOS (requires macOS)
eas build --profile development --platform ios

# Android
eas build --profile development --platform android

# Run on device after build completes
npm run ios    # iOS simulator
npm run android # Android emulator/device
```

### Production Builds (App Store / Play Store)

#### iOS App Store
```bash
# Build for App Store submission
eas build --profile production --platform ios

# Or build AND submit in one command
eas build --profile production --platform ios --auto-submit

# Manual submission (if needed)
eas submit --profile production --platform ios
```

#### Android Play Store
```bash
# Build for Play Store submission
eas build --profile production --platform android

# Or build AND submit in one command
eas build --profile production --platform android --auto-submit

# Manual submission (if needed)
eas submit --profile production --platform android
```

### Monitor Builds
```bash
# View build status
eas build:list

# View specific build
eas build:view <build-id>
```

---

## 🔍 Pre-Deployment Verification

### Run Verification Script
```bash
# From project root
chmod +x ./scripts/verify-release.sh
./scripts/verify-release.sh
```

### Manual Checks
```bash
# TypeScript compilation
npm run build

# ESLint
npm run lint

# Security audit
npm audit --production --audit-level=high

# Check bundle size
du -sh dist
```

---

## 📋 Final Checklist

### Before Deploying Web App
- [ ] Build completes without errors
- [ ] ESLint passes with no warnings
- [ ] Environment variables set (VITE_SUPABASE_URL, etc.)
- [ ] Test on multiple browsers
- [ ] Verify dark/light mode
- [ ] Check mobile responsive design

### Before Submitting Mobile App
- [ ] EAS project initialized
- [ ] Environment variables configured in .env
- [ ] App icons generated (1024x1024)
- [ ] Splash screen created
- [ ] Privacy policy URL ready
- [ ] Store descriptions written
- [ ] Screenshots captured (multiple device sizes)
- [ ] Tested on physical iOS and Android devices

### Store Submission
- [ ] Review store checklist: `docs/STORE-CHECKLIST.md`
- [ ] Prepare store assets (icons, screenshots, descriptions)
- [ ] Set up App Store Connect / Play Console accounts
- [ ] Configure code signing (iOS) or keystore (Android)
- [ ] Submit for review

---

## 🎉 Success Indicators

### Web App
```
✓ Build completed successfully
✓ Bundle size: ~1.3MB (gzipped: ~300KB)
✓ No TypeScript errors
✓ ESLint clean
✓ Console logs stripped in production
```

### Mobile App
```
✓ EAS build completes
✓ App installs on devices
✓ No crashes on launch
✓ All features functional
✓ Biometric auth works
✓ Deep links configured
```

---

## 🆘 Troubleshooting

### Build Fails
```bash
# Clear cache and rebuild
rm -rf node_modules dist
npm install
npm run build
```

### EAS Build Fails
```bash
# Clear EAS cache
eas build --clear-cache --profile production --platform ios

# View detailed logs
eas build:view <build-id>
```

### Dependencies Issues
```bash
# Mobile: Fix dependency mismatches
cd mobile
npx expo install --check --fix
```

---

## 📚 Documentation References

- Ship Readiness: `docs/SHIP-READINESS.md`
- Store Checklist: `docs/STORE-CHECKLIST.md`
- Full Deployment Guide: `PRODUCTION-DEPLOYMENT.md`
- Changes Summary: `CHANGES_SUMMARY.md`

---

## 🚀 You're Ready to Ship!

All production hardening is complete. Execute the commands above to deploy your app to production.

**Next Steps:**
1. Choose deployment target (web: Netlify/Vercel, mobile: App Store/Play Store)
2. Run verification script
3. Execute deployment commands
4. Monitor for errors
5. Celebrate launch! 🎉
