# महफ़िल (Mehfil) 🎶

Purani yaadon ka radio — Chai ki Tapri jaisi illustration ke saath, jo din
ke time ke hisaab se apna rang badalti hai (morning halka warm, evening
sunset-jaisa, raat mein neela-dark). Gaane **asli** bajte hain — YouTube ke
official embedded player ke through (koi mp3 file host nahi ki gayi, isliye
copyright-safe hai, aur full song bajta hai, koi 30-second trial nahi).

## Kya-kya hai isme
- Ek hi illustration (desktop ke liye landscape, mobile ke liye portrait
  version) — lekin CSS color-grading se **morning / evening / night** ka
  alag mood apne aap ban jaata hai, device ke system time ke hisaab se.
- Bada Hindi signboard **"महफ़िल"**।
- Top-left corner mein **live listeners counter** (jaise "24 online") —
  green dot ke saath, reference site jaisa hi look.
  > ⚠️ Ye ek **simulated** counter hai (gently random fluctuate karta
  > rehta hai) — kyunki GitHub Pages ek static site hosting hai, uske paas
  > apna server/database nahi hota jo real visitors count kare. Agar tumhe
  > **real** live-user count chahiye, neeche "Real online counter" section
  > dekho.
- Real gaane — YouTube IFrame Player se, play/pause/next/previous poori
  tarah kaam karte hain, gaana khatam hote hi agla apne aap bajta hai.
  Beech mein YouTube ka apna ad aa sakta hai (unka platform hai) — ye
  normal hai aur song poora hi bajta hai, koi cut/trial nahi.
- 90s station hamesha **"Tumsa Koi Pyaara"** (Khuddar) se start hoti hai,
  fir poora 90s jukebox continue chalta hai.
- Bottom-left **90s Classic** vs **Early 2000s Hits** selector.
- **Vintage volume knob** — click-drag karke (ya mouse wheel se) ghumao,
  YouTube player ka volume control karta hai.
- Top-right YouTube playlist icon.
- Mobile par poori screen scene + neeche floating glass pill player.
- Developer credit "Bhavesh Pandole", favicon = car icon.

## Folder structure
```
mehfil/
├── index.html          ← poora site (HTML + CSS + JS) is ek file mein hai
├── favicon.svg
└── assets/
    ├── scene-desktop.jpg   ← desktop background
    └── scene-mobile.jpg    ← mobile background
```
CSS aur JS ab `index.html` ke andar hi hain (`<style>` aur `<script>` tags mein)
— sirf images alag file mein hain kyunki unhe inline karne se file bahut bada
ho jaata. Kuch bhi edit karna ho toh seedha `index.html` khol ke karo.

## GitHub Pages par live karna (step by step)
1. GitHub.com par login karo → top-right **+** → **New repository**.
2. Naam do `mehfil` (ya jo chaho), Public rakho → **Create repository**.
3. Apne computer par terminal kholo, is `mehfil` folder ke andar jaake:
   ```
   git init
   git add .
   git commit -m "Mehfil radio site"
   git branch -M main
   git remote add origin https://github.com/<your-username>/mehfil.git
   git push -u origin main
   ```
   (`<your-username>` apne GitHub username se replace karo.)
4. GitHub par apne repo ke **Settings → Pages** mein jaao.
5. **Source** mein "Deploy from a branch" chuno, **Branch**: `main`,
   folder `/ (root)` → **Save**.
6. 1-2 minute wait karo — site live ho jaayegi:
   `https://<your-username>.github.io/mehfil/`

(Agar terminal/git use karna nahi aata, GitHub.com par repo khol ke
**"Add file → Upload files"** se bhi seedha in sab files ko drag-drop kar
sakte ho — phir wahi Settings → Pages step follow karo.)

## Real online counter (optional upgrade)
Abhi wala counter simulated hai. Agar sach mein kitne log website par hain
wo dikhana ho, iske liye ek chhota free backend chahiye hota hai — jaise
**Firebase Realtime Database** (presence feature) ya **Supabase**. Dono
free tier mein available hain aur GitHub Pages ke saath kaam kar sakte hain
(kyunki wo bhi client-side JS se hi connect ho jaate hain, koi apna server
chalane ki zaroorat nahi). Jab tum ready ho iske liye, mujhe bata dena —
main step-by-step Firebase setup kar dunga.

## Customize
Sab kuch ab `index.html` ke andar hai:
- Time slots `<script>` block ke `currentScene()` mein hain (morning 05–12,
  evening 12–19, night 19–05).
- Lighting colors `<style>` block mein `.light-overlay.morning/evening/night`
  aur `.scene-img.grade-*` mein hain.
- Playlists / opening song `<script>` block ke `playlists` object mein hain.
- Signboard text `<body>` mein `.signboard-text` / `.signboard-sub` mein hai.
