# Saathi — Find your people. On campus.

Saathi is an exclusive social coordination platform built for IIT Roorkee students. Whether you are looking for a travel companion to the railway station, a study group for end-sems, or friends to play badminton with, Saathi helps you find your circle.

## ✨ Features
- **IITR Exclusive**: Strictly gated. Only `@*.iitr.ac.in` emails are allowed to register or login.
- **Smart Duplicate Prevention**: Before posting an activity, the platform checks for similar active circles (same time + same destination) to encourage pooling instead of fragmentation.
- **Private Group Chats**: Approved members get access to a real-time, private chat room for coordination.
- **Smart Suggestions**: Suggests activities based on your Bhawan/Hostel, Department, Year, and Interests.
- **Zero-Config Deployment**: 100% Serverless architecture. The entire application runs on the client and directly interfaces securely with Firebase.

## 🛠️ Tech Stack
- **Frontend**: React 18, Vite, TypeScript
- **Styling**: Tailwind CSS v4, Lucide Icons, Framer Motion
- **Backend / Database**: Firebase (Auth, Firestore)
- **Deployment Ready**: Configured for Vercel and Netlify (SPA routing included)

## 🚀 Local Setup

1. **Install Dependencies**
   ```bash
   npm install
   ```

2. **Configure Environment Variables**
   Copy `.env.example` to `.env` and fill in your Firebase configuration keys:
   ```bash
   cp .env.example .env
   ```

3. **Start the Development Server**
   ```bash
   npm run dev
   ```
   The app will be running at `http://localhost:5173`.

## 🌐 Deployment (Vercel / Netlify)

This project is perfectly optimized for free-tier deployments on **Vercel** or **Netlify**. It uses a purely static SPA architecture with no backend server required.

### Steps to Deploy:
1. Push this repository to GitHub.
2. Go to Vercel or Netlify and import the repository.
3. The platform will automatically detect **Vite** as the framework.
4. **Important**: Add all the `VITE_FIREBASE_*` environment variables (found in `.env.example`) to your Vercel/Netlify project settings before deploying.
5. In your [Firebase Console](https://console.firebase.google.com/), go to **Authentication > Settings > Authorized Domains** and add your new Vercel/Netlify domain (e.g., `saathi.vercel.app`) so Google Login works.
6. Deploy!

*Note: Custom routing rules for SPAs are already included in the `vercel.json` and `netlify.toml` files in this repository.*

## 🔒 Security & Firebase Rules
All business logic and security rules are enforced at the Firestore level. The `firestore.rules` file ensures that:
- Users can only edit their own profiles.
- Only the host can edit or delete an activity.
- Only approved members can read or write to an activity's private group chat.
- All documents enforce the `@*.iitr.ac.in` email restriction on writes.
