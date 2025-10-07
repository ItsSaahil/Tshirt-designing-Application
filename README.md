# Design Your T-shirt 👕

A modern Android application built with Kotlin and Jetpack Compose that allows users to design custom T-shirts with an intuitive interface. The app features Firebase authentication, real-time database integration, and a rich design toolkit for creating personalized apparel.

## 📱 Features

- **Custom T-shirt Design**: Interactive design canvas for creating unique T-shirt designs
- **User Authentication**: Secure login/signup with Firebase Authentication and Google Sign-In
- **Real-time Database**: Store and sync designs with Firebase Realtime Database
- **Material Design 3**: Modern and intuitive user interface
- **Design Tools**: Rich set of tools for customizing T-shirt designs
- **Image Integration**: Support for adding custom images and graphics
- **Design Gallery**: Browse and manage your saved designs
- **Responsive UI**: Optimized for different screen sizes

## 🛠️ Tech Stack

- **Language**: Kotlin
- **UI Framework**: Jetpack Compose
- **Architecture**: MVVM with Dagger Hilt
- **Authentication**: Firebase Auth + Google Sign-In
- **Database**: Firebase Realtime Database
- **Dependency Injection**: Dagger Hilt
- **Navigation**: Navigation Compose
- **Image Loading**: Coil
- **Design System**: Material Design 3
- **Min SDK**: 24 (Android 7.0)
- **Target SDK**: 34
- **Compile SDK**: 35

## 📋 Prerequisites

Before running this application, make sure you have:

- Android Studio (Latest version recommended)
- JDK 11 or higher
- An Android device or emulator with API level 24+
- Firebase project setup
- Google Services configuration

## 🚀 Installation & Setup

### 1. Clone the Repository
```bash
git clone https://github.com/Shivamtawar/Design_your_Tshirt.git
cd Design_your_Tshirt
```

