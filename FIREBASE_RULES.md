# Firebase Security Code (PROFESSIONAL & SECURE)

Machan, meka thama professional ma widiya.
Me rules walin kiyanne:

1. **Gallery & Tours:** Ona kenekta balanna puluwan (READ: true).
2. **Edit:** Edit karanna puluwan 'admin@gmail.com' kiyana email eken log wela inna kenata witharai.

### Cloud Firestore Rules

Go to **Firestore Database** > **Rules** and paste this:

rules_version = '2';
service cloud.firestore {
match /databases/{database}/documents {

    // Check if the user is authenticated and is the specific admin
    function isAdmin() {
      return request.auth != null && request.auth.token.email == 'admin@gmail.com';
    }

    // Tours Rules
    match /tours/{document=**} {
      allow read: if true;
      allow write: if isAdmin();
    }

    // Legacy Gallery Rules
    match /gallery/{document=**} {
      allow read: if true;
      allow write: if isAdmin();
    }

    // NEW: Albums Rules
    match /albums/{document=**} {
      allow read: if true;
      allow write: if isAdmin();
    }

}
}

```

### Wadagath
Uba Firebase Console eke **Authentication** > **Users** walata gihin `admin@gmail.com` kiyana user wa hadanna one manual.
Password eka: `20140903` (Uba illapu eka).
Ehema nathuwata me rules wada karanne na.
```
