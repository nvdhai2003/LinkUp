# LinkUp

A modern social media mobile application built with **React Native** and **Expo**, powered by **Supabase** for authentication, database, and storage.

> *Where every thought finds a home and every image tells a story.*

## Features

- **Authentication** — Email/password sign-up and login with persistent sessions via Supabase Auth
- **Home Feed** — Infinite-scroll feed of posts with real-time updates (new posts, edits, deletions appear instantly)
- **Create & Edit Posts** — Rich-text editor with image and video attachments
- **Likes & Comments** — Like/unlike posts and leave comments with real-time counters
- **Notifications** — Real-time in-app notifications with a badge counter on the home screen
- **User Profiles** — View and edit your profile (avatar, name, bio, phone, address) with image upload
- **Real-Time Updates** — Powered by Supabase Realtime (Postgres Changes) for posts and notifications

## Tech Stack

| Layer | Technology |
|-------|-----------|
| Framework | [Expo](https://expo.dev) (SDK 51) with [Expo Router](https://docs.expo.dev/router/introduction/) (file-based routing) |
| Language | JavaScript / TypeScript (config) |
| UI | React Native 0.74, React Native Reanimated, React Native Gesture Handler |
| Backend | [Supabase](https://supabase.com) (Auth, PostgreSQL database, Storage, Realtime) |
| Rich Text | `react-native-pell-rich-editor` + `react-native-render-html` |
| Media | `expo-image-picker`, `expo-av` (video playback), `expo-image` |
| State | React Context (`AuthContext`) |
| Date/Time | Moment.js |

## Project Structure

```
LinkUp/
├── app/                    # Screens (Expo Router file-based routing)
│   ├── _layout.jsx         # Root layout with AuthProvider & auth state listener
│   ├── index.jsx           # Entry point (loading screen)
│   ├── welcome.jsx         # Welcome / onboarding screen
│   ├── login.jsx           # Login screen
│   ├── signUp.jsx          # Sign-up screen
│   └── (main)/             # Authenticated screens group
│       ├── home.jsx        # Home feed with real-time posts
│       ├── newPost.jsx     # Create / edit post
│       ├── postDetails.jsx # Post detail view with comments
│       ├── profile.jsx     # User profile with their posts
│       ├── editProfile.jsx # Edit profile form
│       └── notifications.jsx # Notifications list
├── assets/
│   ├── icons/              # SVG icon components
│   └── images/             # Static images (splash, welcome, default avatar, etc.)
├── components/             # Reusable UI components
│   ├── Avatar.jsx
│   ├── BackButton.jsx
│   ├── Button.jsx
│   ├── CommentItem.jsx
│   ├── Header.jsx
│   ├── Input.jsx
│   ├── Loading.jsx
│   ├── NotificationItem.jsx
│   ├── PostCard.jsx
│   ├── RichTextEditor.jsx
│   └── ScreenWrapper.jsx
├── constants/              # App constants & theme
│   ├── index.js            # Supabase URL & anon key
│   └── theme.js            # Colors, fonts, border radii
├── contexts/
│   └── AuthContext.js      # Auth state provider
├── helpers/
│   └── common.js           # Responsive dimension helpers (hp, wp)
├── lib/
│   └── supabase.js         # Supabase client initialization
├── services/               # Data-access layer (Supabase queries)
│   ├── imageService.js     # Image upload, download, URL helpers
│   ├── notificationService.js
│   ├── postService.js      # CRUD for posts, likes, comments
│   └── userService.js      # User data get/update
├── patches/                # patch-package patches
├── scripts/
│   └── reset-project.js    # Expo reset script
├── app.json                # Expo app config
├── babel.config.js
├── package.json
└── tsconfig.json
```

## Getting Started

### Prerequisites

- [Node.js](https://nodejs.org/) (LTS recommended)
- [Expo CLI](https://docs.expo.dev/get-started/installation/) — installed via `npx`
- [Expo Go](https://expo.dev/go) on your mobile device **or** an Android / iOS emulator
- A [Supabase](https://supabase.com) project (the app ships with a pre-configured project URL)

### Installation

1. **Clone the repository**

   ```bash
   git clone https://github.com/nvdhai2003/LinkUp.git
   cd LinkUp
   ```

2. **Install dependencies**

   ```bash
   npm install
   ```

3. **Start the development server**

   ```bash
   npx expo start
   ```

4. **Run on a device or emulator**

   From the Expo CLI output, choose one of:
   - Scan the QR code with **Expo Go** (iOS / Android)
   - Press `a` to open on an **Android emulator**
   - Press `i` to open on an **iOS simulator** (macOS only)
   - Press `w` to open in a **web browser**

### Available Scripts

| Script | Description |
|--------|-------------|
| `npm start` | Start the Expo dev server |
| `npm run android` | Start on Android |
| `npm run ios` | Start on iOS |
| `npm run web` | Start on Web |
| `npm test` | Run tests with Jest |
| `npm run lint` | Run Expo lint |
| `npm run reset-project` | Reset to a blank `app/` directory |

## Supabase Setup

The app connects to a Supabase backend. The expected database tables are:

| Table | Purpose |
|-------|---------|
| `users` | User profiles (name, image, bio, address, phoneNumber) |
| `posts` | Post content (body, file, userId) |
| `postLikes` | Post like records (userId, postId) |
| `comments` | Post comments (text, userId, postId) |
| `notifications` | Notification records (senderId, receiverId, title, data) |

A `uploads` storage bucket is used for profile images, post images, and post videos.

## Learn More

- [Expo Documentation](https://docs.expo.dev/)
- [Supabase Documentation](https://supabase.com/docs)
- [React Native Documentation](https://reactnative.dev/docs/getting-started)
- [Expo Router](https://docs.expo.dev/router/introduction/)

## License

This project is private.
