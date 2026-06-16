# Pullhub Chrome Web Store Listing Draft

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
- Google `drive.metadata`: Locates and checks metadata for the Pullhub Uploads folder and related Drive files used by the fallback workflow; Pullhub does not read Drive file contents through this scope.
- Google `userinfo.email`: Shows the signed-in account, links account state to Pullhub access, and supports Firebase sharing ownership.
- Drive fallback public-link behavior: If direct Slides insertion fails, Pullhub may upload an image to the user's Drive and set that fallback file so anyone with the link can view it, only so Google Slides can render the image.
- Firebase/Firestore: Used only for optional public board sharing. Shared boards store a snapshot of the board data needed for the public link.
- ExtensionPay/Stripe: Used for trial, subscription, and Pro access management.

## Store Listing URLs
- Homepage: `https://debutt.studio/`
- Privacy Policy: `https://debutt.studio/privacy.html`
- Support: `https://debutt.studio/support.html`
- Terms: `https://debutt.studio/terms.html`

## Suggested Category
Productivity or Workflow & Planning

## Support Email
support@debutt.studio
