# 🌦️ Sassy Skies

<div align="center">
  
**The Weather App with Attitude**

*Because regular weather apps are boring, and the weather deserves to be roasted properly.*

[![Android](https://img.shields.io/badge/Platform-Android-green.svg)](https://android.com)
[![Kotlin](https://img.shields.io/badge/Language-Kotlin-purple.svg)](https://kotlinlang.org)
[![API](https://img.shields.io/badge/Min%20SDK-24-orange.svg)](https://developer.android.com)
[![License](https://img.shields.io/badge/License-MIT-blue.svg)](LICENSE)

[Features](#-features) • [Tech Stack](#️-tech-stack) • [Setup](#-getting-started) • [Architecture](#-architecture) • [Contributing](#-contributing)

</div>

---

## 📖 About

Sassy Skies is an Android weather app that delivers weather information with personality. Using AI-powered sarcastic commentary, it transforms mundane weather updates into entertaining roasts that'll make you laugh while you check if you need an umbrella.

### 🎯 Why Sassy Skies?

- **Boring weather apps?** Not anymore! 
- **Generic forecasts?** We serve them with extra sass
- **Predictable UI?** Our weather icons have attitude
- **One-size-fits-all humor?** Choose between Global sass or Desi tadka!

---

## ✨ Features

### 🤖 **AI-Powered Sarcasm**
- **Global Mode**: International sarcasm with no boundaries
- **Desi Mode**: Indian humor with local slang and memes
- Powered by Google's Gemini AI for dynamic, contextual roasts

### 🌍 **Comprehensive Weather Data**
- Real-time weather conditions
- 7-day detailed forecasts
- Location-based automatic updates
- Detailed atmospheric conditions (humidity, pressure, wind, visibility)

### 🎨 **Modern UI/UX**
- **Material 3 Design** with dynamic theming
- **Animated Weather Icons** that react to conditions
- **Responsive Layout** that adapts to content length
- **Smooth Animations** and transitions throughout

### 🔐 **Privacy-First Approach**
- **Personal API Keys**: Use your own weather and AI API keys
- **Secure Storage**: Firebase Realtime Database with user authentication
- **No Data Mining**: Your weather preferences stay yours

### 📱 **Smart Features**
- **Auto-location Detection** with GPS integration
- **Offline Fallbacks** when APIs are unavailable
- **Dynamic Font Sizing** based on message length
- **Pull-to-refresh** for instant updates

---

## 🛠️ Tech Stack

### **Frontend**
- **Language**: Kotlin
- **UI Framework**: Jetpack Compose
- **Design System**: Material 3
- **Navigation**: Navigation Compose

### **Architecture**
- **Pattern**: MVVM + Clean Architecture
- **DI**: Hilt (Dagger)
- **Reactive**: StateFlow + Coroutines
- **State Management**: Compose State

### **Backend & APIs**
- **Authentication**: Firebase Auth
- **Database**: Firebase Realtime Database
- **Weather API**: OpenWeatherMap
- **AI Service**: Google AI (Gemini)

### **Libraries & Tools**
```kotlin
// Core
implementation ("androidx.core:core-ktx:1.12.0")
implementation ("androidx.lifecycle:lifecycle-runtime-ktx:2.7.0")
implementation ("androidx.activity:activity-compose:1.8.2")

// Compose
implementation platform("androidx.compose:compose-bom:2024.02.00")
implementation ("androidx.compose.ui:ui")
implementation ("androidx.compose.material3:material3"
implementation ("androidx.navigation:navigation-compose:2.7.6")

// Architecture
implementation "androidx.lifecycle:lifecycle-viewmodel-compose:2.7.0"
implementation "androidx.hilt:hilt-navigation-compose:1.1.0"
implementation "com.google.dagger:hilt-android:2.48"

// Network
implementation "com.squareup.retrofit2:retrofit:2.9.0"
implementation "com.squareup.retrofit2:converter-gson:2.9.0"

// Firebase
implementation "com.google.firebase:firebase-auth:22.3.1"
implementation "com.google.firebase:firebase-database:20.3.0"

// AI & Image Loading
implementation "com.google.ai.client.generativeai:generativeai:0.2.2"
implementation "io.coil-kt:coil-compose:2.5.0"
implementation "io.coil-kt:coil-svg:2.5.0"

// Location
implementation "com.google.android.gms:play-services-location:21.0.1"
```

---

## 🚀 Getting Started

### Prerequisites
- Android Studio Hedgehog or newer
- Android SDK 24+ (Android 7.0)
- Google Services JSON file
- API Keys (see setup below)

### 🔧 Installation

1. **Clone the repository**
   ```bash
   git clone https://github.com/yourusername/sassy-skies.git
   cd sassy-skies
   ```

2. **Open in Android Studio**
   - Import the project
   - Let Gradle sync complete

3. **Setup Firebase**
   - Create a new Firebase project
   - Add your Android app to Firebase
   - Download `google-services.json`
   - Place it in `app/` directory

4. **Configure API Keys** (Required)
   
   You'll need to obtain these free API keys:
   
   **🌤️ OpenWeatherMap API**
   - Visit [OpenWeatherMap](https://openweathermap.org/api)
   - Create free account
   - Generate API key
   
   **🤖 Google AI (Gemini) API**
   - Visit [Google AI Studio](https://aistudio.google.com/app/apikey)
   - Create API key
   - Enable Gemini API

5. **Build and Run**
   ```bash
   ./gradlew assembleDebug
   ```

### 🔐 First Run Setup

1. **Create Account**: Sign up with email/password
2. **Verify Email**: Check your inbox for verification
3. **Add API Keys**: Enter your OpenWeatherMap and Gemini API keys
4. **Grant Location**: Allow location access for local weather
5. **Choose Your Sass**: Select Global or Desi humor style

---

## 🏗️ Architecture

### **Project Structure**
```
app/src/main/java/com/hritwik/sassyskies/
├── 📁 core/                 # Navigation & App-level components
├── 📁 di/                   # Dependency Injection modules
├── 📁 model/                # Data models & UI state
│   ├── 📁 auth/             # Authentication models
│   ├── 📁 weather/          # Weather data models
│   └── 📁 uistate/          # UI state management
├── 📁 repository/           # Data layer interfaces
├── 📁 repositoryImpl/       # Repository implementations
├── 📁 screen/               # UI screens & components
│   ├── 📁 auth/             # Authentication screens
│   ├── 📁 weather/          # Weather-related screens
│   └── 📁 components/       # Reusable UI components
├── 📁 service/              # External API services
├── 📁 ui/theme/             # App theming & typography
└── 📁 viewmodel/            # Business logic & state
```

### **Data Flow**
```
UI Layer (Compose) 
    ↕ 
ViewModel (StateFlow) 
    ↕ 
Repository (Interface) 
    ↕ 
Service/API (Implementation)
```

### **Key Components**

- **🔐 AuthRepository**: Manages Firebase authentication and user data
- **🌤️ WeatherRepository**: Handles OpenWeatherMap API calls
- **🤖 GeminiService**: Generates AI-powered sarcastic commentary
- **📍 LocationRepository**: GPS location services with fallbacks
- **🔑 ApiKeyRepository**: Secure user API key management

---

## 🎨 Design Philosophy

### **User Experience**
- **Humor First**: Weather info delivered with personality
- **Privacy Focused**: User controls their own API keys
- **Culturally Aware**: Localized humor that resonates
- **Performance Optimized**: Smooth animations, fast loading

### **Technical Principles**
- **Clean Architecture**: Separation of concerns
- **Reactive Programming**: StateFlow for UI updates
- **Error Handling**: Graceful fallbacks and user feedback
- **Testing Ready**: Dependency injection for easy testing

---

## 📊 Features Breakdown

### **Weather Intelligence**
- ✅ Current conditions with real-time updates
- ✅ 7-day forecast with daily summaries
- ✅ Detailed atmospheric data
- ✅ Location-based automatic detection
- ✅ Sunrise/sunset times
- ✅ Weather-specific animated icons

### **AI Commentary Engine**
- ✅ Context-aware sarcastic messages
- ✅ Two distinct humor styles (Global/Desi)
- ✅ Dynamic content based on weather conditions
- ✅ Fallback messages when AI is unavailable
- ✅ Message length optimization for readability

### **User Experience**
- ✅ Material 3 design with dynamic colors
- ✅ Smooth animations and transitions
- ✅ Responsive layouts for all screen sizes
- ✅ Dark/light theme support
- ✅ Intuitive navigation patterns

---

## 🤝 Contributing

We welcome contributions! Here's how you can help:

### **✨ Feature Requests**
- Check existing issues first
- Describe the use case and expected behavior
- Consider implementing it yourself!

### **💻 Code Contributions**

1. **Fork the repository**
2. **Create feature branch**: `git checkout -b feature/amazing-feature`
3. **Follow coding standards**:
   - Use Kotlin coding conventions
   - Add KDoc comments for public APIs
   - Include unit tests for new features
4. **Commit changes**: `git commit -m 'Add amazing feature'`
5. **Push to branch**: `git push origin feature/amazing-feature`
6. **Open Pull Request**

### **Code Standards**
- **Kotlin**: Follow official style guide
- **Compose**: Use Compose best practices
- **Architecture**: Maintain MVVM + Clean Architecture
- **Testing**: Add tests for new functionality

---


- **OpenWeatherMap** for reliable weather data
- **Google AI** for powerful language generation
- **Firebase** for seamless backend services
- **Android Team** for amazing development tools
- **Open Source Community** for inspiration and libraries

---

## 📞 Contact

**Hritwik** - [reshu70173@gmail.com](mailto:reshu70173@gmail.com)

**Project Link**: [https://www.linkedin.com/in/reshu-singh07/](https://github.com/reshusingh07/sassyskies)] 

**LinkedIn**: [https://www.linkedin.com/in/reshu-singh07/](https://www.linkedin.com/in/reshu-singh07/)

---

<div align="center">

**Made with ❤️ and a lot of ☕ in India**

*If you found this project helpful, please consider giving it a ⭐!*

</div>
