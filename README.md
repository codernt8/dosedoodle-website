# DoseDoodle website

Support page (`index.html`) and privacy policy (`privacy.html`) for the DoseDoodle iPhone app, live at https://dosedoodle.com/ (the old https://dosedoodle.netlify.app/ address still works). The support address `support@dosedoodle.com` forwards to the DoseDoodle support Gmail inbox through Cloudflare Email Routing. Plain static files, no build step, no external fonts, scripts or trackers. Use the Support URL for `/` and the Privacy Policy URL for `/privacy.html` in App Store Connect.

## Branches

- `main` is production. Once Netlify is connected, every push to `main` is a production deploy, so only merge to it when the change is ready to go live.
- `staging` is where changes are built and checked first. Pushes to it deploy to the free staging URL (see the Netlify project page). Promote to `main` only after checking staging.

Never force-push either branch.

## Editing

- `style.css` holds all the styling, light and dark.
- Images are in `img/` (WebP, 720 px wide, from the app's App Store screenshots in the private workspace repo under `medtracker/AppStore/Screenshots`). `img/og.png` is the 1200 x 630 social share image.
- When the app is live, replace the "Coming soon to iPhone" pill in `index.html` with the App Store link.

## Keep the policy in step with the app

If the app's lookups, permissions, analytics or sync change, update `privacy.html` and its "Last updated" date first. The App Store privacy label answers must match it. `grep -rn -E "SUPPORT_EMAIL|DEVELOPER_NAME" .` must return nothing before a deploy.
