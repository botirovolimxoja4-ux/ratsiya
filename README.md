# Mobil Ratsiya — tekin PWA (o'rnatib ishlatish)

Bos-va-gapir mobil ratsiya. Ovoz ikkala telefon orasida **bevosita** oqadi (WebRTC),
hech qayerda saqlanmaydi. O'z serveringiz **kerak emas** — ulanish uchun tekin PeerJS
buluti, tekin STUN/TURN ishlatiladi.

## Fayllar
- `index.html` — butun ilova (interfeys + mantiq)
- `manifest.webmanifest`, `sw.js` — telefon ekraniga "ilova" qilib o'rnatish uchun (PWA)
- `icon-192.png`, `icon-512.png` — ilova belgisi

---

## A) Tavsiya etiladi — GitHub Pages (tekin, keyin tahrirlash eng oson)

1. github.com da ro'yxatdan o'ting (tekin).
2. **New repository** → nom bering (masalan `ratsiya`) → **Public** → **Create**.
3. **Add file → Upload files** → shu papkadagi BARCHA fayllarni tashlang
   (`index.html`, `manifest.webmanifest`, `sw.js`, `icon-192.png`, `icon-512.png`) → **Commit**.
4. Repozitoriy → **Settings → Pages** → "Branch" ni `main` qilib **Save**.
5. Bir-ikki daqiqada manzil chiqadi:
   `https://FOYDALANUVCHI.github.io/ratsiya/` — bu sizning ilova havolangiz.

**Keyin o'zgartirish:** GitHub'da `index.html` ni oching → qalam (✏️) belgisi → tahrirlang
→ **Commit**. Sayt bir daqiqada o'zi yangilanadi. Tamom.

## B) Tezkor sinash — Netlify (tekin)

1. app.netlify.com → **Add new site → Deploy manually**.
2. Shu papkani (yoki `ratsiya.zip` ni) maydonga tashlang. Darrov HTTPS havola beradi.
   (Keyin tahrirlash uchun qaytadan tashlash kerak — shuning uchun uzoq muddatga GitHub qulayroq.)

> Muhim: ikkala variant ham **HTTPS** beradi. Mikrofon va PWA faqat HTTPS'da ishlaydi.

---

## Telefonga o'rnatish (PWA)
- **Android (Chrome):** havolani oching → menyu (⋮) → **Install app / Add to Home screen**.
- **iPhone (Safari):** havolani oching → **Share** → **Add to Home Screen**.
Shundan so'ng oddiy ilovadek ochiladi.

## Qanday sinaladi
1. Ikkita telefonda havolani oching.
2. Har birida **boshqa** raqam va ism kiriting → ro'yxatdan o'ting.
3. Bir-biringizning raqamingizni kontakt qilib qo'shing.
4. Kontakt yonidagi 📞 ni bosing → narigi telefonda chaqiruv chiqadi → qabul qiling.
5. **Bosib turib gapiring** (yoki "Ochiq liniya"). Guruh uchun bir nechta kontakt tanlab "Boshlash".

---

## Cheklovlar (halol)
- **Suhbatdosh ilovani ochiq tutishi kerak.** Veb-ilova yopilganda ishlamaydi.
- Ism faqat raqamdan avtomatik chiqmaydi — birinchi ulanishda narigi taraf o'z ismini
  yuboradi va shundan keyin kontaktda saqlanadi.
- Ba'zi qattiq tarmoqlar ortida ulanish uchun TURN kerak (tekin Open Relay qo'shilgan,
  lekin u doim 100% kafolat bermaydi).
- PeerJS tekin buluti sinash uchun zo'r, lekin yuqori yuk uchun mo'ljallanmagan.

## Kelajakdagi to'liq versiya (baribir tekin bo'lishi mumkin)
"Raqamdan ism avtomatik chiqsin" va "ilova yopiq bo'lsa ham push orqali eshitsin" —
bular uchun kichik backend kerak. **Firebase (tekin Spark reja)** buni beradi:
- Firestore — raqam→ism katalogi va onlayn holat
- Cloud Messaging (FCM) — yopiq/orqa fondagi ilovani uyg'otuvchi push
- WebRTC signaling — Firestore orqali

Tayyor bo'lsangiz, shu PWA ustiga Firebase ulab, push va katalogni qo'shamiz.
