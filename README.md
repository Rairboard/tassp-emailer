# TASSP Mass Emailer
**A Chrome extension for contacting all 150 Texas House representatives — one form at a time.**

Built for TASSP (Texas Association of School Social Workers) advocates during the 89th Texas Legislature session. The extension auto-fills your contact information and personalized message on each representative's email form. You review every message and click Submit yourself — the extension never sends anything without you.

🌐 **[Download & Install → rairboard.github.io/tassp-emailer](https://rairboard.github.io/tassp-emailer)**

---

## Features
- ✅ Auto-fills all 150 Texas House district email forms
- ✅ Personalizes the message with each rep's name using `[REP_NAME]`
- ✅ 3-second delay before filling — lets the page load fully before injecting values
- ✅ You submit every form manually — zero auto-sending
- ✅ Automatically advances to the next district after confirmation
- ✅ Detects and retries if a validation error occurs
- ✅ All data stays local — nothing leaves your browser

---

## Quick Install
1. Download `tassp-emailer.zip` from the [website](https://rairboard.github.io/tassp-emailer)
2. Unzip the file
3. Go to `chrome://extensions` in Chrome
4. Enable **Developer Mode** (top-right toggle)
5. Click **Load unpacked** → select the unzipped `tassp-v6` folder
6. The extension icon appears in your Chrome toolbar — you're ready

---

## How to Use
1. Click the extension icon and fill in your contact info + message template once
2. Use `[REP_NAME]` in your message where the representative's name should go
3. Click **Start Campaign** — the extension opens District 1's email page and fills everything
4. Review the form, make any edits, then click **Send Message**
5. The extension detects the confirmation and loads the next district automatically
6. Repeat for all 150 districts

---

## Repository Structure
```
tassp-v6/
├── manifest.json    # Extension config, permissions, URL matches
├── background.js    # Service worker — campaign state, navigation logic
├── content.js       # Page script — autofill, confirmation detection
├── popup.html       # Extension popup UI
├── popup.js         # Popup logic — save info, start/stop
├── index.html       # GitHub Pages landing page with download button
└── README.md        # This file
```

---

## URL Handling
| Page | What the extension does |
|------|------------------------|
| `/members/*/email` | Waits 3 seconds, then autofills the form |
| `/members/*/email/process` | Validation error — redirects back to the same rep's form |
| `/members/*/email/thankyou` | Success — advances to the next district |

---

## Permissions
| Permission | Why it's needed |
|------------|----------------|
| `tabs` | Navigate between representative pages |
| `storage` | Save contact info and campaign progress locally |
| `scripting` | Inject autofill into Texas House pages |
| `host_permissions: house.texas.gov` | Scoped only to the Texas House website |

No data is collected or sent anywhere outside the Texas House website.

---

## Deployment
This repo uses **GitHub Pages** to host the landing page (`index.html`). To deploy your own copy:
1. Fork or clone this repo
2. Go to **Settings → Pages**
3. Set source to **main branch / root**
4. Your site will be live at `https://rairboard.github.io/tassp-emailer`
5. Update the download link in `index.html` to match your repo URL

---

## Disclaimer
This tool is not affiliated with or endorsed by the Texas House of Representatives or any government entity. It is an independent advocacy tool to help constituents contact their elected representatives.

---
*v2.1 · Chrome Extension · 89th Texas Legislature*
