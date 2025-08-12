# My Fitness - Gym Management System

A modern gym management application built with React, TypeScript, and Firebase.

## Features

- 🔐 Google Authentication
- 👥 Customer Management
- 📊 Dashboard Analytics
- 🌙 Dark/Light Theme
- 📱 Responsive Design
- ☁️ Cloud Database (Firestore)

## Firebase Setup

To set up Firebase for this project:

### 1. Firestore Security Rules

You need to configure Firestore security rules in your Firebase Console:

1. Go to [Firebase Console](https://console.firebase.google.com/)
2. Select your project: `my-fitness-c53d3`
3. Navigate to **Firestore Database** → **Rules**
4. Replace the existing rules with:

```javascript
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    // Allow authenticated users to read and write their own customer data
    match /customers/{document} {
      allow read, write: if request.auth != null && request.auth.uid == resource.data.userId;
      allow create: if request.auth != null && request.auth.uid == request.resource.data.userId;
    }
    
    // Deny all other access
    match /{document=**} {
      allow read, write: if false;
    }
  }
}
```

5. Click **Publish** to save the rules

### 2. Authentication Setup

1. In Firebase Console, go to **Authentication** → **Sign-in method**
2. Enable **Google** sign-in provider
3. Add your domain to authorized domains:
   - `localhost` (for development)
   - `gleaming-vacherin-3f3cda.netlify.app` (for production)

### 3. Firestore Database

1. Go to **Firestore Database**
2. Create database in **production mode**
3. Choose your preferred location

## Troubleshooting

### "Failed to load customers" Error

This error typically occurs due to:

1. **Firestore Security Rules**: Make sure the rules above are properly configured
2. **Authentication**: Ensure the user is properly authenticated
3. **Network Issues**: Check your internet connection

### Permission Denied Errors

- Verify Firestore security rules are correctly set up
- Ensure the user is authenticated before making database calls
- Check that the `userId` field is properly set in documents

## Development

```bash
npm install
npm run dev
```

## Deployment

The app is deployed on Netlify: https://gleaming-vacherin-3f3cda.netlify.app

## Tech Stack

- **Frontend**: React 18, TypeScript, Tailwind CSS
- **Backend**: Firebase (Auth + Firestore)
- **Icons**: Lucide React
- **Deployment**: Netlify