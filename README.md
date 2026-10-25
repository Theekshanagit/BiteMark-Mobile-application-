# BiteMark 🍔📍

**BiteMark** is a cross-platform social food review mobile application built with Flutter and Dart. It allows food enthusiasts to discover, document, and share their dining experiences with real-time updates, community interactions, GPS tagging, and photo uploads.



## ✨ Features

- **🔐 User Authentication:** Secure email/password registration, sign-in, sign-out, and password recovery powered by Firebase Authentication.
- **📸 Food Review Creation:** Post detailed reviews including restaurant name, cuisine type, rating (1–5 stars), visit date, text review, image, and optional GPS location tag.
- **🗺️ Explore & Distance Sorting:** Discover restaurants filtered by cuisine category and automatically sorted by proximity (distance in kilometers from current GPS coordinates).
- **💬 Community Responses:** Reply to reviews with ratings, comments, and dish photos—creating a interactive micro-dialogue per restaurant.
- **⚡ Real-Time Synchronisation:** Live streaming of reviews and responses across devices without requiring manual refreshes using Firebase Realtime Database streams.
- **📱 Adaptive & Responsive UI:**
  - Dynamic switching between portrait layout (bottom navigation bar) and landscape/large screens (side `NavigationRail`).
  - Auto-responsive grid layout (1 to 4 columns based on logical pixel width).
  - Material Design 3 implementation supporting Light and Dark themes optimized for WCAG AA accessibility contrast standards.
- **📍 Native Hardware Integration:** Camera and gallery integration for optimized photo uploads and GPS receiver integration for accurate location tagging.

---

## 🛠️ Tech Stack & Dependencies

| Technology / Package | Role in Application |
| :--- | :--- |
| **Flutter & Dart** | Cross-platform UI toolkit and primary programming language. |
| **Firebase Auth** | User account management, session persistence, and security authentication. |
| **Firebase Realtime Database** | Real-time JSON cloud database streaming review and response feeds. |
| **Cloudinary API** | Cloud media storage hosting uploaded images via unsigned upload presets. |
| **`geolocator`** | GPS location tagging, permission workflows, and distance calculations. |
| **`image_picker`** | Camera capture & photo gallery selection with client-side image compression. |
| **`http`** | Multipart HTTP requests for image uploads to Cloudinary. |

---

## 📂 Project Architecture

The codebase follows a clean layered structure to separate concerns:

```text
lib/
├── models/         # Data models with JSON serialization (ReviewModel, UserResponseModel)
├── services/       # Service layers (AuthService, FirebaseService, StorageService, LocationService, ImageService)
├── screens/        # Primary UI views (FeedScreen, ExploreScreen, AddReviewScreen, ProfileScreen, DetailScreen, LoginScreen)
├── widgets/        # Reusable UI components & custom animations (AnimatedBookmarkButton, AppImage)
└── theme/          # Material Design 3 light/dark color schemes and typography (AppTheme)
```

---

## 🗄️ Database Structure

Data is maintained in a flat JSON architecture within Firebase Realtime Database:

- `/reviews`: Contains review entries keyed by unique push IDs (`userId`, `restaurantName`, `cuisine`, `rating`, `reviewText`, `imageUrl`, `visitDate`, `latitude`, `longitude`, `hasGpsTag`).
- `/responses`: Top-level node containing community replies keyed by unique response ID, referencing parent reviews via `reviewId`.

---

## 🚀 Getting Started

### Prerequisites

- [Flutter SDK](https://docs.flutter.dev/get-started/install) (latest stable release)
- [Dart SDK](https://dart.dev/get-started)
- IDE (VS Code, Android Studio, or IntelliJ) with Flutter plugins
- Firebase project configured for Android, iOS, or Web
- Cloudinary account with an active unsigned upload preset

### Installation & Setup

1. **Clone the Repository:**
   ```bash
   git clone https://github.com/your-username/bitemark.git
   cd bitemark
   ```

2. **Install Dependencies:**
   ```bash
   flutter pub get
   ```

3. **Configure Firebase & Media Storage:**
   - Add your `google-services.json` (Android) or `GoogleService-Info.plist` (iOS) to their respective directories.
   - Configure your Cloudinary cloud name and unsigned upload preset inside `StorageService`.

4. **Run the App:**
   ```bash
   flutter run
   ```

---

## 🧪 Testing & Validation

The application was tested through comprehensive manual functional testing, edge-case testing, and hardware behavior scenario testing:

- **Authentication & Input Validation:** Verified error handling for weak passwords, invalid credentials, and empty inputs.
- **Permission & Hardware Resilience:** Implemented fallback strategies for denied GPS permissions and indoor location timeouts using last-known position coordinates.
- **Accessibility & Dark Theme:** High-contrast dark theme colors (cyan primary `80DEEA`, card background `1E2D38`, coral CTA `FF8066`) ensuring WCAG AA compliance.
- **Adaptive Screen Transitions:** Responsive screen transitions across varying device widths (360px to 1000px+).

---

## 📄 License

This project was developed for educational purposes 
