# CV – അറബി പഠന ഗെയിം

ഈ ഫോൾഡറിലെ എല്ലാ ഫയലുകളും GitHub റിപ്പോസിറ്ററിയുടെ ഏറ്റവും പുറത്ത് (root) അപ്‌ലോഡ് ചെയ്യുക:
index.html, manifest.webmanifest, sw.js, icon.svg, icon-192.png, icon-512.png, icon-maskable-512.png

## ലീഡർബോർഡ് എല്ലാ ഫോണിലും ഒരുപോലെ കാണാൻ (Firebase Realtime Database)
1. console.firebase.google.com → പ്രോജക്റ്റ് → Build → Realtime Database → Create Database (Start in locked mode).
2. Rules ടാബിൽ താഴെയുള്ളത് പേസ്റ്റ് ചെയ്ത് Publish:

{
  "rules": {
    "comps": {
      "$code": {
        ".read": true,
        "$name": {
          ".write": "!data.exists() || newData.child('points').val() >= data.child('points').val()",
          ".validate": "newData.hasChildren(['name','points'])"
        }
      }
    }
  }
}

(ഉയർന്ന പോയിന്റ് ആർക്കും കുറയ്ക്കാൻ പറ്റാത്ത നിയമമാണിത്.)
3. Data ടാബിന് മുകളിൽ കാണുന്ന URL (https://....firebaseio.com) കോപ്പി ചെയ്യുക.
4. index.html ൽ `const CFG={DB_URL:"",` എന്ന വരിയിലെ "" നുള്ളിൽ ആ URL ഒട്ടിക്കുക (അവസാനത്തെ / വേണ്ട).
5. sw.js ലെ `cv-game-v3` എന്നത് `cv-game-v3` ആക്കുക (ഓരോ മാറ്റത്തിനും ഒന്ന് കൂട്ടുക).
