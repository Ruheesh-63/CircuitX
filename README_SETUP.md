# CircuitX Premium · iPhone Liquid Glass · Spark FREE / Firestore-only

**Website brand:** CircuitX. **Existing Firebase project ID:** `circketx-df07a` (do NOT change).  
**Admin email:** `ruheeshruheesh5@gmail.com` + admin UID document in Firestore.

## தமிழ் Setup | Step by step

### 1. ZIP Extract + Live Server

1. ZIP → **Extract All**. VS Code → **File → Open Folder** → `CircuitX-Website`.
2. `index.html` → **Go Live**. Chrome: `http://localhost:5500/index.html`.
3. Liquid Glass, தமிழ்/English, Dark/Light, Search, Filters, Gallery மற்றும் Demo Projects வேலை செய்யும்.
4. `src/firebase-config.js`-ல் `circketx-df07a` Firebase Web Config ஏற்கனவே உள்ளது. இது public web config மட்டுமே; secret admin key அல்ல.

### 2. Firebase Authentication

1. Open https://console.firebase.google.com/project/circketx-df07a/authentication/providers
2. **Google** மற்றும் **Email/Password** → Enable, Save.
3. Authentication → Settings → Authorized domains → `localhost` சேர்க்கவும்.
4. Website-ல் Google Login test செய்யவும். Email/Password பயனர்கள் verification email link-ஐ திறக்க வேண்டும்.

### 3. Firestore Rules (VERY IMPORTANT)

1. Open https://console.firebase.google.com/project/circketx-df07a/firestore
2. Cloud Firestore Database ஏற்கனவே உருவாக்கப்பட்டிருக்க வேண்டும்.
3. Firestore → **Rules** → ZIP-ல் உள்ள `rules/firestore.rules` முழுவதும் Copy/Paste செய்து **Publish** செய்யவும்.
4. **இந்த Rules publish செய்யாமல் project upload மற்றும் code download வேலை செய்யாது!** பழைய Storage-version Rules-ஐ replace செய்ய வேண்டும்.
5. Realtime Database Rules-ல் paste செய்ய வேண்டாம். **Cloud Firestore Rules**-ல் மட்டும்.

### 4. Admin Permission

1. CircuitX-ல் `ruheeshruheesh5@gmail.com` Google account மூலம் Login செய்யவும்.
2. Firebase Console → Authentication → Users → இந்த user-ன் **UID** Copy செய்யவும்.
3. Firestore → Data → collection ID **`admins`** (UID அல்ல).
4. Document ID = Authentication user UID.
5. Field `active` → **boolean** → **true** → Save.
6. Refresh Website. **Dashboard** button தோன்றும். Admin Gmail **மட்டும்** போதாது; UID document வேண்டும்.

### 5. First Arduino project upload · Spark Free

1. CircuitX → **Dashboard**.
2. Title English/Tamil, Description, Category, Difficulty, Tags உள்ளிடுங்கள்.
3. Optional cover photo JPG/PNG/WEBP ≤2MB. Website அதனைச் சிறிய JPEG thumbnail-ஆக compress செய்து Firestore public metadata-ல் சேமிக்கும்.
4. **Code:** `.ino`, `.cpp`, `.h`, `.txt`, `.md`, `.json`, `.py` என்ற UTF-8 **text** file ≤80 KiB (81,920 bytes) தேர்வு செய்யுங்கள்; **அல்லது** code-ஐ `Or paste Arduino code` பகுதியில் Paste செய்யுங்கள். இரண்டையும் ஒரே நேரத்தில் செய்ய வேண்டாம்.
5. ZIP-ல் `example-code/arduino-uno-led-blink-demo.ino` என்ற test file உள்ளது; இதைக் கொண்டு முதலில் test செய்யலாம். இது Smart Green House code அல்ல.
6. **Publish project** அழுத்துங்கள். `projects/{projectId}` = public info + thumbnail; `projectCodeFiles/{projectId}` = private source code.
7. Project card-ல் **Download Code** button வரும். Verified Google/Email login செய்த users-க்கு மட்டும் code கிடைக்கும்.
8. ZIP, PDF, EXE, images-as-files, large binary files **இந்த Free version-ல் upload செய்ய முடியாது**. Storage / paid backend இல்லாமல் இதனைப் பாதுகாப்பாகச் செய்ய முடியாது.

