# Floofbit

## What it does
A virtual pet companion that lives on your phone, follows you through real-world activities, and grows based on how active you are together.

## Who it's for
Pet lovers who want a tamagotchi-like experience tied to real-world movement and activity tracking. People who may or may not own a real pet.

## Core concept
You create or adopt a virtual pet — either from scratch with customisation, or by uploading a photo of your real pet to generate an avatar. Your pet has needs (hunger, happiness, energy) that respond to your real-world activity. Walk in real life, your pet walks with you. Stay idle, your pet gets bored. The more active you are, the more your pet thrives and unlocks new looks, accessories, and environments.

---

## Screens

### 1. Onboarding
- Welcome flow (2-3 screens max)
- Choose: "Create a pet" or "Make one from my photo"
- Name your pet

### 2. Home screen
- Your pet displayed with current mood/state
- Key stats visible (happiness, energy, hunger)
- Quick access to feed, play, customise
- Activity summary for today (steps, distance)

### 3. Pet customisation
- Choose species/breed (cat, dog, bunny, fantasy creature)
- Colour, pattern, accessories
- Photo-based avatar generation (later milestone)

### 4. Activity view
- Current activity status (idle, walking, running)
- Today's activity log
- Pet's reaction to activity (animations, mood changes)
- Weekly activity history

### 5. Pet profile / journal
- Pet's name, age (days since creation), level
- Unlocked items and achievements
- Activity milestones

### 6. Settings
- Notifications (reminders to check on pet)
- Health permissions
- App preferences

---

## Data

### Stored locally (SwiftData)
- Pet profile (name, species, appearance, creation date)
- Pet state (hunger, happiness, energy, level, XP)
- Activity history (daily steps, distance, active minutes)
- Unlocked items and achievements
- User preferences

### From system APIs
- HealthKit: step count, distance, active energy
- Core Motion: real-time movement detection (walking, running, stationary)

### No server needed for v1
- All data local to device
- Photo-based avatar generation can use on-device ML (Core ML / Vision)

---

## Features by priority

### Must have (v1.0 — Minimum Lovable Product)
1. Create a pet with basic customisation (name, species, colour)
2. Home screen showing pet with mood/state
3. Pet needs system (happiness, hunger, energy) that decay over time
4. Feed and play interactions that affect pet state
5. Step tracking via HealthKit
6. Pet mood responds to real activity (more steps = happier pet)
7. Simple animations for pet states (happy, hungry, sleepy, excited)
8. Local data persistence with SwiftData

### Should have (v1.1)
9. Activity view with daily/weekly history
10. Pet levelling system (XP from steps and interactions)
11. Unlock accessories/cosmetics at level milestones
12. Notifications ("Your pet is hungry!", "Great walk today!")
13. Pet journal / milestone log
14. Widget showing pet on home screen (WidgetKit)

### Nice to have (v2.0)
15. Photo-based avatar generation (upload photo → stylised pet avatar)
16. Live Activity on lock screen during walks (ActivityKit)
17. Apple Watch companion (see pet on wrist, track activity)
18. Multiple pets
19. Seasonal events / limited cosmetics
20. Social: share pet screenshots

---

## Build phases (learning progression)

Each phase teaches specific iOS concepts. Complete one before starting the next.

### Phase 1 — Hello Pet
**Goal:** Display a pet on screen with a name.
**Learn:** SwiftUI basics, views, @State, images, text, navigation.
**Deliver:** App launches, shows a pet image and name. Tap to change mood.

### Phase 2 — Pet needs
**Goal:** Pet has hunger, happiness, energy that change over time.
**Learn:** @Observable, timers, data modelling, computed properties.
**Deliver:** Stats bars on screen. They decay. Buttons to feed/play restore them.

### Phase 3 — Persistence
**Goal:** Pet state survives app restart.
**Learn:** SwiftData, @Model, modelContainer, modelContext.
**Deliver:** Close app, reopen, pet remembers its state and name.

### Phase 4 — Customisation
**Goal:** Choose species, colour, accessories at creation.
**Learn:** Navigation flows, forms, pickers, passing data between views.
**Deliver:** Onboarding flow → customise → home screen with chosen pet.

### Phase 5 — Step tracking
**Goal:** Read step count from HealthKit, display on activity view.
**Learn:** HealthKit setup, permissions, async/await, background data.
**Deliver:** Activity view shows today's steps. Pet reacts to step count.

### Phase 6 — Animations and polish
**Goal:** Pet feels alive.
**Learn:** SwiftUI animations, transitions, gestures.
**Deliver:** Pet bounces, blinks, reacts to taps and activity changes.

### Phase 7 — Notifications and widgets
**Goal:** Pet reminds you it exists even when app is closed.
**Learn:** UserNotifications, WidgetKit, app extensions.
**Deliver:** Push reminders. Home screen widget showing pet.

### Phase 8 — Live Activity (stretch)
**Goal:** Pet appears on lock screen during walks.
**Learn:** ActivityKit, Live Activities, Dynamic Island.
**Deliver:** Start a walk → pet appears on lock screen with live step count.

### Phase 9 — Photo avatar (stretch)
**Goal:** Upload pet photo, generate stylised avatar.
**Learn:** PhotosUI, Vision framework, Core ML, on-device image processing.
**Deliver:** Photo picker → processed/stylised version becomes pet avatar.

---

## Architecture (keep it simple)

```
Floofbit/
├── FloofbitApp.swift          # App entry point
├── Models/
│   ├── Pet.swift              # Pet data model (SwiftData)
│   ├── ActivityRecord.swift   # Daily activity data
│   └── PetState.swift         # Current mood/needs
├── Views/
│   ├── HomeView.swift         # Main pet display
│   ├── OnboardingView.swift   # Pet creation flow
│   ├── CustomiseView.swift    # Appearance editor
│   ├── ActivityView.swift     # Step/activity tracking
│   └── ProfileView.swift      # Pet journal/achievements
├── Services/
│   ├── HealthService.swift    # HealthKit integration
│   ├── PetEngine.swift        # Needs decay, levelling logic
│   └── NotificationService.swift
├── Components/
│   ├── PetView.swift          # Reusable pet display component
│   ├── StatBar.swift          # Hunger/happiness/energy bar
│   └── ActionButton.swift     # Feed/play buttons
├── Assets.xcassets/           # Pet sprites, icons, colours
└── Extensions/                # Helper extensions
```

---

## Tech stack
- **Language:** Swift
- **UI:** SwiftUI
- **Data:** SwiftData
- **Activity:** HealthKit, Core Motion
- **Notifications:** UserNotifications
- **Widgets:** WidgetKit
- **Live Activity:** ActivityKit
- **Image processing:** Vision, Core ML (later phases)
- **Target:** iOS 17+
- **Min device:** iPhone (iPad as bonus)

---

## What I don't know yet
- What art style for the pets? (pixel art, cartoon, 3D-ish)
- How to create/source pet sprite assets
- How complex should the needs decay formula be?
- Is on-device photo-to-avatar feasible without a server?
- How does WidgetKit actually update with live data?
- Can Live Activities show custom pet graphics?

---

## Working title
**Floofbit** — your fluffy fitness companion.

## Tagline ideas
- "Step together."
- "Your pet. Your pace."
- "Get active. Keep it fluffy."
