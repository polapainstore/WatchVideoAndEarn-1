# Watch Video and Earn — Full Firebase Structure

## What is included
1. Firebase email/password login + registration.
2. Firestore user profiles with `role: user/admin`.
3. Admin video upload to Firebase Storage.
4. Firestore video catalogue and points-per-video.
5. Server-side reward claim using Cloud Functions.
6. Withdrawal request flow with minimum points + conversion rate.
7. Firestore + Storage security rules.
8. Admin/user separation structure.

## Important
This project is a starter implementation. It does not contain your private Firebase credentials and cannot be a ready-to-publish APK until you connect your Firebase project and build it.

## Firebase setup
- Create a Firebase project.
- Add Android app package: `com.watchvideoandearn.app`.
- Download `google-services.json` into `app/`.
- Enable Authentication > Email/Password.
- Create Firestore Database.
- Create Storage.
- Deploy `firebase/firestore.rules`, `firebase/storage.rules`, and `functions`.
- Create `settings/general` with:
  - `minWithdrawalPoints`: 1000
  - `pointsPerTaka`: 100

## Admin
After creating your account, change that user's Firestore `role` to `admin` from a trusted admin process/console. Do not let the mobile client choose its own role.

Recommended admin collections:
- users
- videos
- withdrawals
- rewardClaims
- settings/general

## Security
Points must NOT be granted directly by the Android client. The included Cloud Function performs the points update transaction server-side.

For a real production rewards platform, add:
- watch-time verification
- anti-bot/rate limits
- duplicate-device/account checks
- withdrawal fraud review
- audit logs
- App Check
- admin custom claims
- proper KYC/age/legal requirements where applicable

## Advertising
Do not pay users for ad clicks or manufacture ad views. Use only legitimate rewarded-ad placements and follow the chosen ad network's policies. The platform owner should earn from valid traffic, not incentivized ad clicks.
