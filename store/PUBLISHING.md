# Publishing to Google Play (Trusted Web Activity)

Prerequisites: a Google Play developer account (one-time US$25), and the app live over HTTPS
(GitHub Pages: Settings → Pages → Deploy from branch `main` / root).
Live URL: https://dixlercovie-byte.github.io/recipes/

## 1. Build the Android bundle
1. Go to https://www.pwabuilder.com and enter the live URL.
2. Fix anything it flags, then **Package for stores → Android**.
3. Suggested settings: package ID e.g. `io.github.dixlercovie_byte.recipes` (cannot be changed later),
   start URL `/recipes/index.html`, let PWABuilder generate a new signing key.
4. Download the zip. **Keep the signing key and its passwords somewhere safe** — losing it means you
   cannot update the app. Do not commit it to this repo.

## 2. Verify ownership (Digital Asset Links)
The zip contains an `assetlinks.json` with your key's SHA-256 fingerprint (`store/assetlinks.json.template`
shows the shape). It must be served at:

    https://dixlercovie-byte.github.io/.well-known/assetlinks.json

With GitHub Pages that root belongs to a repo named **`dixlercovie-byte.github.io`** — create it, put the file
at `.well-known/assetlinks.json` (and an empty `.nojekyll` file so the dot-folder is served), and enable Pages
for it. If you enrol in Play App Signing, also add the Play-generated fingerprint (Play Console → Setup →
App signing). Until this is in place the app shows a browser address bar.

## 3. Play Console
1. Create app → upload the `.aab` to a **closed testing** track first.
2. Fill in the listing from `LISTING.md`, upload the images in this folder.
3. Complete App content: privacy policy URL, data safety, content rating, ads declaration, target audience.
4. New personal developer accounts must typically run a closed test with ~12 testers for 14 days before
   production access is offered — check the current requirement in the Console.
5. Promote to production after review.

## Updating later
Web changes go live as soon as GitHub Pages redeploys — no new Play release is needed unless you change
the Android wrapper (icon, package settings, etc.).
