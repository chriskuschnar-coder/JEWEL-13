# Production Deployment Guide

## 🎯 Quick Start

```bash
# Web App
npm install
npm run lint
npm run build

# Mobile App
cd mobile
npm install
npx expo install --check
```

## 📱 Mobile App Deployment

### Prerequisites
```bash
# Install EAS CLI globally
npm install -g eas-cli

# Login to Expo
eas login

# Initialize project (first time only)
cd mobile
eas init
```

### Environment Setup
```bash
# Create .env file from template
cp .env.example .env

# Edit .env with actual values
# EXPO_PUBLIC_SUPABASE_URL=...
# EXPO_PUBLIC_SUPABASE_ANON_KEY=...
```

### Development Builds
```bash
# iOS Simulator
eas build --profile development --platform ios

# Android Emulator/Device
eas build --profile development --platform android

# Run locally
npm run ios
npm run android
```

### Preview Builds (Internal Testing)
```bash
# iOS (TestFlight internal)
eas build --profile preview --platform ios

# Android (Internal testing track)
eas build --profile preview --platform android
```

### Production Builds

#### iOS App Store
```bash
# Build for App Store
eas build --profile production --platform ios

# Auto-submit to App Store Connect
eas build --profile production --platform ios --auto-submit

# Manual submit (if needed)
eas submit --profile production --platform ios
```

#### Android Play Store
```bash
# Build for Play Store
eas build --profile production --platform android

# Auto-submit to Play Console
eas build --profile production --platform android --auto-submit

# Manual submit (if needed)
eas submit --profile production --platform android
```

### Monitor Build Status
```bash
# Check build status
eas build:list

# View build logs
eas build:view [build-id]
```

## 🌐 Web App Deployment

### Build
```bash
# Production build (with optimizations)
npm run build:production

# Preview build locally
npm run preview
```

### Verification Before Deploy
```bash
# Run all checks
./scripts/verify-release.sh

# Or manually:
npm run lint
npm run build
npm audit --production
```

### Deploy to Netlify
```bash
# Build is already in ./dist folder
netlify deploy --prod --dir=dist

# Or via git (automatic)
git push origin main
```

### Deploy to Vercel
```bash
vercel --prod
```

### Deploy to Custom Server
```bash
# Copy dist folder to server
rsync -avz dist/ user@server:/var/www/html/

# Or use FTP/SFTP
```

## 🔍 Pre-Release Checklist

### Code Quality
- [ ] All TypeScript errors resolved
- [ ] ESLint warnings reviewed
- [ ] No console.log statements (auto-stripped)
- [ ] Error boundaries in place
- [ ] Loading states implemented

### Functionality
- [ ] All navigation flows work
- [ ] Forms validate correctly
- [ ] API calls handle errors gracefully
- [ ] Offline mode functional
- [ ] Dark mode works across all screens

### Performance
- [ ] Bundle size acceptable (< 1.5MB gzip)
- [ ] Images optimized
- [ ] Lists virtualized
- [ ] No memory leaks
- [ ] Smooth animations (60fps)

### Security
- [ ] No secrets in code
- [ ] Input sanitization in place
- [ ] HTTPS enforced
- [ ] Secure storage for tokens
- [ ] Privacy policy linked

### Mobile Specific
- [ ] iOS: Privacy usage strings added
- [ ] Android: Permissions minimized
- [ ] Touch targets ≥ 44x44 points
- [ ] Safe areas handled
- [ ] Biometric auth working

### Store Assets
- [ ] App icons generated (all sizes)
- [ ] Screenshots captured (multiple devices)
- [ ] Store descriptions written
- [ ] Keywords researched
- [ ] Privacy policy URL ready

## 📊 Monitoring

### After Deployment

```bash
# Web: Check bundle stats
npm run build -- --stats

# Monitor analytics (setup required)
# - Page views
# - User sessions
# - Error rates
# - Performance metrics

# Mobile: Monitor via EAS
eas update:list
eas build:list

# Check crash reports
# - iOS: Xcode Organizer
# - Android: Play Console
```

## 🔄 Version Updates

### Increment Versions

**Mobile (app.json):**
```json
{
  "version": "1.0.1",  // User-visible version
  "ios": {
    "buildNumber": "2"  // Auto-incremented by EAS
  },
  "android": {
    "versionCode": 2  // Auto-incremented by EAS
  }
}
```

**Web (package.json):**
```json
{
  "version": "1.0.1"
}
```

### Git Tags
```bash
# Tag release
git tag -a v1.0.1 -m "Release version 1.0.1"
git push origin v1.0.1
```

## 🆘 Troubleshooting

### Build Failures

**TypeScript errors:**
```bash
npm run build
# Fix reported errors
```

**Dependency issues:**
```bash
# Clear cache and reinstall
rm -rf node_modules package-lock.json
npm install

# Mobile
cd mobile
rm -rf node_modules
npx expo install --check
```

**EAS build fails:**
```bash
# View detailed logs
eas build:view [build-id]

# Clear EAS cache
eas build --profile production --platform ios --clear-cache
```

### Store Rejection

**iOS:**
- Review App Store rejection reason
- Common issues: Missing privacy policy, crashes on launch, unclear usage strings
- Fix and resubmit via App Store Connect

**Android:**
- Review Play Console rejection
- Common issues: Missing privacy policy, inappropriate content rating
- Update and resubmit

### Runtime Errors

**Check logs:**
```bash
# Web: Browser console
# iOS: Xcode device logs
# Android: adb logcat
```

**Common fixes:**
- Clear app cache
- Reinstall app
- Check API endpoints
- Verify environment variables

## 📚 Resources

- [Expo EAS Build](https://docs.expo.dev/build/introduction/)
- [Expo EAS Submit](https://docs.expo.dev/submit/introduction/)
- [App Store Review Guidelines](https://developer.apple.com/app-store/review/guidelines/)
- [Google Play Policy](https://play.google.com/about/developer-content-policy/)
- [Vite Build Documentation](https://vitejs.dev/guide/build.html)

## 🎉 Congratulations!

Your app is now production-ready. Remember to:
- Monitor user feedback
- Track analytics
- Plan regular updates
- Respond to reviews
- Keep dependencies updated

Happy shipping! 🚀
