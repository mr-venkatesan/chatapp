# 💬 ChatFlow — Real-time Chat Application

## 📱 App Overview
A full-featured real-time chat application built with Flutter (Mobile) 
and .NET Core (Backend). WhatsApp-inspired UI with enterprise-grade 
architecture using Clean Architecture + BLoC pattern.

---

## 🎯 Purpose
Portfolio project demonstrating:
- Flutter Clean Architecture
- Real-time communication (SignalR)
- Video/Audio calling (WebRTC)
- JWT Authentication with Refresh Token
- Secure file/media handling

---

## ✨ Features

### 🔐 Authentication
- Sign In / Sign Up
- JWT + Refresh Token (Auto refresh)
- Secure token storage (flutter_secure_storage)
- Biometric login (optional)
- Auto logout on token expiry

### 👥 Contacts
- Search users by name / email / phone
- Add / Remove contacts
- Online / Offline status
- Last seen timestamp

### 💬 Chat — 1-to-1 & Group
- Real-time messaging via SignalR (.NET Core)
- Message types:
  ✅ Text messages
  ✅ Images (camera + gallery)
  ✅ Files (PDF, DOC, etc.)
  ✅ Voice messages (record + play)
- Message status: Sent ✓ / Delivered ✓✓ / Read ✓✓ (blue)
- Typing indicator (...)
- Reply to message
- Delete message (for me / for everyone)
- Message reactions (emoji)
- Offline message queue (send when reconnected)

### 👥 Group Chat
- Create group (name + avatar)
- Add / Remove members
- Admin controls
- Group info page

### 📞 Calls — WebRTC
- 1-to-1 Video call
- 1-to-1 Audio call
- Call history
- Mute / Unmute
- Camera on/off
- Speaker toggle
- Call notifications

### 👤 Profile
- Profile photo upload
- Update name / status / bio
- Privacy settings
- Block / Unblock users

### 🔔 Notifications
- Push notifications (FCM)
- In-app notifications
- Message preview
- Call notifications

---

## 🏗️ Technical Architecture

### Frontend — Flutter
```
Pattern:     Clean Architecture + BLoC
Language:    Dart
Min SDK:     Android 6.0 (API 23) / iOS 12
```

### Backend — .NET Core
```
Framework:   ASP.NET Core 8.0
Database:    SQL Server
ORM:         Entity Framework Core
Auth:        JWT + Refresh Token
Real-time:   SignalR
Storage:     Azure Blob / AWS S3
```

## 🔄 Data Flow

```
USER ACTION
    ↓
Widget (UI)
    ↓
BLoC Event
    ↓
Use Case (Domain)
    ↓
Repository (Abstract)
    ↓
Repository Impl (Data)
    ↓
  ┌─────────────────┐
  │  Remote DS      │  ← .NET Core API / SignalR
  │  Local DS       │  ← SQLite cache
  └─────────────────┘
    ↓
Either<Failure, Data>
    ↓
BLoC State
    ↓
Widget rebuilds
```

---

## 🔐 Security Implementation

```
1. JWT Access Token    → 15 min expiry
2. Refresh Token       → 7 days expiry
3. Auto Token Refresh  → Interceptor + Mutex
4. Secure Storage      → Android Keystore / iOS Keychain
5. SSL Pinning         → MITM attack prevention
6. Screenshot Block    → Sensitive screens
```

---

## 💧 Memory Leak Prevention

```
1. StreamSubscription  → cancel() in close()
2. Controllers         → dispose() in dispose()
3. AnimationController → dispose() in dispose()
4. WebRTC streams      → close() + dispose()
5. Image cache         → clear on memory warning
```

---

## 📱 Screens

```
Splash Screen
    ↓
Onboarding (first launch)
    ↓
Sign In / Sign Up
    ↓
Home (Chat List)
├── Chat Room (1-to-1)
│   ├── Text / Image / File / Voice
│   └── Video / Audio Call
├── Groups
│   ├── Group Chat Room
│   └── Group Info
├── Contacts
│   └── Search Users
├── Notifications
└── Profile
    └── Settings
```

---

## 🚀 How to Run

### Flutter
```bash
# Install dependencies
flutter pub get

# Run
flutter run
```

### .NET Core
```bash
# Restore packages
dotnet restore

# Update database
dotnet ef database update

# Run
dotnet run
```
