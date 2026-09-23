# *FilmRoulette* - Android Movie Discovery App

![Kotlin](https://img.shields.io/badge/Kotlin-2.1-7F52FF?logo=kotlin&logoColor=white)
![Jetpack Compose](https://img.shields.io/badge/Jetpack%20Compose-Material%203-4285F4?logo=jetpackcompose&logoColor=white)
![Firebase](https://img.shields.io/badge/Firebase-Auth%20%2B%20Firestore-FFCA28?logo=firebase&logoColor=black)
![Room](https://img.shields.io/badge/Room-local%20persistence-3DDC84?logo=android&logoColor=white)
![minSdk](https://img.shields.io/badge/minSdk-24-blue)

*Deciding what to watch, alone or with friends.* **FilmRoulette** is a Jetpack Compose Android app that turns movie picking into a swipeable deck. Filter by what you feel like, swipe through TMDB-backed suggestions, or open a group session where everyone swipes the same deck until a film matches for all of them.

Around $10,800$ lines of Kotlin across $81$ files, built on MVVM with repository interfaces, Room for local persistence, Firestore for shared state, and a pluggable AI assistant.

> Academic project - Mobile Application Development (*Desenvolvimento de Aplicações Móveis*), BSc in Computer Science and Multimedia Engineering (LEIM), ISEL. 

The repository also holds the four course tutorials that preceded it.

---

## Features

| Screen | What it does |
| :-- | :-- |
| **Roulette** | A deck of recommendations from TMDB. Already-seen films are marked to avoid reapearance. |
| **Filters** | Genres, maximum runtime, streaming platforms, languages and release decades. |
| **Groups** | A host opens a session; members join and swipe a shared deck under shared filters. Right-swipes are collected per member and the session resolves to a match. |
| **Watchlist** | Personal lists with visibility configurations. |
| **AI Guide** | Natural-language recommendations. Describe the current mood and the agent recomends accordingly. |
| **Profile** / **Settings** | Friendships, account, and the app's configurable options. |
| **Login** / **Register** | Firebase Authentication. |

## Architecture
```
data/
├── local/        # Room entities, DAOs, type converters, cross-reference tables
├── model/        # domain models
├── remote/
│   ├── api/      # TMDB via Retrofit
│   ├── dto/      # wire format
│   └── ai/       # AI assistant 
├── repository/   # interfaces + implementations
└── utils/        # mappers between DTO, domain and entity
ui/
├── screens/      # one package per screen
├── navigation/   # sealed Screen hierarchy + nav graph
├── components/   # shared composables
└── theme/        # colour schemes
```
## Stack

| Layer | Technology |
| :-- | :-- |
| Language | Kotlin 2.1.21, coroutines + Flow |
| UI | Jetpack Compose (BOM 2025.05), Material 3, Navigation Compose, Coil |
| Local data | Room 2.7.1 with KSP, DataStore |
| Remote data | Retrofit 2.11 + OkHttp 4.12, TMDB API |
| Backend | Firebase Authentication, Cloud Firestore |
| AI | Google Gemini / NVIDIA NIM, behind one interface |
| Build | Gradle KTS, version catalog, AGP 9.1 · minSdk 24 · targetSdk 35 |

## Build

The app needs credentials that are deliberately not in the repository.

1. Create `projeto/local.properties` (untracked) with your own keys:

   ```properties
   sdk.dir=/path/to/Android/sdk
   TMDB_API_KEY="your_tmdb_key"
   NIM_API_KEY="your_nim_key"
   ```

2. Add your own `projeto/app/google-services.json` from a Firebase project with Authentication and Firestore enabled.

3. Open `projeto/` in Android Studio and run on a device or emulator with API 24 or higher.

## Course Tutorials

The four tutorials leading up to the project, each with its own README (PT-PT <img src="https://flagcdn.com/16x12/pt.png" alt="PT" width="16">):

| | Topic | Apps |
| :-- | :-- | :-- |
| [Tutorial 1](tutorial-1/) | Kotlin fundamentals, first Android apps | `Hello World`, `System Info`, `Weather Buddy` |
| [Tutorial 2](tutorial-2/) | Generics, sealed classes, higher-order functions, MVVM, REST | `Cool Weather App`, `Mission Impossible 2` |
| [Tutorial 3](tutorial-3/) | Jetpack Compose | `Cool Jetpack Weather App` |
| [Tutorial 4](tutorial-4/) | Room persistence, Firestore, RecyclerView, chat | `NotesPro`, `FriendlyChat` |

## Author

Bruno Pereira (51811) - *Mobile Application Development*, ISEL - DEI, 2025/26.