### 6. Download Test (crucial)

1. Incognito/Private window → website → Project Code Download → Login prompt வர வேண்டும்.
2. Email/Password user login செய்தும் email **verify செய்யாதவருக்கு** download மறுக்கப்பட வேண்டும்.
3. Verified user login செய்தால் code text file `.ino` ஆக download ஆக வேண்டும்.
4. Admin அல்லாத user Dashboard/Upload செய்யக்கூடாது.
5. Firestore Console → `projectCodeFiles` collection-ல் code text இருப்பதை உறுதி செய்யலாம்; `projects` collection-ல் codeText இருக்கக் கூடாது.

### 7. Contact Form, bilingual UI, Gallery

- Verified users Firestore `messages` collection-க்கு Contact Form அனுப்பலாம்.
- Admin Dashboard → inbox-ல் பார்க்கலாம்.
- Gallery: Admin JPG cover upload செய்தால் compress செய்யப்பட்ட thumbnail; இல்லாவிட்டால் local SVG artwork.
- Liquid Glass design `liquid-glass.css`-ல்; Dark/Light + Tamil/English + animations available.

## Security / limits

- **Do not store source code in publicly readable `projects` documents.** Code stored in `projectCodeFiles`, `get` only for email-verified users. `list` denied.
- Firestore Rules (not hiding a button) enforce permissions. `getDocFromServer()` checks authorization for each download. A user who downloads a file may still share it manually. Firestore SDK's local cache / downloaded copies on shared devices should be treated accordingly.
- Cover thumbnails are public, small JPEG data URL strings in project metadata. Do not upload sensitive images.
- Client limit ≤80 KiB UTF-8 text. Firestore individual document hard limit **1 MiB**. Small files are not general-purpose file storage.
- Firestore Spark Free quotas apply (reads, writes, outbound transfer), and usage can stop at quota. No Blaze billing/Cloud Storage setup needed for these features.
- Previous `codePath` / Firebase Storage projects will still show metadata, but **their old Storage files cannot be downloaded** by this Firestore-only code. Re-upload text source via new Dashboard. Do not put public file URLs into project metadata.
- Firebase project config is public by design; **never** add Firebase Admin SDK service-account keys to web files.
- If other sites/apps use this Firestore project, replacing the Rules affects them too. Review before publishing.
- Firebase web SDK is loaded from Google CDN on first website load; an internet connection is needed.

### Firebase Hosting (optional)

`firebase.json` deploys **Firestore Rules + static Hosting only**; it does not use Firebase Storage. Publish rules in Console first. Hosting may be used through Firebase CLI if eligible, or use another static HTTPS host; set its domain in Authentication → Authorized domains.

## Files

- `index.html`: HTML UI
- `styles.css` + `liquid-glass.css` + `spark-free.css`: iPhone Liquid Glass design
- `src/app.js`: Google Login, Firestore-only projects and protected downloads
- `src/firebase-config.js`: existing public Firebase web config
- `src/i18n.js`: Tamil + English
- `rules/firestore.rules`: **REPLACE existing Firestore rules with this**
- `SECURITY_TESTS.md`: security checklist
- `TEST_CHECKLIST.md`: smoke tests

### Documentation

- https://firebase.google.com/docs/firestore/quotas
- https://firebase.google.com/docs/firestore/security/get-started
- https://firebase.google.com/docs/firestore/manage-data/transactions
- https://firebase.google.com/docs/projects/billing/firebase-pricing-plans
