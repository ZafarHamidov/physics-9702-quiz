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
- `mail` for email result requests, used by the Firebase Trigger Email extension.

If Firebase is not configured, each browser only sees its own local scores.

## Email results

To send results by email, install the official Firebase extension **Trigger Email from Firestore** and configure it to listen to the `mail` collection. The quiz writes documents shaped like:

```js
{
  to: "student@example.com",
  message: {
    subject: "Physics 9702/11 Quiz Results",
    text: "...",
    html: "..."
  }
}
```

Official docs: https://firebase.google.com/docs/extensions/official/firestore-send-email

## Sign-in methods

The quiz supports Google, email/password, passwordless email link, phone, and anonymous sign-in through Firebase Authentication.

1. Open Firebase Console.
2. Go to Authentication.
3. Click Get started if needed.
4. Open Sign-in method.
5. Enable Google.
6. Enable Email/Password and turn on Email link/passwordless sign-in.
7. Enable Phone.
8. Enable Anonymous.
9. Set a support email and save.
10. In Authentication > Settings > Authorized domains, make sure `zafarhamidov.github.io` is allowed.

The quiz uses the signed-in user's display name, email, or phone number as the leaderboard name. It stores the Firebase user ID with scores, but does not display email addresses in the public leaderboard.

## GitHub Pages

Publish the repository with GitHub Pages set to deploy from the `main` branch root. `index.html` redirects to the quiz page.
