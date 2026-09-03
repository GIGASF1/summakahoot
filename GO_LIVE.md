# PCCM Poll — Go Live in 10 Minutes

## ✅ Done (Code is Ready)

- ✓ GitHub repo: https://github.com/GIGASF1/summakahoot
- ✓ All source code pushed
- ✓ Demo mode works locally: http://localhost:8765/index.html
- ✓ Ready for production deployment

---

## 🚀 Next Steps: Deploy to Netlify

### Option A: One-Click Deploy (Recommended)

Click this link and follow the prompts:
https://app.netlify.com/start/deploy?repository=https://github.com/GIGASF1/summakahoot

Netlify will:
1. Fork the repo to your account (optional)
2. Deploy the code
3. Give you a live URL (e.g., `pccm-poll-xyz.netlify.app`)

**Time: 30 seconds**

### Option B: Drag & Drop

1. Go to https://app.netlify.com/drop
2. Drag the `/Users/axr/summakahoot` folder onto the page
3. Done — live URL appears instantly

**Time: 30 seconds**

---

## 🔑 Setup Firebase (Required for Multi-Device)

Once you have a live URL, complete the Firebase setup:

1. Open `/Users/axr/summakahoot/FIREBASE_SETUP.md` (also in GitHub repo)
2. Follow the 6 steps
3. Paste your Firebase config into `index.html`
4. Push to GitHub (Netlify auto-redeploys)

**Time: 5 minutes**

---

## 📝 Test It

Once deployed and Firebase is configured:

1. Open the live URL
2. Click **"Presenter"**
3. Enter PIN: `2468`
4. Click **"New session"**
5. Share the QR code with fellows

**Demo session code (for testing locally):** `DEMO`

---

## 🎯 You're Ready!

Your live PCCM Poll deployment is ready to use with:

- **Bulk question import** (paste from ChatGPT/OpenEvidence)
- **Question bank** (tracks performance across all sessions)
- **Explanations** (show on reveal)
- **Keyboard shortcuts** (→ next, ← prev, Space toggle, R reveal, L lobby, C cards, M panel)
- **Offline-first** (works behind hospital proxies)

---

## 📞 Support

- **GitHub repo:** https://github.com/GIGASF1/summakahoot
- **README.md:** Full docs in the repo
- **Firebase setup help:** FIREBASE_SETUP.md in the repo
- **Demo code:** `DEMO` (available locally at http://localhost:8765/index.html)

---

## 🔐 Security Note

Change your PIN! In `index.html`:
```javascript
teacherPin: '2468',  // ← Change this to something only you know
```

Then push to GitHub → Netlify redeploys automatically.

---

## Questions?

Everything is documented in the GitHub repo. All code is open-source and free to modify.

**Ready to launch?** Click the one-click Netlify deploy link above and follow the Firebase setup guide.
