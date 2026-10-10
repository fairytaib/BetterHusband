# Be a better Husband – MVP-Fundament

Expo SDK 52 · TypeScript (strict) · Expo Router · Zustand + verschlüsseltes MMKV · Reanimated

## Start

```bash
npm install
npx expo install --fix          # gleicht Versionen an dein SDK an
cp .env.example .env            # nur für Premium-KI
npx expo prebuild
npx expo run:ios                # oder run:android
```

MMKV v3 braucht die New Architecture und einen Development Build – **Expo Go reicht nicht**.

## Architektur

- `app/` – nur Routen (dünn), delegieren an `src/screens`
- `src/store` – ein Zustand-Store pro Modul, persistiert in MMKV
- `src/services/storage` – MMKV-Instanz, AES-Schlüssel im Keychain/Keystore
- `src/services/media` – Fotos in der App-Sandbox, 3-Monats-Export/-Löschung
- `src/services/ai` – Anonymisierung + Proxy-Aufruf (nur Premium, nur mit Einwilligung)
- `src/components/widgets` – Registry, Smart Stack, Widget-Rahmen
- `proxy/` – Beispiel-Cloudflare-Worker, der die LLM-Keys hält

## Neues Widget hinzufügen

1. Komponente in `src/components/widgets/items/` (nutzt `useWidgetTone()` für Farben)
2. Eintrag in `src/components/widgets/registry.tsx`
3. ID in `WidgetId` (`src/types/models.ts`) und Default in `useDashboardStore.ts`

## Vor dem Release

- Arabische Texte in `src/data/duas.ts` gegenlesen lassen
- Premium-Schalter durch echten Kaufstatus ersetzen (z. B. RevenueCat), Token im Proxy prüfen
- Ab SDK 54: `expo-file-system` → `expo-file-system/legacy` in `mediaService.ts`
"# BetterHusband" 
"# BetterHusband" 
