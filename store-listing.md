# Pullhub Chrome Web Store Listing Draft

## Current CWS Draft Status - 2026-06-18
- Extension ID: `hgkankpnpgoikbcggnlnlgddmnkendof`
- Chrome Web Store URL: `https://chromewebstore.google.com/detail/pullhub/hgkankpnpgoikbcggnlnlgddmnkendof`
- Status: Draft, not submitted for review, not published.
- The CWS URL may 404 until publication; this is expected.
- Manifest version for next submission: `1.0.2`
- CWS/dashboard visible version (`version_name`): `1.0.2`
- Latest uploaded package SHA-256: `70cb23b49a8b51cc2951c2c2c5988570de3d7b0091637e10bcd1ab65d00df128`
- Distribution / Payments: Contains in-app purchases.
- Distribution / Visibility: Public.
- Remote code answer: No, Pullhub does not execute remotely hosted code.
- Remaining before submit review: ExtensionPay dashboard confirmation for the CWS extension ID, Privacy questionnaire, listing fields/assets, 5 screenshots, final production-ID OAuth/sign-in/Slides push/Drive fallback test, and final SHA/commit record.

## Short Description
Save visual references into boards and push them to Google Slides.

## Detailed Description
Pullhub helps designers, creatives, marketers, and researchers collect visual references while browsing and turn them into presentation-ready Google Slides.

Use Pullhub to save images into boards, capture selected areas of a page, organize references by project, export ZIP backups, and push curated boards directly into Google Slides with automatic layout.

Core features:
- Save images from webpages into visual boards
- Capture screenshots and selected page areas
- Push boards to current, selected, or new Google Slides
- Organize references with board colors and notes
- Export and import ZIP backups
- Optional board sharing
- Light and dark appearance modes

Free plan limits are designed for trying the workflow. Pullhub Pro unlocks unlimited boards, captures, and sharing.

## Permission Justification
- `contextMenus`: Adds right-click save and push actions.
- `tabs`: Detects active Google Slides tabs and current page context.
- `activeTab`: Captures or interacts with the current user-selected page.
- `storage`: Stores boards, settings, signed-in account display state, subscription status cache, and local extension state.
- `unlimitedStorage`: Allows local boards, screenshots, and exported/imported reference collections to remain local without Chrome extension storage quota failures.
- `scripting`: Injects capture and floating widget scripts when the user requests those features.
- `notifications`: Shows success/error messages for capture and push actions.
- `identity`: Signs users into Google for Slides and Drive integration.
- `sidePanel`: Provides the Pullhub side panel experience.
- `downloads`: Exports board backups as ZIP files.
- `<all_urls>`: Allows users to save references and capture content from the pages they choose.
- Content script on `<all_urls>`: Supports Google Slides page detection, drag/drop to Slides when the user uses the pinned in-page widget, cursor capture mode, and restoring the optional floating widget. It does not automatically collect page content.
- `web_accessible_resources`: Allows the extension popup and its required local scripts/styles to render inside the optional pinned floating widget iframe on webpages.
- Google `presentations`: Inserts user-selected references and layouts into Google Slides.
- Google `drive.file`: Creates and manages Pullhub-created fallback image files used when Google Slides cannot insert a source image directly.
- Google `userinfo.email`: Shows the signed-in account, links account state to Pullhub access, and supports Firebase sharing ownership.
- Drive fallback public-link behavior: If direct Slides insertion fails, Pullhub may upload an image to the user's Drive and set that fallback file so anyone with the link can view it, only so Google Slides can render the image.
- Firebase/Firestore: Used only for optional public board sharing. Shared boards store a snapshot of the board data needed for the public link.
- ExtensionPay/Stripe: Used for trial, subscription, and Pro access management.

## Store Listing URLs
- Homepage: `https://debutt.studio/`
- Privacy Policy: `https://debutt.studio/privacy.html`
- Support: `https://debutt.studio/support.html`
- Terms: `https://debutt.studio/terms.html`
- Chrome Web Store draft: `https://chromewebstore.google.com/detail/pullhub/hgkankpnpgoikbcggnlnlgddmnkendof`

## OAuth / External Services Notes
- Manifest OAuth client ID: `345457259417-v4q2j8tm8agjvucm1m5f183r2r955msj.apps.googleusercontent.com`.
- Production redirect URI is configured in Google Cloud: `https://hgkankpnpgoikbcggnlnlgddmnkendof.chromiumapp.org/`.
- Old/testing redirect URI is intentionally retained: `https://hpikpbjjahbpjjlbaengkocckppdkmbh.chromiumapp.org/`.
- The OAuth client type is Web application, which is correct for the current implementation because the code uses `chrome.identity.launchWebAuthFlow` with `chromiumapp.org` redirect URIs.
- Manifest was not changed for OAuth and no manifest `"key"` field was added.
- Current extension usage / OAuth appears to work for current extension usage / dev ID behavior; production-ID OAuth still must be tested on CWS extension ID `hgkankpnpgoikbcggnlnlgddmnkendof` before submit review.
- To test production-ID OAuth before submit review, use a CWS trusted tester / draft install flow if available, or temporarily pin manifest `"key"` only if explicitly chosen later.
- `options.html` enterprise enquiry intentionally remains `info@debutt.studio`.
- Support and bug-report email should use `support@debutt.studio`.

## Suggested Category
Productivity or Workflow & Planning

## Support Email
support@debutt.studio
