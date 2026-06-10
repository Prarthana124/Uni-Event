# Local Development Setup

This guide explains how to run Uni-Event locally using Docker and the Firebase Emulator Suite.

## Prerequisites

Before starting, ensure you have the following installed:

- Docker Desktop
- Docker Compose
- Git
- A Firebase project (Spark plan is sufficient)

## Environment Setup

### 1. Copy the Environment Template

```bash
cp app/.env.example app/.env
```

### 2. Configure Firebase

Create a Firebase project and populate the required Firebase configuration values in `app/.env`.

### 3. Optional Configuration

Google Sign-In (only required if testing Google authentication):

```env
EXPO_PUBLIC_GOOGLE_ANDROID_CLIENT_ID=
EXPO_PUBLIC_GOOGLE_IOS_CLIENT_ID=
EXPO_PUBLIC_GOOGLE_WEB_CLIENT_ID=
```

Email features (optional):

```env
EMAILJS_SERVICE_ID=
EMAILJS_TEMPLATE_ID=
EMAILJS_PUBLIC_KEY=
```

### 4. Enable Emulator Mode

Add the following to `app/.env`:

```env
EXPO_PUBLIC_USE_EMULATORS=true
```

## Running the Development Environment

Start all services:

```bash
docker compose up
```

This will start:

- Firebase Authentication Emulator
- Firestore Emulator
- Realtime Database Emulator
- Storage Emulator
- Firebase Emulator UI
- Expo Web Application

## Available Services

| Service                    | URL                   |
| -------------------------- | --------------------- |
| Firebase Emulator UI       | http://localhost:4000 |
| Authentication Emulator    | http://localhost:9099 |
| Firestore Emulator         | http://localhost:8090 |
| Realtime Database Emulator | http://localhost:9000 |
| Storage Emulator           | http://localhost:9199 |
| Expo Web                   | http://localhost:8081 |

## Stopping Services

```bash
docker compose down
```

Or press `Ctrl + C` in the terminal running Docker Compose.

## Notes

- Contributors must create their own Firebase project and provide the required Firebase configuration values.
- When `EXPO_PUBLIC_USE_EMULATORS=true`, the application connects to the local Firebase Emulator Suite.
- Google OAuth credentials are only required for testing Google Sign-In.
- EmailJS credentials are optional and only required for email-related features.
- Do not commit `.env` files or any personal credentials.
