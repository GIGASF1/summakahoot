# PCCM Poll

Kahoot-style live polling for pulmonary / critical care teaching. One HTML file, no accounts, free to run.

**Fellows:** scan the QR code (or type the 4-letter code at the site), enter their name once, answer on their phone.
**You (presenter):** open the site, enter the PIN, run the session from the projector screen.

## What it does

- **Questions**: multiple choice (with or without a marked correct answer) or free text. Add an image by pasting a screenshot (⌘V) straight into the form, dropping a file, or choosing one. Copy a slide region in PowerPoint, paste it here.
- **Live results** on the projector: bar chart for MC (shown when you close the question), free-text answers appear as they come in. "Reveal answer" highlights the correct option and tells each fellow if they were right.
- **Scores**: per fellow for the session, and an all-time table across every session (correct / answered / %). CSV export for both.
- **Cards** (oral exam style): type topics one per line. Switch the screen to Cards; fellows tap a face-down card on their phone, it flips for everyone with their name on it, and they explain the topic out loud or draw it on the board.
- **Lobby**: big QR code + join code with the names of everyone who has joined.

## Setup (about 10 minutes, one time)

Until you do this, the app runs in **demo mode**: it works in one browser only, so you can try it right away by opening the file, but phones in the room won't sync.

1. Go to <https://console.firebase.google.com>, **Add project** (any name, e.g. `pccm-poll`), analytics off.
2. Left menu **Build → Firestore Database → Create database**. Choose a region near you, start in production mode.
3. Open the **Rules** tab, replace the contents with the contents of `firestore.rules` from this folder, click **Publish**.
4. Click the gear → **Project settings**, scroll to **Your apps**, click the `</>` (web) icon, register the app (no hosting needed here). Copy the `firebaseConfig = { ... }` object.
5. Open `index.html`, find `CONFIG` near the top, and paste the object as the value of `firebase:`. Change `teacherPin` to something of your own.

Then host the folder anywhere that serves static files. Two free options:

**Option A, Firebase Hosting** (needs Node.js installed):

```bash
npm install -g firebase-tools
firebase login
firebase use --add        # pick the project you made
firebase deploy
```

Your site is at `https://<project-id>.web.app`.

**Option B, Netlify Drop**: sign up free at <https://app.netlify.com/drop>, drag this folder onto the page. Done. You can rename the site to something short like `pccm-poll.netlify.app` in Site settings.

Whenever you edit `index.html` (new PIN, tweaks), redeploy the same way.

## Running a session

1. Open the site, click **Presenter**, enter the PIN, click **New session**.
2. The Lobby screen shows the QR code and join code. Put it on the projector. Fellows join.
3. In the **Manage** panel add questions (they save instantly and can be reused during the session). Click ▶ on a question to put it on screen and open answering.
4. **Close & show results** → **Reveal answer** → **Next**.
5. For the card exercise: Manage → Cards, add topics, **Show on screen**.
6. Scores tab shows this session; **All-time** shows every session for every fellow.

Fellows are matched across sessions by the name they type, so ask them to use the same name each time (it's remembered on their phone).

## PowerPoint

No plugin. Keep the presenter page in a browser window next to PowerPoint and alt-tab, or use PowerPoint's **Insert → Add-ins → Web Viewer** to embed the presenter URL in a slide. The paste-an-image workflow covers most cases: copy from your slide, paste into the question.

## Cost

Firebase's free Spark plan allows 50,000 document reads and 20,000 writes per day. A session with 15 fellows and 20 questions uses well under 5,000. Hosting is free at this scale on either option.
