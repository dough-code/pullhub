# Pullhub Launch Checklist

## Current Chrome Web Store Draft - 2026-06-18
- Draft item has been created.
- Extension ID: `hgkankpnpgoikbcggnlnlgddmnkendof`
- Chrome Web Store URL: `https://chromewebstore.google.com/detail/pullhub/hgkankpnpgoikbcggnlnlgddmnkendof`
- Current status: Draft, not submitted for review, not published.
- The Chrome Web Store URL may 404 until the item is published; this is expected.
- Rebuilt package has been uploaded to the CWS draft.
- Manifest version for next submission: `1.0.2`.
- CWS/dashboard visible version (`version_name`): `1.0.2`.
- Latest rebuilt zip SHA-256: `70cb23b49a8b51cc2951c2c2c5988570de3d7b0091637e10bcd1ab65d00df128`.
- Rebuilt package includes the popup support email fix.
- Website Add to Chrome CTAs point to the CWS URL.

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
- Google Cloud project name: `pullhub`.
- Project number: `345457259417`.
- Project ID shown in console: `smart-test-497508`.
- OAuth app branding:
  - App name: Pullhub.
  - Home page: `https://debutt.studio/`.
  - Privacy policy: `https://debutt.studio/privacy.html`.
  - Terms: `https://debutt.studio/terms.html`.
- Authorized domains include `chromiumapp.org` and `debutt.studio`.
- Manifest OAuth client ID: `345457259417-v4q2j8tm8agjvucm1m5f183r2r955msj.apps.googleusercontent.com`.
- OAuth client type currently shown: Web application.
- The Web application client type is correct for the current implementation because the code uses `chrome.identity.launchWebAuthFlow` with `chromiumapp.org` redirect URIs.
- Authorized redirect URIs include:
  - Old/testing redirect, intentionally retained: `https://hpikpbjjahbpjjlbaengkocckppdkmbh.chromiumapp.org/`.
  - Production CWS redirect: `https://hgkankpnpgoikbcggnlnlgddmnkendof.chromiumapp.org/`.
- Manifest was not changed for OAuth.
- No manifest `"key"` field was added.
- Current extension usage / OAuth appears to work for current extension usage / dev ID behavior after adding the production redirect URI.
- Production-ID OAuth still must be tested on CWS extension ID `hgkankpnpgoikbcggnlnlgddmnkendof` before submit review.
- To test production-ID OAuth before submit review, use a CWS trusted tester / draft install flow if available, or temporarily pin manifest `"key"` only if explicitly chosen later.
- Branding verification and the 100-user OAuth cap remain later considerations, not immediate blockers for draft setup.
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
- Before CWS review submission, confirm the ExtensionPay dashboard is configured for CWS extension ID `hgkankpnpgoikbcggnlnlgddmnkendof`.

## Chrome Web Store
- Current package uploaded to the draft: `outputs/pullhub-webstore.zip`.
- Build future upload packages with `scripts/package-webstore.sh`.
- The package script uses an explicit production allowlist and excludes `.git`, `.DS_Store`, source maps, dev docs, stale launch artifacts, and non-production debris.
- After packaging, compare the ZIP contents against the clean staging directory produced by the script.
- Distribution / Payments: Contains in-app purchases.
- Distribution / Visibility: Public.
- Privacy remote code answer: No, Pullhub does not execute remotely hosted code.
- Add store icon and screenshots.
- Prepare 5 screenshots.
- Add homepage, privacy policy, and support links.
- Fill data practices consistently with the privacy policy.
- Explain why `<all_urls>` is needed for user-selected saving and capture.
- Explain that the all-page content script supports Google Slides detection, user-initiated drag/drop, cursor capture, and optional floating widget behavior, and does not automatically collect page content.
- Explain `storage` and `unlimitedStorage`: boards, screenshots, settings, account display state, and local backups are stored locally; unlimited storage prevents quota failures for local boards and captures.
- Explain Google OAuth scopes:
  - `presentations`: insert selected references and layouts into Google Slides.
  - `drive.file`: create and manage Pullhub-created fallback files for Slides insertion.
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
- Confirm final Chrome Web Store extension ID: `hgkankpnpgoikbcggnlnlgddmnkendof`.
- Confirm authorized redirect URI exists: `https://hgkankpnpgoikbcggnlnlgddmnkendof.chromiumapp.org/`.
- Confirm OAuth consent screen app name, homepage, privacy URL, support email, and authorized domain match Pullhub / debutt.studio.
- `drive.metadata` has been temporarily removed for launch-risk reduction; presentation rename is disabled and should be revisited later with a narrower OAuth-safe design.
- Confirm `<all_urls>`, `tabs`, and content script justifications are copied into the CWS permission justification fields.
- Confirm ExtensionPay dashboard is configured for the CWS extension ID before submit review.
- Complete the CWS Privacy questionnaire before submit review.
- Complete store listing fields and assets before submit review.
- Prepare 5 screenshots before submit review.
- Run final production-ID OAuth / sign-in / Slides push / Drive fallback test before submit review.
- Record final package SHA and commit before submit review.
- Confirm upload ZIP checksum matches: `70cb23b49a8b51cc2951c2c2c5988570de3d7b0091637e10bcd1ab65d00df128`.