### 2. Firebase Setup
1. Create a new Firebase project at [Firebase Console](https://console.firebase.google.com/)
2. Enable Authentication and Realtime Database
3. Download `google-services.json` file
4. Place it in the `app/` directory

### 3. Configure Firebase Authentication
1. In Firebase Console, go to Authentication → Sign-in method
2. Enable Email/Password and Google sign-in providers
3. For Google Sign-In, add your app's SHA-1 fingerprint

### 4. Google Sign-In Configuration
1. Go to Google Cloud Console
2. Create credentials for your Android app
3. Add the Web client ID to your Firebase project

### 5. Build and Run
1. Open the project in Android Studio
2. Sync Gradle files
3. Build and run on your device/emulator

## 🏗️ Project Structure

```
app/
├── src/
│   ├── main/
│   │   ├── java/com/example/designyourt_shirt/
│   │   │   ├── ui/
│   │   │   │   ├── auth/                # Authentication screens
│   │   │   │   ├── design/              # Design canvas and tools
│   │   │   │   ├── gallery/             # Design gallery
│   │   │   │   ├── profile/             # User profile
│   │   │   │   └── theme/               # App theme and styling
│   │   │   ├── data/
│   │   │   │   ├── repository/          # Data repositories
│   │   │   │   ├── remote/              # Firebase data sources
│   │   │   │   └── model/               # Data models
│   │   │   ├── di/                      # Dependency injection modules
│   │   │   ├── navigation/              # Navigation setup
│   │   │   ├── utils/                   # Utility classes
│   │   │   └── MainActivity.kt          # Main activity
│   │   ├── res/
│   │   │   ├── values/                  # App resources
│   │   │   ├── drawable/                # Images and icons
│   │   │   └── layout/                  # Layout files (if any)
│   │   └── AndroidManifest.xml
│   ├── androidTest/                     # Instrumented tests
│   └── test/                            # Unit tests
├── build.gradle.kts                     # App-level Gradle build file
└── google-services.json                 # Firebase configuration
```

## 🎨 Key Features

### Design Canvas
- Interactive T-shirt design interface
- Drag and drop design elements
- Text customization (fonts, colors, sizes)
- Shape and graphic tools
- Layer management
- Undo/Redo functionality

### Authentication System
- Email/Password registration and login
- Google Sign-In integration
- User profile management
- Secure session handling

### Design Management
- Save designs to Firebase
- Load previous designs
- Share designs with others
- Export designs as images

## 🔧 Key Dependencies

```kotlin
// Core Android libraries
implementation("androidx.core:core-ktx")
implementation("androidx.lifecycle:lifecycle-runtime-ktx")
implementation("androidx.activity:activity-compose")

// Jetpack Compose
implementation(platform("androidx.compose:compose-bom"))
implementation("androidx.compose.ui:ui")
implementation("androidx.compose.material3:material3")
implementation("androidx.compose.material:material-icons-extended")

// Navigation
implementation("androidx.navigation:navigation-compose")

// Firebase
implementation("com.google.firebase:firebase-auth")
implementation("com.google.firebase:firebase-database-ktx")

// Authentication
implementation("androidx.credentials:credentials")
implementation("androidx.credentials:credentials-play-services-auth")
implementation("com.google.android.libraries.identity.googleid:googleid")

// Dependency Injection
implementation("com.google.dagger:hilt-android")
implementation("androidx.hilt:hilt-navigation-compose")

// Image Loading
implementation("io.coil-kt:coil-compose")
```

## 🔐 Firebase Configuration

### Database Structure
```json
{
  "users": {
    "userId": {
      "email": "user@example.com",
      "displayName": "User Name",
      "profilePicture": "url_to_image"
    }
  },
  "designs": {
    "designId": {
      "userId": "user_id",
      "title": "My Design",
      "designData": "serialized_design_data",
      "thumbnail": "thumbnail_url",
      "createdAt": "timestamp",
      "updatedAt": "timestamp"
    }
  }
}
```

### Security Rules
```javascript
{
  "rules": {
    "users": {
      "$uid": {
        ".read": "$uid === auth.uid",
        ".write": "$uid === auth.uid"
      }
    },
    "designs": {
      ".read": "auth != null",
      ".write": "auth != null",
      "$designId": {
        ".validate": "newData.child('userId').val() === auth.uid"
      }
    }
  }
}
```

## 🎯 App Flow

### 1. Authentication Flow
- Splash screen with app branding
- Login/Register options
- Google Sign-In or Email/Password
- Profile setup for new users

### 2. Design Flow
- Main dashboard with design options
- T-shirt template selection
- Design canvas with tools
- Save and preview functionality

### 3. Gallery Flow
- Browse saved designs
- Edit existing designs
- Share or delete designs
- Search and filter options

## 🧪 Testing

### Running Tests
```bash
# Run unit tests
./gradlew test

# Run instrumented tests
./gradlew connectedAndroidTest

# Run all tests with coverage
./gradlew jacocoTestReport
```

### Test Coverage
- Unit tests for ViewModels and repositories
- UI tests for critical user flows
- Integration tests for Firebase operations

## 📱 Supported Features

### Design Tools
- **Text Tool**: Add customizable text with various fonts
- **Shape Tool**: Insert geometric shapes and patterns
- **Image Tool**: Upload and manipulate custom images
- **Color Picker**: Full color palette for all elements
- **Transform Tool**: Resize, rotate, and position elements

### Export Options
- High-resolution PNG export
- PDF format for printing
- Share directly to social media
- Email design attachments

## 🔧 Configuration

### Build Variants
```kotlin
android {
    buildTypes {
        debug {
            applicationIdSuffix = ".debug"
            isDebuggable = true
        }
        release {
            isMinifyEnabled = true
            proguardFiles(getDefaultProguardFile("proguard-android-optimize.txt"))
        }
    }
}
```

### Permissions
```xml
<uses-permission android:name="android.permission.INTERNET" />
<uses-permission android:name="android.permission.READ_EXTERNAL_STORAGE" />
<uses-permission android:name="android.permission.CAMERA" />
```

## 🚦 Error Handling

The app includes comprehensive error handling for:
- Network connectivity issues
- Firebase authentication errors
- Database operation failures
- File upload/download errors
- Invalid design data

## 🎨 Design Patterns

- **MVVM Architecture**: Clear separation of concerns
- **Repository Pattern**: Centralized data management
- **Dependency Injection**: Improved testability and modularity
- **State Management**: Reactive UI updates with StateFlow

## 🐛 Troubleshooting

### Common Issues

1. **Firebase Authentication fails**
   - Check google-services.json placement
   - Verify SHA-1 fingerprint in Firebase Console
   - Ensure correct client ID configuration

2. **Database permission denied**
   - Review Firebase Security Rules
   - Check user authentication status
   - Verify user permissions

3. **Google Sign-In not working**
   - Confirm Web client ID in Firebase
   - Check Google Cloud Console credentials
   - Verify package name and SHA-1

### Debug Tips
- Enable Firebase debug logging
- Use Android Studio's Network Inspector
- Check Logcat for detailed error messages
- Test on different devices and Android versions

## 📄 License

This project is open source and available under the [MIT License](LICENSE).

## 🤝 Contributing

Contributions are welcome! Please follow these guidelines:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/AmazingFeature`)
3. Follow Kotlin coding conventions and Material Design guidelines
4. Write tests for new features
5. Update documentation as needed
6. Commit your changes (`git commit -m 'Add some AmazingFeature'`)
7. Push to the branch (`git push origin feature/AmazingFeature`)
8. Open a Pull Request

## 📞 Support

If you encounter any issues:
1. Check the [Issues](https://github.com/Shivamtawar/Design_your_Tshirt/issues) section
2. Create a new issue with detailed information
3. Contact: [@Shivamtawar](https://github.com/Shivamtawar)

## 🔮 Future Enhancements

- [ ] AI-powered design suggestions
- [ ] 3D T-shirt preview
- [ ] Collaborative design editing
- [ ] Design marketplace integration
- [ ] Print-on-demand service integration
- [ ] Augmented reality try-on
- [ ] Design templates library
- [ ] Vector graphics support
- [ ] Animation and effects
- [ ] Multi-language support

## 🏆 Acknowledgments

- Firebase team for backend services
- Jetpack Compose community
- Material Design guidelines
- Open source contributors

---

**Made with ❤️ by [Shivam Tawar](https://github.com/Shivamtawar)**

*Design Your Style, Wear Your Creativity! 🎨*
