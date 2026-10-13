THIRD EYE EDITS — MOBILE-FIRST PROTOTYPE

Files:
- index.html: complete self-contained photo filter + AI prompt-library prototype.

What works:
- Select a photo from your phone
- Apply browser-based color filters
- Save the filtered photo
- Copy ready-made AI prompts or write your own

What does not work yet:
- It does not generate AI-edited images directly. AI image generation requires an image-editing service.
- It is a web prototype, not a compiled Android APK.

Test on Android:
1. Extract the ZIP.
2. Open index.html in Chrome or another modern browser.
   Depending on your phone's file manager/browser, local file access may be restricted. If it doesn't open correctly, host the file as a website first.

Free publishing route:
1. Create/sign into a GitHub account.
2. Create a public repository named `third-eye-edits`.
3. Upload `index.html` to the repository root using GitHub's website in Chrome.
4. In repository Settings > Pages, select deploy from the `main` branch and `/ (root)`.
5. Wait for GitHub Pages to publish; it will provide a public website URL.
6. Test the site on your phone. You can use the browser's Add to Home screen feature for an app-like shortcut.

Google Play Store:
- A web page is not automatically a Play Store Android app.
- Publishing to Play Store requires an Android package, signing, store listing, and compliance with current Play Console rules. A trusted wrapper/build service or Android build environment is needed.
- Do not put private AI service API keys in index.html. Use a backend if you later connect an AI API.

Privacy:
- This prototype processes the selected image in the browser; it does not upload the image to a server.
