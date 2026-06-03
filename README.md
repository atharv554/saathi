# Saathi — Find your people. On campus.

Saathi is an exclusive social coordination platform built for IIT Roorkee students. Whether you are looking for a travel companion to the railway station, a study group for end-sems, or friends to play badminton with, Saathi helps you find your circle and coordinate effortlessly.

## ✨ Key Features

- **Exclusive Community**: Strictly gated to IIT Roorkee students. Only `@*.iitr.ac.in` emails can register or log in.
- **Smart Group Coordination**: Post activities, manage join requests via waitlists, and chat in private groups restricted to approved members.
- **Interactive Map**: View activities across the campus on an interactive map with marker clustering and geolocation sorting.
- **Integrated Expense Tracker**: Split bills automatically and track who owes whom with a built-in settlement algorithm and UPI QR code generation.
- **Trust & Ratings**: Rate hosts and read reviews to ensure accountability. Ratings are uniquely enforced per user.
- **Seamless Sharing & Export**: Share activities via auto-generated QR codes and deep-links, or export them directly to your calendar.
- **Scalable Real-time Feed**: Enjoy an infinite-scrolling feed with smart suggestions based on your department or Bhawan.

## 🔒 Database & Authentication (Firebase)

Saathi is a 100% serverless application that relies entirely on **Firebase** for authentication and data storage.

- **Authentication**: Uses Google OAuth and Email/Password sign-ins.
- **Firestore Database**: Stores users, activities, waitlists, expenses, and chats.
- **Strict Security Rules (`firestore.rules`)**: 
  - Validates that only `@*.iitr.ac.in` emails can write to the database.
  - Prevents race conditions (like overbooking spots).
  - Ensures only the host can manage an activity and its waitlist.
  - Restricts private chats and expense trackers strictly to approved group members.

## 🛠️ Tech Stack

- **Frontend**: React 19, Vite, TypeScript
- **Styling & UI**: Tailwind CSS v4, Lucide Icons, Framer Motion
- **Maps**: Leaflet, React-Leaflet, MarkerCluster
- **Utilities**: React-QR-Code, Sonner (Toasts)
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
