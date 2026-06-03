# Harmonia — Windows

> *Your Music. Your World.*

A cinematic, playlist-first personal music sanctuary. Runs as a single HTML file on Windows. No installer, no server, no internet, no tracking — just double-click and go.

---

## What it is

Harmonia is a premium, dark-themed music player for **your own audio collection**. It's not a streaming service. It's a quiet, beautiful place to keep and play the music you already have.

- 🎬 Cinematic intro on launch
- 🔐 Private local account with a hashed password
- 📚 Mock playlists with themed atmospheres (Study, Workout, Night Drive, Gaming, Calm, Motivation, Sunrise)
- 🎵 Full-screen player with swipe gestures, shuffle, repeat, favorites
- 💾 Import your own MP3s — saved to your account, survives restarts
- 🔍 Instant search across songs, artists, albums, playlists
- ⚙️ Themes, animations toggle, intro toggle, profile editor

---

## Quick start

1. Download / copy **`Preview.html`** to your Windows PC.
2. **Double-click it.** It opens in your default browser.
3. Create an account on first launch.
4. That's it. No installation, no setup.

> 💡 Tip: rename `Preview.html` to `Harmonia.html` so it's easier to find.

---

## Make it feel like a real app (optional, 30 seconds)

Get a Start-Menu icon and a standalone window with no browser chrome:

### In Microsoft Edge or Google Chrome

1. Open `Preview.html` in Edge or Chrome.
2. Click the **⋯ menu** (top-right) → **Save and share → Create shortcut…**
   *(In Chrome: ⋮ menu → Cast, save, and share → Create shortcut…)*
3. **Tick the box "Open as window"**.
4. Click **Create**.

You now have a desktop shortcut. Double-click it → Harmonia opens in its own window with no tabs, no address bar. Right-click the taskbar icon → **Pin to taskbar** to keep it there.

Done. From now on, click the icon like any other app.

---

## How to use Harmonia

### Sign in
- **First time**: create an account with a username, display name, and password (min. 6 characters).
- **Returning**: sign in with your username + password. "Remember me" keeps you signed in for 30 days.

### Import your own music
1. Click **Library** in the bottom nav.
2. Click **Import Audio**.
3. Pick one or more `.mp3`, `.m4a`, `.wav`, `.ogg`, `.flac` files.
4. They appear in a new **MY LIBRARY** playlist, ready to play.

Your songs are saved to your account and will be there next time you sign in.

### Play music
- Tap any playlist → tap any song.
- The mini-player at the bottom shows what's playing.
- Tap it to open the full-screen player.

### Full-screen player gestures
| Gesture | Action |
|---|---|
| Swipe left | Next song |
| Swipe right | Previous song |
| Swipe down | Close player |
| `Space` | Play / Pause |
| `←` / `→` | Previous / Next |
| `Esc` | Close player |

### Manage playlists
- **Create**: Library → **New Playlist**
- **Rename**: Open a playlist → **Rename** button
- **Delete**: Open a playlist → **Delete** button
- **Reorder songs**: Drag and drop within the track list
- **Add a song**: Open a playlist → **Add Song**

### Edit your profile
**Settings → Edit profile** → change your display name, upload an avatar.

### Change password
**Settings → Change password** → enter current password → set a new one.

### Sign out
**Settings → Sign out**. Your music and playlists stay safe — you'll find them all when you sign back in.

---

## Privacy & security

Harmonia is **100% local-first**. Nothing ever leaves your computer.

| What | Where it's stored | Encryption |
|---|---|---|
| Your account (username, hashed password) | Browser `localStorage` | **PBKDF2-SHA256, 200,000 iterations**, 128-bit random salt — same family of password hashing used by 1Password & LastPass |
| Your session token | `localStorage` (if "Remember me") or `sessionStorage` (otherwise) | 30-day expiry / per-tab |
| Your imported MP3 files | Browser `IndexedDB`, scoped to your username | Raw blobs (your computer; not over a network) |
| Settings, playlists, favorites | In-memory + browser storage | — |

**Zero servers. Zero tracking. Zero telemetry. Zero network requests.** You can disconnect from Wi-Fi and Harmonia works exactly the same.

---

## FAQ

### Do I have to run a server (`.bat`, Python, anything) every time?
**No.** Just double-click `Preview.html`. That's all.

### Will my music survive after I close the browser?
**Yes.** Songs are saved to IndexedDB. They reload automatically when you sign in next time.

### How much music can I store?
Modern browsers give a few GB to IndexedDB on `file://`. For typical MP3s (~5 MB each), that's roughly **500–1,000 songs**. The Settings → Storage row shows your current usage.

### What if I use a different browser tomorrow?
Browser storage is per-browser, per-user. If you sign in on Edge today and Chrome tomorrow, they see two separate libraries. **Pick one browser** and stick with it for the most consistent experience.

### I forgot my password. What now?
Because there are no servers, there's no email reset. On the sign-in screen, click **Forgot?** → "Reset account". This wipes your account so you can create a new one. **Your imported music will be lost** along with the account.

### How do I uninstall it?
Just delete `Preview.html` (and any desktop shortcut you made). To also delete your account + music:
- Open `Preview.html`, press `F12` → Console → run:
  ```js
  indexedDB.deleteDatabase('harmonia'); localStorage.clear(); sessionStorage.clear();
  ```

### Can I use Harmonia on my phone?
Yes — open `Preview.html` in mobile Chrome. The UI is fully mobile-first with a bottom nav and swipe gestures. (For a "real" Android app version, see the separate `harmonia-android/` project.)

### Why is there an "Install" button missing? My PWA install icon isn't showing.
PWA install requires the file to be served over `http://`, not opened from `file://`. This is a browser security rule. You don't need PWA install — the "Save as window" trick above gives you the same standalone-app feel.

---

## System requirements

- **Windows 10 or 11** (works on older versions too, as long as the browser is modern)
- A reasonably current browser: **Chrome 90+, Edge 90+, or Firefox 90+**
- About 1 MB of disk for the HTML file. Your music takes whatever you import.

---

## Troubleshooting

### The cinematic intro hangs
Click the **Skip** button in the top-right corner of the intro. Then go to Settings and turn off "Cinematic intro" if you want.

### Imported music doesn't appear after closing browser
You may have opened `Preview.html` in **private/incognito mode**. Private windows don't persist storage. Open it in a normal window.

### Sound is muted
Browsers require a user gesture before playing audio. Click anywhere first, then press Play. Also check the volume slider in the full-screen player.

### File picker won't show my audio files
Make sure the file extension is one of `.mp3`, `.m4a`, `.wav`, `.ogg`, `.flac`, `.aac`. In the picker, change the filter to "All files" if needed.

### "Storage quota exceeded" when importing
You've hit your browser's IndexedDB cap. Either delete some imported songs (Settings → **Clear imported**) or split your library into a few accounts.

---

## File layout

The Windows version is **one single file**:

```
Preview.html      ← double-click this. That's the whole app.
README.md         ← you are here.
```

Everything else in this folder (icons, the `harmonia-app/` Tauri folder, `harmonia-android/`, `serve.py`, `start-harmonia.bat`, `manifest.webmanifest`, `sw.js`) is **optional** and only matters for advanced packaging paths. You can safely delete them if you only care about the Windows single-file experience.

---

## Version

Harmonia • Preview 1.0.0 (Windows single-file edition)

Built as a personal music sanctuary, not a product.
