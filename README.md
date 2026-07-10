# RDR1 Completionist — Expo (React Native) app
Tablet-first Expo Go app that mirrors the web dashboard: story missions,
stranger missions, challenges, bounties, jobs, gang hideouts, minigames,
locations, outfits, weapons, safehouses, and completionist extras — with
official 100% tracking kept separate from completionist extras.
## Run
```bash
cd mobile
npm install    # or: bun install / yarn / pnpm
npx expo start
```
Then scan the QR code with **Expo Go** on your iPhone or iPad. Rotate an
iPad to landscape to get the split master/detail layout; on iPhone the
same screens fall back to stacked navigation with a bottom tab bar.
## What's included
- **Expo Go compatible only** — no custom native modules. Uses
  `@react-navigation/native` + native-stack + bottom-tabs,
  `react-native-safe-area-context`, `react-native-screens`,
  `react-native-gesture-handler`, `@react-native-async-storage/async-storage`,
  `expo-clipboard`, `expo-sharing`, `expo-linking`.
- **Progress store** in `src/lib/progress.ts` (Zustand + AsyncStorage) with
  per-item done / pinned / notes / checklist steps.
- **Import / Export** as JSON via clipboard and native Share sheet.
- **Data-first architecture** in `src/data/` — replace the seeded padding
  with the full dataset later; the store, rollups, and UI are already wired
  to the official-vs-extras split via `isRequiredForOfficial100` and
  `isCompletionistExtra`.
- **Map screen** uses `expo-linking` to open the IGN / Fandom interactive
  maps in the system browser instead of embedding fragile iframes.
## File layout
```
mobile/
  App.tsx
  index.ts
  app.json
  package.json
  tsconfig.json
  babel.config.js
  src/
    navigation/RootNavigator.tsx
    screens/
      DashboardScreen.tsx
      CategoryScreen.tsx
      DetailScreen.tsx
      MapScreen.tsx
      SettingsScreen.tsx
    components/
      CategoryCard.tsx
      TrackableRow.tsx
      DetailPanel.tsx
      ProgressBar.tsx
    data/
      types.ts
      categories.ts
      seed.ts
    lib/
      progress.ts
      useIsTablet.ts
    theme/theme.ts
```
## Seeded counts (aligned with IGN 100% checklist)
| Category    | Official | Extras |
|-------------|----------|--------|
| Story       | 57       | 0      |
| Strangers   | 18       | 1      |
| Challenges  | 4 chains | 2      |
| Bounties    | 20       | 0      |
| Jobs        | 5        | 0      |
| Hideouts    | 7        | 1      |
| Minigames   | 6        | 0      |
| Locations   | 94       | 0      |
| Outfits     | 9        | 3      |
| Weapons     | 5        | 5      |
| Safehouses  | 13       | 0      |
| Collectibles| 0        | 15     |
