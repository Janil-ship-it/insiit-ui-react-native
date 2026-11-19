# INSIIT notification permission + 10-min reminders (frontend)

Patches against Metis-IITGandhinagar/insiit-ui-react-native master.

## Behaviour

1. After @iitgn.ac.in login, when Home first opens, the app requests notification permission (if not granted and the OS still allows the dialog).
2. First install, reinstall, and existing installs that open Home while signed in all hit this path.
3. If permission is granted, Event reminders defaults to ON unless the user has already turned the switch off in Settings.
4. Settings → Notifications shows the 10-min toggle (label: campus events + announcements).

## Files to copy into the Metis UI repo

- src/features/notifications/services/pushRegistrationService.ts
- src/features/home/screens/HomeScreen.tsx
- src/features/more/screens/SettingsScreen.tsx
- src/features/notifications/services/notificationService.ts (only change: syncAllEventReminders default ?? true)

Then ship a new Play Store / OTA build — the Play Store binary does not pick these up automatically.
