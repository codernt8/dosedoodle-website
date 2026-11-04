# Handover: DoseDoodle support and privacy site

Written 4 November 2026 for the next Claude Code session (run on Tim's PC, where Node and the Netlify tooling already work). Read this first, then do "What is left".

## What this is

Two static pages for the DoseDoodle iPhone app (working name was MedTracker; the final App Store name is **DoseDoodle**). Apple requires a public Support URL and Privacy Policy URL for the App Store Connect record.

- `index.html`: support page (also the Support URL).
- `privacy.html`: privacy policy, written from what the app actually does.
- `style.css`: shared styles, light and dark. No external fonts or scripts, on purpose.
- `netlify.toml`: publishes the folder as it is, no build step, plus a few security headers.
- `README.md`: short notes on editing.

The text is complete and the placeholders are filled in:
- Support email: DoseDoodleSupport@gmail.com
- Developer name: Timothy Crouch

## Netlify state

- Free Netlify site already created: **name `dosedoodle`**, **site id `9d3594c9-903b-47a0-a44f-5aacb42bcb3f`**, team id `69a6e4acc576a7e36f454826`.
- Project page: https://app.netlify.com/projects/dosedoodle
- It has **no deploy yet**, so it is not live. Tim chose the free `netlify.app` address, with no custom domain. Do not buy or attach a domain unless he asks.
- Not linked to a git repo. The files are deployed from this folder.

## What is left

1. **Deploy the folder to the `dosedoodle` site**, as production. Any of these works:
   - Netlify CLI from this folder: `netlify deploy --prod --dir=. --site 9d3594c9-903b-47a0-a44f-5aacb42bcb3f`
   - The Netlify MCP connector's `deploy-site` operation with that site id. It returns an `npx @netlify/mcp ...` command with a one-off proxy token. Run the command it gives you. Do not save that command or token anywhere.
   - Or drag this folder onto https://app.netlify.com/projects/dosedoodle/deploys
2. **Check it is live.** Fetch and read:
   - https://dosedoodle.netlify.app/ should show the support page.
   - https://dosedoodle.netlify.app/privacy.html should show the policy.
   - Confirm the page has real styling (not plain text), the email link reads DoseDoodleSupport@gmail.com, and `grep -rn -E "SUPPORT_EMAIL|DEVELOPER_NAME" .` returns nothing in the folder.
3. **Tell Tim the two URLs** for App Store Connect:
   - Support URL: `https://dosedoodle.netlify.app/`
   - Privacy Policy URL: `https://dosedoodle.netlify.app/privacy.html`
   If the name `dosedoodle` turned out to be unavailable, the actual address is shown on the Netlify project page. Use that one and say so.

## Things to keep true

- **The policy must match the app.** If the app's lookups, permissions, analytics or sync change, update `privacy.html` and its "Last updated" date first. The App Store privacy label answers must match it too. Today the policy says:
  - Records stay on the iPhone. No accounts, ads, analytics or tracking.
  - The only thing that leaves the phone is the medicine name, sent to openFDA (api.fda.gov) when the person taps Look up.
  - Optional: notifications, camera (label photo read on the phone), calendar, Face ID app lock, Siri and Shortcuts, shared PDF and CSV reports.
  - Side-effect text is from US FDA drug labels, is not medical advice, and is not endorsed by the FDA.
- **Do not add trackers, analytics, fonts from a CDN, or any third-party script** to these pages. The policy says there are none.
- This repo (`codernt8/claude-workspace`) is **private**. The site is deployed from a local folder, so the repo does not need to become public.

## Context, if useful

- The app code is in `../medtracker` (its own `STATUS.md` has the release checklist). Another session was renaming the app to DoseDoodle and removing the bundled side-effect list (FDA-only for 1.0) at the time of writing. If that work changed what the app sends or asks permission for, re-check the policy against the app's `Info.plist` strings and `PrivacyInfo.xcprivacy`.
- Other App Store Connect items still on Tim: creating the app record under the name DoseDoodle (check it is free), listing text and screenshots, uploading the archive, and answering the privacy label questions.
- The policy is a draft written by Claude, not legal advice. Tim should read it once before submitting.
