# Timetable

Editable weekly timetable. Light/dark theme. Installs on phone and laptop. Syncs between them through your GitHub repo.

## 1. Put it online

1. Create a **public** GitHub repo named `timetable`
2. Upload to the repo root: `index.html`, `data.json`, `manifest.json`, `sw.js`, `icon-192.png`, `icon-512.png`
3. Settings → Pages → Deploy from a branch → main → /(root) → Save
4. Your URL: `https://mxd-faahim.github.io/timetable/`

## 2. Install it

- **Phone (Chrome):** open the URL → menu (⋮) → Install app
- **Laptop (Chrome/Edge):** open the URL → install icon in the address bar → Install

## 3. Turn on sync

Make a token once:

1. GitHub → Settings → Developer settings → Personal access tokens → **Fine-grained tokens** → Generate new token
2. Repository access: **Only select repositories** → pick `timetable`
3. Permissions → Repository permissions → **Contents: Read and write**
4. Generate, copy the token

Then on **each device**: open the app → "Sync across devices" → paste the token → Save token.

From then on, **Save** writes to `data.json` in the repo, and every device pulls the latest each time it opens. "Pull latest" fetches on demand.

## How it behaves

- No token on a device → it still works, saves locally only
- No internet → shows the last copy it had; save again when back online
- Two devices edited while offline → last Save wins

## Keep the token private

The token is stored only in that device's browser storage — it is never written into the repo. Do not paste it into any file you upload. If it ever leaks, revoke it on GitHub and generate a new one.

## Editing the app itself

- `CHOICES` in `index.html` = the dropdown list
- `CODES` = subject codes shown as small text
- `ORIGINAL` = what **Reset** restores
- After changing any file, bump `CACHE` in `sw.js` (v6 → v7) so devices pick it up
