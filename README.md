# QuickMove Flutter App

A Flutter mobile app for the QuickMove ride-sharing platform. This app connects to the existing Express.js backend.

## Project Structure

```
flutter_app/
├── lib/
│   ├── main.dart                 # App entry point
│   ├── models/                   # Data models
│   │   ├── user.dart            # User model
│   │   ├── ride.dart            # Ride model
│   │   └── message.dart         # Message & Notification models
│   ├── providers/               # State management
│   │   ├── auth_provider.dart   # Authentication state
│   │   ├── ride_provider.dart   # Ride booking state
│   │   └── location_provider.dart # Location services
│   ├── services/                # API services
│   │   ├── api_service.dart     # HTTP client
│   │   ├── auth_service.dart    # Auth API calls
│   │   └── ride_service.dart    # Ride API calls
│   ├── screens/                 # UI screens
│   │   ├── splash_screen.dart
│   │   ├── auth/
│   │   │   ├── login_screen.dart
│   │   │   └── register_screen.dart
│   │   ├── customer/
│   │   │   └── customer_dashboard.dart
│   │   └── driver/
│   │       └── driver_dashboard.dart
│   ├── widgets/                 # Reusable widgets
│   │   ├── vehicle_selector.dart
│   │   ├── location_input.dart
│   │   ├── fare_slider.dart
│   │   ├── ride_card.dart
│   │   └── ride_request_card.dart
│   └── utils/                   # Utilities
│       ├── theme.dart           # App theme
│       └── constants.dart       # API constants
└── pubspec.yaml                 # Dependencies
```

## Setup Instructions

### 1. Prerequisites

- Flutter SDK (3.0.0 or higher)
- Android Studio or VS Code with Flutter extensions
- Xcode (for iOS development on macOS)

### 2. Install Flutter

Follow the official Flutter installation guide:
https://docs.flutter.dev/get-started/install

### 3. Configure Backend URL

Update the API base URL in `lib/utils/constants.dart`:

```dart
class ApiConstants {
  static const String baseUrl = 'https://your-replit-app.replit.app';
  static const String wsUrl = 'wss://your-replit-app.replit.app';
  // ...
}
```

### 4. Install Dependencies

```bash
cd flutter_app
flutter pub get
```

### 5. Run the App

```bash
# For Android
flutter run

# For iOS
flutter run -d ios

# For web (development)
flutter run -d chrome
```

## Features

### Customer Features
- User registration and login
- Set pickup and dropoff locations
- Select vehicle type (Bike, Mini, Sedan, SUV, Truck)
- Set custom fare (inDrive-style bidding)
- Multiple payment methods
- View ride history
- Rate completed rides
- Profile management

### Driver Features
- Go online/offline toggle
- View available ride requests
- Accept/decline rides
- Track earnings
- Complete rides
- Profile and vehicle management

## Key Dependencies

- **provider** - State management
- **http** / **dio** - HTTP networking
- **flutter_secure_storage** - Secure token storage
- **google_maps_flutter** - Maps integration
- **geolocator** - Location services
- **flutter_rating_bar** - Rating UI

## Adding Google Maps

1. Get a Google Maps API key from the Google Cloud Console
2. Add to Android: `android/app/src/main/AndroidManifest.xml`
   ```xml
   <meta-data
       android:name="com.google.android.geo.API_KEY"
       android:value="YOUR_API_KEY"/>
   ```
3. Add to iOS: `ios/Runner/AppDelegate.swift`
   ```swift
   GMSServices.provideAPIKey("YOUR_API_KEY")
   ```

## Demo Credentials

- **Customer:** customer@quickmove.pk / password123
- **Driver:** driver@quickmove.pk / password123

## Building for Release

### Android
```bash
flutter build apk --release
# or for app bundle
flutter build appbundle --release
```

### iOS
```bash
flutter build ios --release
```

## Notes

- This Flutter app uses the same backend as the web app
- Both apps can run simultaneously sharing the same database
- WebSocket connections are used for real-time updates
