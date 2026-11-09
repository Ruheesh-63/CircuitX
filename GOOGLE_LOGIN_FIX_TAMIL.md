# CircuitX Google Login · Troubleshoot (Tamil)

1. VS Code Live Server -> `http://localhost:5500/index.html`.
2. Firebase -> Authentication -> Sign-in method -> **Google Enabled**.
3. Firebase -> Authentication -> Settings -> Authorized domains -> `localhost`.
4. `src/firebase-config.js` projectId `circketx-df07a` என்று இருக்க வேண்டும்.
5. Chrome popup-ஐ Allow செய்யவும்; Login முடியும் வரை Google popup-ஐ மூடாதீர்கள்.
6. Browser F12 -> Console -> `auth/unauthorized-domain`, `auth/popup-blocked`, `auth/popup-closed-by-user` ஆகிய error codes-ஐ வாசிக்கவும்.
7. Google login முடிந்த பிறகு Firestore Rules publish + admins/<UID> active:true இருந்தால்தான் Dashboard வரும்.

Spark Free version-ல் code download Firestore-இல் உள்ளது. Storage/Blaze/CORS தேவையில்லை.
