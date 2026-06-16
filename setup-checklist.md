# Pullhub Launch Checklist

## Website
- Publish `index.html`, `privacy.html`, `terms.html`, and `support.html`.
- Use `debutt.studio`.
- Add `https://debutt.studio/privacy.html` to Chrome Web Store Developer Dashboard.
- Add `https://debutt.studio/support.html` as the support URL.
- Add `https://debutt.studio/terms.html` where terms are requested or linked from listing/support materials.

## Landing Page Demo Freeze
The Pullhub landing page demo/video section is integrated, deployed, and ready to freeze. Do not reopen the How-it-works demo section before launch unless a production bug is found.

Final How-it-works state:
- Three real workflow demo videos are integrated: `01 Pull`, `02 Save`, and `03 Slide`.
- The section reads as `01 Pull -> 02 Save -> 03 Slide`.
- The layout is frozen as alternating full-width rows with large readable 16:10 video frames.
- Do not cardify the rows or make further pre-launch layout/CSS changes to this section.
- Handoff section is frozen.
- How-it-works 01/02/03 layout is frozen.
- No more pre-launch layout polish is planned for this landing page section.

Video loading behavior:
- Demo videos use WebM first, MP4 fallback second, and JPEG posters.
- Video elements use `preload="none"`, `muted`, `loop`, and `playsinline`.
- IntersectionObserver plays videos only when visible and pauses them offscreen.
- Reduced-motion fallback remains intact.

Final compressed demo assets:
- `assets/demos/01-pull.webm`: 812,316 B
- `assets/demos/01-pull.mp4`: 595,322 B
- `assets/demos/01-pull.jpeg`: 100,092 B
- `assets/demos/02-save.webm`: 375,028 B
- `assets/demos/02-save.mp4`: 299,606 B
- `assets/demos/02-save.jpeg`: 39,365 B
- `assets/demos/03-slide.webm`: 475,959 B
- `assets/demos/03-slide.mp4`: 388,243 B
- `assets/demos/03-slide.jpeg`: 39,751 B
- Total demo assets after compression: 3,125,682 B

Compression settings:
- Output size: 1280x800.
- Aspect ratio: 16:10.
- Frame rate: 30fps.
- Audio stripped.
- WebM: VP9, CRF 34.
- MP4: H.264, CRF 26, preset slow, yuv420p, `+faststart`.
- Posters exported as JPEG from final MP4 files.

Step 02 crop:
- `02-save` was cropped toward the Pullhub board panel during compression.
- Purpose: make Step 02 read as board organization, save, recolor, and move references, and keep it visually distinct from Step 03.
- Crop used: `crop=1072:670:200:50,scale=1280:800`.

Post-deployment QA:
- Desktop checked.
- 768px checked.
- 390px checked.
- No horizontal overflow.
- Videos remain large and readable.
- Videos start paused with posters, then play when visible.
- Videos pause offscreen.
- No console errors.
- `01 -> 02 -> 03` reads as `Pull -> Save -> Slide`.
- Step 03 remains the main slide payoff.
- No `index.html`, CSS, layout, copy, or structure changes were made during the final compression pass.

Future post-launch ideas only:
- Workflow connector/spine.
- Sticky-copy / advancing-media scrollytelling.
- Unified product surface.
- Further video A/B testing.

Next steps:
- Finish launch docs and final checklist.
- Commit deployment-ready landing page changes if not already committed.

## Google Cloud
- OAuth consent screen app name: Pullhub.
- Support email: support@debutt.studio.
- Authorized domain: debutt.studio.
- Chrome extension OAuth client should use the final Chrome Web Store extension ID.
- Keep a separate development OAuth client for unpacked testing if the unpacked ID differs.

## Firebase
- Confirm Firestore rules match intended sharing behavior.
- If Firebase Auth federated sign-in is used, add the final Chrome extension ID / authorized domain required by Firebase.
- Keep development and production IDs documented.

## ExtensionPay
- Product name: Pullhub.
- Trial: 14 days.
- Recommended plans: USD 6.99 monthly, USD 60 annual.
- Production ExtensionPay ID in the extension package is `pullhub`.

## Chrome Web Store
- Build the upload package with `scripts/package-webstore.sh`.
- Upload `outputs/pullhub-webstore.zip`.
- The package script uses an explicit production allowlist and excludes `.git`, `.DS_Store`, source maps, dev docs, stale launch artifacts, and non-production debris.
- After packaging, compare the ZIP contents against the clean staging directory produced by the script.
- Add store icon and screenshots.
- Add homepage, privacy policy, and support links.
- Fill data practices consistently with the privacy policy.
- Explain why `<all_urls>` is needed for user-selected saving and capture.
- Explain that the all-page content script supports Google Slides detection, user-initiated drag/drop, cursor capture, and optional floating widget behavior, and does not automatically collect page content.
- Explain `storage` and `unlimitedStorage`: boards, screenshots, settings, account display state, and local backups are stored locally; unlimited storage prevents quota failures for local boards and captures.
- Explain Google OAuth scopes:
  - `presentations`: insert selected references and layouts into Google Slides.
  - `drive.file`: create and manage Pullhub-created fallback files for Slides insertion.
  - `drive.metadata`: locate and check metadata for the Pullhub Uploads folder and related Drive files used by the fallback workflow; not used to read Drive file contents.
  - `userinfo.email`: show the signed-in account, connect account state to Pullhub access, and support Firebase sharing ownership.
- Explain Drive fallback public-link behavior: when direct Slides insertion fails, Pullhub may upload a fallback image to the user's Drive and make that file readable by anyone with the link so Google Slides can render it.
- Explain Firebase/Firestore: optional public board sharing stores a board snapshot for the public link.
- Explain ExtensionPay/Stripe: trial, subscription, and Pro access management.
- Explain `web_accessible_resources`: required for the optional pinned floating widget iframe to load the Pullhub popup and its local scripts/styles inside a webpage.

## Before Publish
- Test Google sign-in with the final extension ID.
- Test push to Google Slides.
- Test Drive fallback upload.
- Test screenshot capture.
- Test ZIP export/import.
- Test paid/trial state.
- Test board sharing if enabled.

## Manual Google OAuth / CWS Console Checks
- Confirm final Chrome Web Store extension ID.
- Add authorized redirect URI: `https://<final-extension-id>.chromiumapp.org/`.
- Confirm OAuth consent screen app name, homepage, privacy URL, support email, and authorized domain match Pullhub / debutt.studio.
- Confirm whether `drive.metadata` triggers restricted-scope verification / CASA.
- If restricted-scope verification blocks launch, fallback plan is to scope-reduce by removing the current/opened deck rename path that requires `drive.metadata`.
- Confirm `<all_urls>`, `tabs`, and content script justifications are copied into the CWS permission justification fields.
- Confirm upload ZIP checksum matches: `2394c24520e1a8824f2b591a16b84921c8aa0a1d175df5d6f3ac2b22f0a7a0d0`.
