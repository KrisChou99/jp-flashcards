# JP Flashcards PWA — Deployment Guide

## Files in this repo

```
flashcard-pwa/
├── index.html      ← The entire app (no build step needed)
├── manifest.json   ← PWA config (name, icon, colors)
├── sw.js           ← Service Worker (offline support)
├── icon-192.png    ← App icon (replace with your own)
├── icon-512.png    ← App icon large
└── words.xlsx      ← Your vocabulary list ← EDIT THIS TO ADD WORDS
```

---

## Step 1 — Create GitHub account & repo

1. Go to https://github.com and sign up (free)
2. Click **New repository**
3. Name: `jp-flashcards` (or anything you like)
4. Set to **Public**
5. Click **Create repository**

---

## Step 2 — Upload files

### Option A: Via GitHub web (easiest, no Git needed)

1. Open your repo on GitHub
2. Click **Add file → Upload files**
3. Drag ALL files from this folder into the upload area
4. Click **Commit changes**

### Option B: Via Git (for future updates)

```bash
git clone https://github.com/YOUR_USERNAME/jp-flashcards.git
# Copy all files into the cloned folder
git add .
git commit -m "initial deploy"
git push origin main
```

---

## Step 3 — Enable GitHub Pages

1. Go to your repo → **Settings** tab
2. Left sidebar → **Pages**
3. Under **Source**, select `Deploy from a branch`
4. Branch: `main`, folder: `/ (root)`
5. Click **Save**
6. Wait ~1 minute
7. Your app URL will appear: `https://YOUR_USERNAME.github.io/jp-flashcards/`

---

## Step 4 — Install on phone

### iPhone / iPad (Safari only)
1. Open the URL in **Safari** (must be Safari, not Chrome)
2. Tap the **Share button** (box with arrow)
3. Scroll down → tap **Add to Home Screen**
4. Tap **Add** — done! App appears on home screen

### Android (Chrome)
1. Open the URL in **Chrome**
2. Tap the **3-dot menu** (top right)
3. Tap **Add to Home screen**
4. Tap **Add** — done!

---

## How to add new words

1. Open `words.xlsx`
2. Go to the **words** sheet
3. Add a new row at the bottom:

| A (kanji) | B (kana) | C (meaning) | D (example) | E (category) |
|---|---|---|---|---|
| 新しい単語 | あたらしいたんご | New word | 例文を書いてください | daily |

**Categories:** `automotive` / `software` / `protocol` / `linux` / `safety` / `business` / `daily`

4. Save the file
5. Upload to GitHub (or `git push`)
6. Open app on phone — tap **Shuffle** to reload

> ✨ The app automatically fetches the latest `words.xlsx` every time you open it.
> If you're offline, it uses the cached version from last time.

---

## Customizing the icon

Replace `icon-192.png` and `icon-512.png` with your own square PNG images.
- 192×192 px for standard, 512×512 px for high-res
- Use a rounded design — iOS will mask it to a circle/rounded rect

---

## Troubleshooting

**"No data" on first open**
→ Make sure `words.xlsx` is in the root of your repo (same folder as `index.html`)

**App not updating after git push**
→ Wait 1-2 minutes for GitHub Pages to rebuild
→ On phone, close and reopen the app
→ If still stale, clear browser cache

**"Add to Home Screen" not appearing on iPhone**
→ Must use Safari (not Chrome, Firefox, etc.)

**Offline not working**
→ Open the app once on WiFi first — this installs the Service Worker and caches assets
→ After that, works offline
