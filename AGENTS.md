# AGENTS.md
A quick-start guide for working with **Chapter-Annotator**, a monorepo that ships a cross-platform React Native / Expo app (mobile-first) plus an optional web build.

---

## Prerequisites
| Tool | Version | Notes |
|------|---------|-------|
| Node | 18 LTS or newer | |
| pnpm | 8 or newer | `npm i -g pnpm` |
| Expo CLI | latest | `npm i -g expo-cli` |
| Xcode | latest | Needed for iOS simulator & device builds |
| Android Studio | latest | Needed for Android emulator & device builds |

After cloning:

```bash
pnpm install      # installs all workspace deps
```

---

## Local development

```bash
# Start Metro, launch iOS / Android simulator + web preview
pnpm --filter apps/mobile expo start
```

---

## How to run tests

```bash
pnpm test                     # Jest tests across all workspaces
# or scope to one package:
pnpm --filter packages/core test
```

---

## Mobile builds

```bash
# iOS dev build (simulator / connected device)
pnpm --filter apps/mobile expo prebuild
pnpm --filter apps/mobile expo run:ios

# Android dev build (emulator / connected device)
pnpm --filter apps/mobile expo run:android
```

### Cloud (EAS) builds

```bash
# Preview/TestFlight build
pnpm dlx eas build -p ios --profile preview

# Submit to stores
pnpm dlx eas submit -p ios
pnpm dlx eas submit -p android
```

---

## Web build (optional PWA)

```bash
# Static bundle outputs to apps/mobile/dist
pnpm --filter apps/mobile expo export:web
```

---

## Lint & type-check

```bash
pnpm lint         # ESLint
pnpm typecheck    # TypeScript project-references check
```

---

## Format

```bash
pnpm format       # Prettier + eslint --fix
```

---

## Environment variables

Create `apps/mobile/.env` (never commit this file):

```
API_URL=https://api.example.com
```

Add additional secrets as needed.

---

Happy hacking 🎉
