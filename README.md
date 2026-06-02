# Physics 9702/11 Quiz

Single-page quiz for CAIE Physics 9702/11 October/November 2025.

## Public leaderboard

The quiz works without setup using a local browser leaderboard. To make scores public for friends:

1. Create a Firebase project.
2. Create a Firestore database.
3. Add a web app in Firebase project settings.
4. Paste the Firebase web config into `leaderboard-config.js`.
5. Use Firestore rules that allow reads and creates for the quiz collection.

Example development-only Firestore rule:

```txt
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /physics_9702_w25_11/{scoreId} {
      allow read: if true;
      allow create: if
        request.resource.data.name is string &&
        request.resource.data.score is number &&
        request.resource.data.totalAttempts is number &&
        request.resource.data.totalTime is number;
    }
    match /physics_9702_w25_11_live/{sessionId} {
      allow read: if true;
      allow create, update: if
        request.resource.data.name is string &&
        request.resource.data.score is number &&
        request.resource.data.totalAttempts is number &&
        request.resource.data.totalTime is number;
      allow delete: if true;
    }
  }
}
```

## GitHub Pages

Publish the repository with GitHub Pages set to deploy from the `main` branch root. `index.html` redirects to the quiz page.
