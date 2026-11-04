# DoseDoodle site

Support page (`index.html`) and privacy policy (`privacy.html`) for the DoseDoodle iPhone app. Plain static files, no build step. Use the Support URL for `/` and the Privacy Policy URL for `/privacy.html` in App Store Connect.

Before deploying, replace the two placeholders in both pages:
- `SUPPORT_EMAIL`: the address people can write to (shown publicly).
- `DEVELOPER_NAME`: the name for the copyright line and "from ..." in the policy.

`grep -rn -E "SUPPORT_EMAIL|DEVELOPER_NAME" .` must return nothing before you publish.

Keep the policy in step with the app: if lookups, permissions, analytics or sync change, update `privacy.html` and its date first. The App Store privacy label answers must match it.
