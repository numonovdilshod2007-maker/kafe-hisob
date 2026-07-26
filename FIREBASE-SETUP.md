# Firebase bilan sozlash (Google akkount orqali kirish)

## 1-qadam: Firebase loyihasini yaratish

1. https://console.firebase.google.com ga o'zingizning Google akkountingiz bilan kiring.
2. "Add project" (Loyiha qo'shish) tugmasini bosing.
3. Loyihaga nom bering (masalan `kafe-hisob`), "Continue" bosing.
4. Google Analytics so'ralsa, o'chirib qo'yishingiz mumkin (kerak emas), "Create project" bosing.

## 2-qadam: Google orqali kirishni yoqish (Authentication)

1. Chap menyuda **Build → Authentication** ni tanlang.
2. "Get started" tugmasini bosing.
3. "Sign-in method" bo'limida **Google** ni tanlang, yoqing (Enable), "Save" bosing.

## 3-qadam: Ma'lumotlar bazasini yaratish (Firestore)

1. Chap menyuda **Build → Firestore Database** ni tanlang.
2. "Create database" tugmasini bosing.
3. Joylashuvni tanlang (istalgan yaqin region, masalan `eur3` yoki `asia-south1`), "Next" bosing.
4. **"Start in production mode"** ni tanlang (test mode emas), "Create" bosing.

### Xavfsizlik qoidalarini sozlash (muhim!)

Firestore yaratilgach, "Rules" bo'limiga o'ting va quyidagi qoidani joylashtiring — bu faqat har bir foydalanuvchi o'zining ma'lumotlarini ko'ra olishini ta'minlaydi:

```
rules_version = '2';
service cloud.firestore {
  match /databases/{database}/documents {
    match /users/{userId}/entries/{entryId} {
      allow read, write: if request.auth != null && request.auth.uid == userId;
    }
  }
}
```

"Publish" tugmasini bosing.

## 4-qadam: Web app konfiguratsiyasini olish

1. Loyiha sozlamalariga o'ting: chap tepada tishli g'ildirak belgisi → **Project settings**.
2. Pastga tushib, "Your apps" bo'limida **</> (Web)** belgisini bosing.
3. App nomini kiriting (masalan `kafe-web`), "Register app" bosing.
4. Sizga `firebaseConfig` degan kod ko'rsatiladi — quyidagicha ko'rinadi:

```javascript
const firebaseConfig = {
  apiKey: "AIzaSy...",
  authDomain: "kafe-hisob-xxxxx.firebaseapp.com",
  projectId: "kafe-hisob-xxxxx",
  storageBucket: "kafe-hisob-xxxxx.appspot.com",
  messagingSenderId: "123456789",
  appId: "1:123456789:web:abcdef123456"
};
```

5. Shu qiymatlarni nusxalab oling.

## 5-qadam: index.html faylini yangilash

`index.html` faylini oching, boshida shu qismni topasiz:

```javascript
const firebaseConfig = {
  apiKey: "YOUR_API_KEY",
  authDomain: "YOUR_PROJECT.firebaseapp.com",
  projectId: "YOUR_PROJECT_ID",
  storageBucket: "YOUR_PROJECT.appspot.com",
  messagingSenderId: "YOUR_SENDER_ID",
  appId: "YOUR_APP_ID"
};
```

Shu qismni Firebase konsolidan olgan haqiqiy qiymatlaringiz bilan almashtiring.

## 6-qadam: GitHub'ga yuklash va Vercel'da deploy qilish

1. Yangilangan `index.html` faylini GitHub repositoryingizga yuklang (commit qiling).
2. Vercel avtomatik qayta deploy qiladi.
3. Sayt ochilganda endi "Google bilan kirish" tugmasi chiqadi — bosganingizda Google akkountingiz orqali kirasiz.

## 7-qadam: ruxsat etilgan domenni tekshirish

Agar login qilishda "auth/unauthorized-domain" degan xato chiqsa:

1. Firebase konsolida **Authentication → Settings → Authorized domains** ga o'ting.
2. Sizning Vercel domeningizni qo'shing (masalan `kafe-hisob.vercel.app`).

## Natija

Endi qaysi qurilmadan (telefon, kompyuter, planshet) shu saytga kirib, bir xil Google akkount bilan login qilsangiz — barcha ma'lumotlaringiz avtomatik sinxronlanadi va bir xil ko'rinadi.
