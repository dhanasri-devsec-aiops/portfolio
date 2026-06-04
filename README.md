# Dhanasri Dasari — DevSecOps Command Center Portfolio

## Bug Fixes Applied

### Bug 1: AI Copilot — "Sorry, I had trouble connecting"
**Root Cause:** The original code called `https://api.anthropic.com/v1/messages` 
directly from the browser. This fails with a CORS error because:
- The Anthropic API blocks browser-side requests (no CORS headers)
- API keys cannot be safely embedded in client HTML
- No backend proxy was configured

**Fix:** Replaced the entire AI section with a client-side rule-based knowledge 
base using keyword matching. Zero API calls. Never fails. Instant responses with 
a realistic 600ms typing delay. Covers all questions about Dhanasri's skills, 
projects, and experience.

---

### Bug 2: "Hire Me" button did nothing
**Root Cause:** `openLink()` was called by every external button 
(Hire Me, Email, LinkedIn, GitHub) but was **never defined** in the script.
JavaScript threw `ReferenceError: openLink is not defined` silently.

**Fix:** 
- Defined `openLink(url)` with `window.open()` and error handling
- "Hire Me" now opens a professional contact modal with:
  - Name, Email, Phone, LinkedIn, GitHub info
  - Send Email / Open LinkedIn / Download Resume / Schedule Interview buttons
- Toast notification confirms each action

---

### Bug 3: All other broken buttons
**Root Cause:** Same as above — `openLink` undefined, causing silent failures for:
- LinkedIn button (hero section)
- GitHub button (hero section)  
- Recruiter panel contact buttons
- Contact section links

**Fix:** All buttons now work. Added `openLink()`, fixed `scroll2()` renamed 
to `scrollTo2()` (avoids shadowing `window.scroll`), added toast notifications.

---

### Bug 4: Progress bar animation never fired
**Root Cause:** Original code used broken `style.match(/width:([^;]+)/)` 
regex on data that was never set. Bars stayed at 0%.

**Fix:** Added `data-width` attributes on each bar, used `IntersectionObserver` 
to animate when scrolled into view.

---

## How to Run Locally

```bash
# Option 1: Open directly in browser
open index.html

# Option 2: Serve with Python
python3 -m http.server 8080
# Visit http://localhost:8080

# Option 3: Serve with Node.js
npx serve .
# Visit http://localhost:3000
```

## Features
- ✅ AI Copilot (fully offline, no API needed)
- ✅ Hire Me modal with contact info and action buttons
- ✅ All nav links scroll to correct sections
- ✅ Recruiter View toggle with toast notification
- ✅ Progress bars animate on scroll
- ✅ Architecture nodes clickable with toast feedback
- ✅ Toast notification system (success/info/error/warning)
- ✅ ESC key closes modal
- ✅ Click outside modal to close
- ✅ Animated canvas particle background
- ✅ Live IST clock in status bar
- ✅ Fully responsive

## Contact
- Email: dhanasri.elr@gmail.com
- Phone: +91 9483480561
- LinkedIn: linkedin.com/in/dhanasri-devsecops
- GitHub: github.com/dhanasri-devsec-aiops
