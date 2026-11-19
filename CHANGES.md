# Remaining small edits (apply in Metis UI repo)

## 1. `src/features/notifications/services/notificationService.ts`

In `syncAllEventReminders`, change default from false to true:

```ts
// BEFORE
const enabled = settingsStorage.getBoolean(EVENT_REMINDERS_KEY) ?? false;

// AFTER
const enabled = settingsStorage.getBoolean(EVENT_REMINDERS_KEY) ?? true;
```

## 2. `src/features/more/screens/SettingsScreen.tsx`

### Import
```ts
import { setEventReminderPreference, getEffectiveRemindersEnabled } from "@/features/notifications/services/pushRegistrationService";
```

### On mount (replace saved ?? true)
```ts
setEventRemindersEnabled(getEffectiveRemindersEnabled());
```

### Subtitle under Event reminders
```tsx
Campus events (10 min before) and new announcements
```

Note: the Notifications section already exists in current Metis master under More → Settings.
If it is missing on Play Store, the installed binary is older than that commit — ship a new build/OTA.
