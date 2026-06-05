<div align="center">

# Cursor Skill — Full-Stack Native App Builder

**A comprehensive Cursor AI skill for building production-ready apps across three platforms:**

- **Node.js CMS** — Monolithic Express server with EJS views, Firebase or Supabase backend
- **iOS** — SwiftUI + MVVM with Firebase, OpenAI, StoreKit 2
- **Android** — Kotlin + Jetpack Compose + MVVM with Firebase, OpenAI, Google Play Billing

All three platforms share the same Firebase backend and follow consistent architectural patterns.

[![Cursor Skill](https://img.shields.io/badge/Cursor-Skill-000000?logo=cursor&logoColor=white)](https://cursor.com)
[![Node.js CMS](https://img.shields.io/badge/Node.js-CMS-339933?logo=node.js&logoColor=white)](#nodejs-cms--admin-panel)
[![SwiftUI](https://img.shields.io/badge/iOS-SwiftUI-F05138?logo=swift&logoColor=white)](#ios-app-swiftui)
[![Jetpack Compose](https://img.shields.io/badge/Android-Jetpack%20Compose-3DDC84?logo=android&logoColor=white)](#android-app-kotlin--jetpack-compose)
[![Firebase](https://img.shields.io/badge/Firebase-backend-FFCA28?logo=firebase&logoColor=black)](https://firebase.google.com)
[![Supabase](https://img.shields.io/badge/Supabase-optional-3FCF8E?logo=supabase&logoColor=white)](#nodejs-cms--admin-panel)
[![OpenAI](https://img.shields.io/badge/OpenAI-integration-412991?logo=openai&logoColor=white)](#important-notes--warnings)
[![MIT License](https://img.shields.io/badge/License-MIT-yellow.svg)](./LICENSE)

</div>

---

## What This Skill Covers

### Node.js CMS / Admin Panel
- Monolithic `server.js` with all routes inline (no separate routes/models/controllers)
- EJS views with `express-ejs-layouts` and `layout.ejs` (collapsible dark sidebar)
- Bulma CSS + Font Awesome for UI
- Firebase Admin SDK (Firestore, Storage, Auth) or Supabase (PostgreSQL, RLS)
- Session-based auth with bcrypt + Firestore/PostgreSQL session store
- Busboy file uploads (compatible with Firebase Cloud Functions)
- Maintenance mode, login lockout, RBAC
- Firebase Hosting + Cloud Functions deployment
- Dark mode with CSS custom properties
- Localization via separate view files per language

### iOS App (SwiftUI)
- SwiftUI + MVVM + Services layer (no DI framework)
- Firebase (Auth, Firestore, Storage, Analytics, Crashlytics, Messaging, Remote Config)
- OpenAI ChatGPT integration (chat + vision API) via URLSession
- StoreKit 2 subscriptions (monthly/yearly) with Firestore sync
- Trial management with Firestore realtime listener + cache-first pattern
- TipKit for contextual tips
- In-app review prompts (once per version, on positive moments)
- Push notifications (FCM) + scheduled local notifications
- WidgetKit (Home Screen, Lock Screen) + Live Activities (Dynamic Island)
- App Intents / Siri Shortcuts
- HealthKit integration
- Onboarding flow (paged TabView + Lottie animations)
- Offline caching (JSON file cache)
- Network monitor + offline banner
- Dark mode with light/dark Lottie variants
- Pattern lock + Face ID
- Deep linking via URL schemes
- Localization (10 languages)

### Android App (Kotlin / Jetpack Compose)
- Kotlin + Jetpack Compose + Material 3 + MVVM (no DI framework)
- Firebase (Auth, Firestore, Storage, Analytics, Crashlytics, Messaging, Remote Config)
- OpenAI ChatGPT integration (chat + vision API) via OkHttp + Gson
- Google Play Billing v8 subscriptions with Firestore sync
- Trial management with Firestore realtime listener + cache-first pattern
- In-app review prompts (Play Core, once per version)
- In-app updates (immediate vs flexible, staleness + priority logic)
- Push notifications (FCM) + WorkManager scheduled local notifications
- App Widgets (AppWidgetProvider) + Foreground Service live trackers
- CameraX for scanning
- Onboarding flow (HorizontalPager + Lottie)
- Offline caching (Firestore Source.CACHE + SharedPreferences)
- Network monitor + offline banner
- Material 3 dynamic color + dark mode
- Pattern lock + biometric auth
- Deep linking + shortcuts
- Localization (10 languages)
- ProGuard/R8 rules for Gson models

---

## Installation

### Install from Git

```bash
git clone https://github.com/Artl13/cursor-skill-fullstack-native-app-builder.git ~/.cursor/skills/cursor-skill-fullstack-native-app-builder
```

Then restart Cursor. The skill will activate whenever you ask about building apps, CMS systems, mobile apps, or any related features.

### Manual Install

Copy the entire `cursor-skill-fullstack-native-app-builder/` folder into `~/.cursor/skills/`.

---

## Folder Structure

```
cursor-skill-fullstack-native-app-builder/
├── SKILL.md                              # Main skill — platform router + shared patterns
├── README.md                             # This file
└── references/
    ├── cms/                              # Node.js CMS platform
    │   ├── cms-skill.md                  # Architecture, server.js, EJS views, routes
    │   ├── firebase.md                   # Firebase Admin, Firestore, sessions, Storage
    │   ├── supabase.md                   # Supabase, SQL schema, RLS, Storage
    │   └── content-modeling.md           # Entity schemas, lifecycle, localization
    ├── ios/                              # iOS platform
    │   ├── ios-skill.md                  # Architecture, app entry, tab bar, onboarding
    │   ├── firebase-ios.md               # Auth, Firestore, FCM, Remote Config, schedulers
    │   ├── openai-integration.md         # Chat, vision, retries, recommendations
    │   ├── storekit-subscriptions.md     # StoreKit 2, trial, paywall, gating
    │   └── widgets-liveactivities.md     # WidgetKit, Live Activities, App Group bridge
    ├── android/                          # Android platform
    │   ├── android-skill.md              # Architecture, MainActivity, navigation, review
    │   ├── firebase-android.md           # Auth, Firestore, FCM, Remote Config, WorkManager
    │   ├── openai-android.md             # OkHttp chat, vision, retries, ProGuard
    │   ├── play-billing.md               # Play Billing v8, trial, paywall, gating
    │   └── widgets-livenotifications.md  # AppWidgetProvider, foreground service trackers
    └── cicd.md                           # GitHub Actions, Fastlane, Playwright, deployment
```

---

## How It Works

When you ask Cursor to build something, the skill activates based on your request:

- **"Build me a CMS"** → Loads `references/cms/cms-skill.md`
- **"Create an iOS app"** → Loads `references/ios/ios-skill.md`
- **"Build an Android app"** → Loads `references/android/android-skill.md`
- **"Build a full-stack app"** → Loads all three as needed

Each platform skill references deeper documentation files for specific features (Firebase, OpenAI, subscriptions, widgets, etc.), which are loaded only when needed.

---

## Example Prompts

Here are example prompts you can use in Cursor to trigger this skill:

### Full-Stack Projects

- "Build me a fitness tracking app with an admin CMS, iOS app, and Android app"
- "Create a recipe sharing platform with a CMS to manage content, plus native iOS and Android apps"
- "Build a habit tracker with a Node.js admin panel, an iPhone app, and an Android app"

### CMS / Admin Panel Only

- "Build me a CMS for managing blog posts with Firebase backend"
- "Create an admin dashboard with user management, content CRUD, and file uploads using Supabase"
- "Build a Node.js admin panel with dark mode, login lockout, and role-based access"

### iOS App Only

- "Build an iOS app with Firebase auth, StoreKit 2 subscriptions, and push notifications"
- "Create a SwiftUI app with ChatGPT integration, camera scanning, and offline caching"
- "Build an iPhone app with onboarding flow, HealthKit, widgets, and Live Activities"

### Android App Only

- "Build an Android app with Jetpack Compose, Google Play Billing, and Firebase"
- "Create a Kotlin app with OpenAI chat, CameraX scanning, and Material 3 theming"
- "Build an Android app with Health Connect, app widgets, and in-app updates"

### Feature-Specific

- "Add subscription billing to my iOS app with StoreKit 2 and a paywall"
- "Set up push notifications with FCM and scheduled local reminders for Android"
- "Add WidgetKit home screen and lock screen widgets to my iOS app"
- "Integrate OpenAI vision API for camera scanning in my Android app"

---

## Important Notes & Warnings

### Firebase Billing — Be Careful with Costs

Firebase bills based on usage. A misconfigured app can generate unexpected costs very quickly.

**Firestore reads are the most common cost trap:**
- Every `.get()`, every `.onSnapshot()` listener tick, every query counts as reads
- A dashboard that queries 5 collections on load = 5 reads per user per page load
- A realtime listener that fires on every document change in a large collection can generate thousands of reads per minute
- **Widgets that refresh every 15-30 minutes multiply this** — each widget refresh triggers reads

**How to protect yourself:**
- **Set budget alerts** in Google Cloud Console → Billing → Budgets & Alerts. Set alerts at 50%, 80%, 100% of your expected monthly budget
- **Set daily spend limits** on Firebase if available, or use Google Cloud billing caps
- **Use Firestore cache-first pattern** — query `Source.CACHE` before server to reduce reads
- **Avoid listening to entire collections** — always filter with `.where()` and `.limit()`
- **Paginate everything** — never load all documents at once
- **Use `getDocuments()` instead of `addSnapshotListener()` when realtime is not needed**
- **Monitor usage daily** in Firebase Console → Usage & Billing during the first weeks after launch

**Cloud Functions:**
- Every HTTP request to a Cloud Function counts as an invocation
- If your CMS serves all traffic through a Cloud Function (`rewrites: "**" → app`), every page load, every API call, every static asset request is an invocation
- Serve static assets from Firebase Hosting directly (not through the function)
- Set `timeoutSeconds` and `memory` appropriately — don't over-provision

**Storage:**
- Downloads are billed — if you serve images directly from Firebase Storage URLs without a CDN, every image view = a download
- Use signed URLs with long expiry or put a CDN (Cloudflare, etc.) in front of Storage

### Notification Limits — Firebase Cloud Messaging

FCM itself is free and has no hard sending limit, but be aware:

- **Firestore writes from notifications:** If your app writes to Firestore when a notification is received or opened (logging analytics, updating read status), those writes count toward your Firestore bill
- **Scheduled local notifications are free** — they run entirely on-device and don't involve Firebase at all
- **Topic messaging** is more efficient than sending to individual tokens when targeting many users
- **Don't spam users** — too many notifications lead to uninstalls, which is worse than any billing issue

### Firebase Spending Controls

Firebase does **not** automatically stop your project when you exceed your budget. The budget alerts only send notifications — **your app continues running and accumulating charges** until you manually take action.

**To actually limit spending:**
1. Set up **budget alerts** at multiple thresholds (50%, 80%, 100%)
2. Create a **Cloud Function or Cloud Monitoring alert** that automatically disables billing or scales down when a threshold is hit
3. Alternatively, use **Google Cloud billing export to BigQuery** and monitor with dashboards
4. Consider starting on the **Spark (free) plan** during development and only upgrading to Blaze when you need it
5. On the Blaze plan, set a **programmatic billing cap** using the Cloud Billing API

**Example: Auto-disable billing when budget exceeded:**
```javascript
// Cloud Function triggered by budget alert pub/sub
exports.stopBilling = functions.pubsub
  .topic('billing-alerts')
  .onPublish(async (message) => {
    const data = JSON.parse(Buffer.from(message.data, 'base64').toString());
    if (data.costAmount > data.budgetAmount) {
      // Disable billing via Cloud Billing API
      // Or: disable Cloud Functions, scale down, etc.
      // IMPORTANT: This will take your app offline
    }
  });
```

### OpenAI API Costs

- Set **usage limits** in the OpenAI dashboard (Settings → Limits → Monthly budget)
- Use `gpt-4o-mini` for simple tasks (10x cheaper than `gpt-4o`)
- Cache AI responses locally — don't re-fetch the same recommendations daily
- **Vision API calls are expensive** — compress images before sending (JPEG 70% quality)
- Limit free users to a small number of AI requests per day/month
- Track usage per user in Firestore to enforce limits

### App Store / Play Store Subscriptions

- **Always test with sandbox/test accounts** before going live
- **Apple:** Sandbox subscriptions renew every few minutes (not monthly) — don't confuse this with real behavior
- **Google:** Use test card numbers and license testing accounts
- **Always implement restore purchases** — both stores require it
- **Sync subscription state to Firestore** so your CMS can read it — don't rely solely on client-side checks
- **Handle grace periods and billing retry** — a user in grace period should still have access

### General Production Checklist

- [ ] Firebase budget alerts configured
- [ ] OpenAI monthly spending limit set
- [ ] Firestore security rules deployed (not open to public)
- [ ] Firebase Storage rules deployed
- [ ] API keys in Remote Config (not hardcoded)
- [ ] Service account JSON files gitignored
- [ ] `.env` / `GoogleService-Info.plist` / `google-services.json` gitignored
- [ ] CORS restricted to your domain
- [ ] Rate limiting on public endpoints
- [ ] Error monitoring (Crashlytics) active
- [ ] Analytics events logging correctly
- [ ] Subscription flow tested end-to-end with sandbox accounts
- [ ] Push notifications tested on real devices
- [ ] Offline mode tested (airplane mode)
- [ ] Dark mode tested
- [ ] All supported languages tested

---

## License

MIT License — see [LICENSE](LICENSE) for details.
