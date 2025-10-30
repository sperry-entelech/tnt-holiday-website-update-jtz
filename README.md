# TNT Tacky Lights - Website Integration Package

**For JTZ Web Team**
Complete marketing campaign materials ready for website integration.

---

## 📦 What's Included

This repository contains **production-ready** static files for the TNT Tacky Lights 2025 marketing campaign. Everything is designed to integrate seamlessly into the existing TNT website with minimal technical setup.

### Components:

1. **Holiday Promotional Popup** - Capture attention on homepage
2. **Interactive Map Landing Page** - 61 Richmond-area locations with insider tips
3. **Lead Magnet PDFs** - Premium downloadable guides
4. **Website Popup Widget** - Add to any page for lead capture

---

## 🚀 Quick Start: What JTZ Needs to Do

### Component 1: Holiday Popup (High Priority)
**File:** `popup-example.html`
**Purpose:** Eye-catching holiday promotion that appears on your main website

**Integration Steps:**
1. Open `popup-example.html` in browser to preview
2. Copy the CSS (inside `<style>` tags) to your site's stylesheet
3. Copy the HTML (inside `<div class="holiday-popup">`) to your site template
4. Copy the JavaScript (inside `<script>` tags) to your site's JS file
5. Update the link `href="landing-page.html"` to point to your hosted landing page URL

**Notes:**
- Popup appears after 2 seconds
- Shows once per session (uses localStorage)
- Mobile responsive
- Easy to dismiss

---

### Component 2: Interactive Map Landing Page
**File:** `landing-page.html`
**Purpose:** Main destination where users sign up to receive guides

**Integration Steps:**
1. Upload `landing-page.html` to your web hosting
2. Upload the `images/` folder to the same directory
3. Ensure `tacky-lights-database.json` is in the same directory
4. **Update Form Action:** Change line 387 from:
   ```html
   <form id="download-form" action="YOUR_FORM_HANDLER_URL" method="POST">
   ```
   To your actual form processing endpoint (e.g., your CRM or email handler)
5. Test form submission

**Dependencies (Loaded from CDN - No Installation Needed):**
- Leaflet.js v1.9.4 (mapping library)
- OpenStreetMap tiles (free, no API key required)

**Current URL to update in popup:** Once hosted, update the popup's link to point here.

---

### Component 3: Full Interactive Map Experience
**File:** `interactive-map.html`
**Purpose:** Standalone map page with all 61 locations, parking tips, and traffic insights

**Integration Options:**

**Option A: Standalone Page (Recommended)**
1. Upload `interactive-map.html` to your site
2. Upload `images/` folder
3. Upload `tacky-lights-database.json`
4. Link to it from your main navigation or holiday promotions section

**Option B: Embed in Existing Page**
1. Create an iframe on any existing page:
   ```html
   <iframe src="interactive-map.html" width="100%" height="800px" frameborder="0"></iframe>
   ```

**Features:**
- 61 pre-loaded Richmond-area locations
- Parking difficulty ratings
- Best viewing times
- Traffic intensity indicators
- Mobile-optimized with geolocation
- No external APIs needed

---

### Component 4: Lead Magnet PDFs
**Files:**
- `TNT-Drivers-Insider-Guide.html`
- `TNT-Tacky-Lights-Checklist.html`

**Current Status:** These are HTML files that need to be converted to PDFs

**Integration Steps:**
1. **Convert to PDF:**
   - Open each HTML file in Chrome/Edge
   - Right-click → "Print" → "Save as PDF"
   - Use settings: Letter size, no headers/footers, background graphics enabled

2. **Host the PDFs:**
   - Upload PDFs to your web hosting (e.g., `/downloads/tacky-lights-guide.pdf`)

3. **Update Landing Page Form:**
   - After form submission, redirect users to the PDF download URLs
   - Or email PDFs automatically via your form handler

**Alternative:** I can convert these to PDFs for you if needed.

---

## 📁 File Structure

```
tnt-tacky-lights/
├── README.md                              # This file
├── popup-example.html                     # Holiday popup widget
├── landing-page.html                      # Main landing page with form
├── interactive-map.html                   # Full map experience
├── TNT-Drivers-Insider-Guide.html         # Lead magnet (needs PDF conversion)
├── TNT-Tacky-Lights-Checklist.html       # Lead magnet (needs PDF conversion)
├── tacky-lights-database.json            # Location data (61 locations)
└── images/
    ├── tacky-lights-1.jpg                # Map popup images
    ├── tacky-lights-2.jpg
    ├── tacky-lights-3.jpg
    ├── tacky-lights-4.jpg
    └── tnt-logo-white.png                # TNT branding
```

---

## 🎨 Design System

**Color Palette:**
- Primary Black: `#000000`
- Accent Red: `#DC143C` (Crimson)
- Premium Gold: `#FFD700`
- Background: Black with red accents
- Text: White and gold on black backgrounds

