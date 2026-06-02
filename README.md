# Physics 9702/11 Quiz

Single-page quiz for CAIE Physics 9702/11 October/November 2025.

## Public and live leaderboard

The quiz works without setup using a local browser leaderboard. To make completed scores and the live "currently taking the quiz" list public for friends:

1. Create a Firebase project.
2. Create a Firestore database.
3. Add a web app in Firebase project settings.
4. Paste the Firebase web config into `leaderboard-config.js`.
5. Open Firestore Rules and paste the contents of `firestore.rules`.
6. Publish the rules.

The app uses these Firestore collections:

- `physics_9702_w25_11` for completed scores.
- `physics_9702_w25_11_live` for active sessions.
- `physics_9702_w25_11_participants` for people who started at least one session.

If Firebase is not configured, each browser only sees its own local scores.

## GitHub Pages

Publish the repository with GitHub Pages set to deploy from the `main` branch root. `index.html` redirects to the quiz page.
