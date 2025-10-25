# Music Practice Tracker with Google Drive Sync

## Setup Instructions

Your tracker now syncs across all your devices using Google Drive. You just need to set up the Google API credentials once.

### Step 1: Get Google API Credentials (5 minutes, one time)

1. Go to https://console.cloud.google.com/
2. Create a new project (or use existing one)
3. Enable the Google Drive API:
   - Click "Enable APIs and Services"
   - Search for "Google Drive API"
   - Click "Enable"

4. Create OAuth credentials:
   - Go to "Credentials" in the left menu
   - Click "Create Credentials" → "OAuth client ID"
   - You might need to configure the OAuth consent screen first:
     - User type: External
     - App name: "Music Practice Tracker" (or whatever)
     - Add your email
     - Scopes: Just skip this for now
     - Test users: Add your own Gmail address
   - Back to creating credentials:
     - Application type: "Web application"
     - Name: "Music Practice Tracker"
     - Authorized JavaScript origins: Add where you'll host it (e.g., `https://yourname.netlify.app`)
     - Click "Create"
   
5. You'll get a **Client ID** - copy this

6. Get an API Key:
   - Click "Create Credentials" → "API key"
   - Copy this key

### Step 2: Add Credentials to Your Tracker

1. Open `practice_tracker_sync.html` in a text editor
2. Find these lines near the top of the `<script>` section:
   ```javascript
   const CLIENT_ID = 'YOUR_CLIENT_ID_HERE';
   const API_KEY = 'YOUR_API_KEY_HERE';
   ```
3. Replace with your actual credentials:
   ```javascript
   const CLIENT_ID = 'your-actual-client-id.apps.googleusercontent.com';
   const API_KEY = 'your-actual-api-key';
   ```

### Step 3: Deploy Online

Use Netlify Drop (easiest):
1. Go to https://app.netlify.com/drop
2. Drag your modified `practice_tracker_sync.html` file
3. You'll get a URL like `https://random-name.netlify.app`
4. Copy this URL

### Step 4: Update Google Cloud Console

Go back to your OAuth credentials in Google Cloud Console and add your actual Netlify URL to "Authorized JavaScript origins"

### Step 5: Use It!

**On any device:**
1. Open your Netlify URL
2. Click "Sign in with Google"
3. Approve the permissions
4. Your practice data loads from Google Drive
5. Any changes auto-sync

**On iPhone:**
1. Open the URL in Safari
2. Tap Share → "Add to Home Screen"
3. Now it works like a native app

## How It Works

- Your practice data is saved in a file called `music_practice_data.json` in your Google Drive
- Every time you check off a practice session, it auto-syncs to Drive
- Open the tracker on any device, sign in, and your data loads automatically
- Only you can access this file (it's private to your Google account)

## Troubleshooting

**"Sign in with Google" doesn't work:**
- Make sure you added your Netlify URL to "Authorized JavaScript origins" in Google Cloud Console
- Check that you're using the exact URL (with https://)

**Data not syncing:**
- Click "Sync Now" button manually
- Check browser console for errors

**Can't enable Drive API:**
- Make sure you've selected the right project in Google Cloud Console
- Billing needs to be enabled (but Drive API is free for personal use)

## Privacy Note

This setup means:
- Data is stored in YOUR Google Drive, not on someone else's server
- Only you have access to it
- Google can't see your practice habits (it's just a JSON file to them)
- No third-party tracking or analytics