**Fonts:**
- Headlines: Georgia, serif (classic luxury)
- Body: System fonts (Arial, Helvetica, sans-serif)
- All fonts are standard - no external font loading required

**Branding:**
- TNT logo in white for dark backgrounds
- Holiday-themed with luxury aesthetic
- Mobile-first responsive design

---

## 🔧 Technical Specifications

### No Complex Setup Required ✅
- **No database** needed
- **No API keys** required (uses free OpenStreetMap)
- **No build process** - pure HTML/CSS/JavaScript
- **No Node.js, npm, or dependencies** to install
- **No environment variables** to configure

### Browser Compatibility
- Chrome, Firefox, Safari, Edge (last 2 versions)
- Mobile Safari (iOS 12+)
- Chrome Mobile (Android 8+)

### Performance
- All assets optimized
- External libraries loaded from CDN (fast, cached)
- Images compressed for web
- Minimal JavaScript (vanilla, no frameworks)

### External Dependencies (CDN-loaded)
1. **Leaflet.js** - https://unpkg.com/leaflet@1.9.4/
   - Free, open-source mapping library
   - No API key required
   - Uses OpenStreetMap tiles (also free)

---

## 📋 Integration Checklist for JTZ

- [ ] **Test all HTML files locally** (open in browser)
- [ ] **Upload files to web hosting**
  - [ ] landing-page.html
  - [ ] interactive-map.html
  - [ ] popup-example.html
  - [ ] tacky-lights-database.json
  - [ ] images/ folder (all 5 images)
- [ ] **Update form action** in landing-page.html (line 387)
- [ ] **Integrate popup code** into main website
- [ ] **Convert lead magnets to PDF**
  - [ ] TNT-Drivers-Insider-Guide.html → PDF
  - [ ] TNT-Tacky-Lights-Checklist.html → PDF
- [ ] **Upload PDFs** to hosting
- [ ] **Update popup link** to point to hosted landing-page.html
- [ ] **Test form submissions** (verify emails/CRM integration)
- [ ] **Test on mobile devices**
- [ ] **Test map functionality** (clicks, popups, geolocation)

---

## 🎯 Marketing Campaign Flow

1. **Visitor lands on TNT website** → Sees holiday popup after 2 seconds
2. **Clicks "Plan Your Route"** → Goes to landing page
3. **Explores interactive map** → Views 61 locations with insider tips
4. **Fills out form** → Submits name and email
5. **Receives lead magnets** → Downloads driver's guide and checklist
6. **TNT captures lead** → Email goes to your CRM/mailing list

---

## 🔒 Privacy & Data

**Form Data Collection:**
- Currently set to `action="YOUR_FORM_HANDLER_URL"`
- **JTZ must configure** this to point to your form processor
- Consider GDPR/privacy policy compliance for email collection
- Recommend adding privacy policy link to form

**No Tracking:**
- No Google Analytics included (add if desired)
- No third-party tracking pixels
- Local storage only used for popup display preference

---

## 🆘 Support & Questions

**Technical Issues:**
- All files are standard HTML/CSS/JS - any web developer can integrate
- Test thoroughly in staging environment before production

**Need Help?**
- Files are self-contained and well-commented
- Map uses standard Leaflet.js (extensive documentation available)
- Form integration depends on your existing backend

---

## 📊 What Makes This Package Web-Team-Friendly

✅ **No complex dependencies** - Just upload and integrate
✅ **No API keys to manage** - Uses free OpenStreetMap
✅ **No build process** - Pure HTML, ready to deploy
✅ **No database setup** - All data in JSON file
✅ **Mobile responsive** - Works on all devices
✅ **Well commented code** - Easy to customize
✅ **Standard technologies** - HTML, CSS, vanilla JS

---

## 🚀 Ready to Launch

This package is **production-ready**. All JTZ needs to do is:
1. Upload files to your web hosting
2. Update the form action URL
3. Integrate popup code into main site
4. Convert and host the PDF lead magnets

**Estimated Integration Time:** 2-3 hours for experienced web developer

---

## 📝 Version Info

- **Created:** October 30, 2025
- **Campaign:** TNT Tacky Lights 2025
- **Season:** December 2025 holidays
- **Total Locations:** 61 Richmond-area displays
- **Lead Magnets:** 2 premium downloadable guides

---

## 🎁 Bonus: What's Already Done for You

- ✅ 61 locations researched and verified
- ✅ Parking difficulty assessed for each location
- ✅ Best viewing times determined
- ✅ Traffic patterns analyzed
- ✅ Mobile-responsive design implemented
- ✅ Professional luxury branding applied
- ✅ Lead magnet content written
- ✅ Interactive map fully functional
- ✅ Form validation included
- ✅ Popup behavior optimized (session-based, dismissible)

**JTZ just needs to integrate - all the hard work is done!**

---

## Questions?

Contact your TNT point of contact or refer to this README for integration guidance.

**Happy Holidays! 🎄✨**
