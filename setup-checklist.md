# Pullhub Launch Checklist

## Website
- Publish `index.html`, `privacy.html`, `terms.html`, and `support.html`.
- Use `debutt.studio` or a subpath/subdomain such as `debutt.studio/pullhub`.
- Add the privacy policy URL to Chrome Web Store Developer Dashboard.

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
- If changing the ExtensionPay ID from `smart-reference`, verify migration/subscription continuity before changing code.

## Chrome Web Store
- Upload `pullhub-webstore.zip`.
- Add store icon and screenshots.
- Add homepage, privacy policy, and support links.
- Fill data practices consistently with the privacy policy.
- Explain why `<all_urls>` is needed for user-selected saving and capture.

## Before Publish
- Test Google sign-in with the final extension ID.
- Test push to Google Slides.
- Test Drive fallback upload.
- Test screenshot capture.
- Test ZIP export/import.
- Test paid/trial state.
- Test board sharing if enabled.
