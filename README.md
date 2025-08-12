# 🏋️ My Fitness - Gym Management System

A modern gym management app built with **React**, **TypeScript**, and **Firebase**.  
Manage members, track subscriptions, and monitor business analytics — all in one place.

![Gym Management Dashboard](https://images.pexels.com/photos/1552242/pexels-photo-1552242.jpeg?auto=compress&cs=tinysrgb&w=800&h=400)

## 🚀 Live Demo
[🌐 View Live](https://gleaming-vacherin-3f3cda.netlify.app)

## 🌟 Features
- 🔐 **Authentication** – Google OAuth + Email/Password
- 👥 **Member Management** – Profiles, subscriptions, notes
- 📊 **Dashboard Analytics** – Revenue, active members, expiry alerts
- 🎨 **User Experience** – Dark/Light mode, responsive UI, smooth animations
- ☁️ **Cloud Integration** – Real-time Firestore sync with security rules

## 🛠 Tech Stack
**Frontend:** React 18, TypeScript, Tailwind CSS, Lucide Icons  
**Backend:** Firebase Auth & Firestore  
**Deployment:** Netlify

## ⚡ Quick Start
```bash
# 1. Clone repository
git clone https://github.com/yourusername/my-fitness-gym-management.git
cd my-fitness-gym-management

# 2. Install dependencies
npm install

# 3. Create .env and add Firebase config
cp .env.example .env

# 4. Run development server
npm run dev
```
🔒 Firestore Security Rules
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /customers/{doc} {
      allow read, write: if request.auth != null &&
        request.auth.uid == resource.data.userId;
      allow create: if request.auth != null &&
        request.auth.uid == request.resource.data.userId;
    }
  }
}
