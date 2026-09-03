# Firebase Setup for PCCM Poll

**Time: ~5 minutes**

## Step 1: Create Firebase Project

1. Go to https://console.firebase.google.com
2. Click **"Create a new project"**
3. Name it: `pccm-poll` (or any name)
4. Uncheck "Enable Google Analytics"
5. Click **Create project**
6. Wait ~1 minute for it to finish

## Step 2: Set Up Firestore Database

1. Left menu → **Build** → **Firestore Database**
2. Click **"Create Database"**
3. Choose a region close to you (e.g., `us-east1`)
4. Select **"Production mode"**
5. Click **Create**

## Step 3: Update Security Rules

1. Click the **Rules** tab in Firestore
2. Replace ALL the text with this:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /sessions/{session} {
      allow read, write: if true;
      match /{sub=**} {
        allow read, write: if true;
      }
    }
    match /bank/{doc=**} {
      allow read, write: if true;
    }
  }
}
```

3. Click **Publish**

## Step 4: Register Web App

1. Click the gear icon (⚙) → **Project settings**
2. Scroll to **Your apps** section
3. Click the **`</>`** (web) icon
4. Click **"Register app"** → name it `pccm-poll` → **Register app**
5. Copy the config object that appears (the one starting with `const firebaseConfig = {...}`)

## Step 5: Paste Config into index.html

1. Open `index.html` from the GitHub repo
2. Find `CONFIG` near the top (~line 25):
   ```javascript
   const CONFIG = {
     firebase: null,  // ← PASTE HERE
     teacherPin: '2468',
     title: 'PCCM Poll',
   };
   ```
3. Replace `firebase: null` with your config object (just the object, not the `const firebaseConfig = ` part)

It should look like:
```javascript
const CONFIG = {
  firebase: {
    apiKey: "...",
    authDomain: "...",
    projectId: "...",
    ...
  },
  teacherPin: '2468',
  title: 'PCCM Poll',
};
```

## Step 6: Redeploy

1. Commit and push the change:
   ```bash
   git add index.html
   git commit -m "Add Firebase config"
   git push
   ```

2. Netlify auto-redeploys (watch your email for notification)

## Done!

Your app is now live and fully functional. Create a session and share the QR code with fellows.

**Change your PIN:** In the `CONFIG` object, change `teacherPin: '2468'` to something only you know.
