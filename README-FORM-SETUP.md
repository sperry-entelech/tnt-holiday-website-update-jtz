# Form Setup Package for JTZ

**Created:** 2025-11-11
**Purpose:** Complete form processing solution for TNT Tacky Lights landing page

---

## 📦 WHAT'S IN THIS PACKAGE

### 1. **EMAIL-TO-JTZ-FORM-SETUP.md**
**Use this:** Email instructions for JTZ developers explaining how to set up the form

**Summary:**
- Tells them to use their existing form handler (simplest approach)
- Lists all form fields to process
- Provides email notification template
- Includes optional Google Analytics tracking code

**Action:** Copy this content and send to JTZ team

---

### 2. **form-handler.php** (Backup Option)
**Use this if:** JTZ doesn't have an existing form handler or wants a dedicated script

**Features:**
- ✅ Complete PHP form processing script
- ✅ Email notifications with HTML formatting
- ✅ "Hot lead" alerts when tour interest is checked
- ✅ Input validation and sanitization
- ✅ Spam prevention (rate limiting)
- ✅ CSV logging (automatic lead tracking)
- ✅ Security features (SQL injection protection)

**Setup Instructions:**
1. Update line 14: `define('RECIPIENT_EMAIL', 'sedan@tntauto.com');`
2. Upload to JTZ web server
3. Update landing-page.html line 536: `action="form-handler.php"`

---

### 3. **FORM-TESTING-GUIDE.md**
**Use this:** Complete testing checklist for JTZ before going live

**Includes:**
- 7-step testing process
- 5 test cases with expected results
- Mobile & browser compatibility checks
- Security testing procedures
- Troubleshooting common issues
- Production readiness checklist

**Action:** Send to JTZ QA team for pre-launch testing

---

## 🚀 RECOMMENDED IMPLEMENTATION PATH

### **OPTION A: Fast Track (Recommended for This Week Launch)**

**Step 1:** Send `EMAIL-TO-JTZ-FORM-SETUP.md` to JTZ
**Step 2:** JTZ points form to their existing contact form handler
**Step 3:** Test using `FORM-TESTING-GUIDE.md`
**Step 4:** Go live

**Time to deploy:** 1-2 hours

**Pros:**
- Uses proven infrastructure (their existing form handler)
- Minimal setup required
- Familiar workflow (email notifications)
- Can go live this week

**Cons:**
- No dedicated tracking for this campaign
- Manual lead management

---

### **OPTION B: Custom Script (If JTZ Doesn't Have Existing Handler)**

**Step 1:** Send `form-handler.php` to JTZ
**Step 2:** JTZ uploads to web server and configures
**Step 3:** Update landing-page.html to point to form-handler.php
**Step 4:** Test using `FORM-TESTING-GUIDE.md`
**Step 5:** Go live

**Time to deploy:** 2-4 hours

**Pros:**
- Dedicated form processor for this campaign
- Automatic CSV logging (built-in lead tracking)
- Hot lead alerts in email
- Pretty HTML email formatting

**Cons:**
- Requires PHP configuration on server
- Slight learning curve if JTZ hasn't used custom PHP before

---

## 📧 WHAT TO SEND TO JTZ

### Immediate Action (Today):

**Email Subject:** Tacky Lights Form Setup - Simple Instructions

**Email Body:**
```
Hi JTZ Team,

I've created complete form setup documentation for the tacky lights landing page.

**RECOMMENDED APPROACH (Fastest):**
Please use your existing contact form handler that already sends emails to sedan@tntauto.com.

Full instructions attached: EMAIL-TO-JTZ-FORM-SETUP.md

**BACKUP OPTION:**
If you don't have an existing handler or prefer a dedicated script, I've also included:
- form-handler.php (ready-to-use PHP script)
- FORM-TESTING-GUIDE.md (complete testing checklist)

**Timeline:**
We need this live this week for the holiday season. The recommended approach should take 1-2 hours to implement and test.

Let me know if you have any questions!

Thanks,
[Your name]
```

**Attachments:**
1. EMAIL-TO-JTZ-FORM-SETUP.md
2. form-handler.php
3. FORM-TESTING-GUIDE.md

---

## 🔍 HOW THE FORM WORKS

### User Flow:
1. User fills out form on landing-page.html
2. Clicks "Get My Free Guide Now" button
3. Client-side JavaScript validates required fields
4. Form submits to form handler (POST request)
5. Form handler processes data and sends email
6. User sees success message

### Email Notification:
- **To:** sedan@tntauto.com
- **Subject:** "New Tacky Lights Lead: [First Name] [Last Name]"
- **Body:** HTML formatted email with all form data
- **Special Alert:** If user checked "tour interest" → **HOT LEAD** flag appears

### Data Collected:
- **Required:** First Name, Last Name, Email, Phone
- **Optional:** Tour Date, Group Size
- **Flag:** Tour Interest checkbox (YES/NO)

---

## 📊 TRACKING OPTIONS

### Basic (Included in form-handler.php):
- CSV log file: `tacky-lights-leads.csv`
- Automatically tracks: timestamp, contact info, tour interest, IP address
- Can open in Excel/Google Sheets for analysis

### Advanced (Optional - Set Up After Holidays):
- Google Analytics event tracking (code included in EMAIL-TO-JTZ-FORM-SETUP.md)
- n8n workflow integration (build later)
- Zapier/Make.com automation
- Direct Zoho integration

---

## 🛡️ SECURITY FEATURES

### Built into form-handler.php:
- ✅ Input sanitization (prevents XSS attacks)
- ✅ Email validation (prevents spam)
- ✅ Rate limiting (prevents bot submissions)
- ✅ SQL injection protection
- ✅ CSRF protection via session checks

### What You Don't Need to Worry About:
- Database security (no database used)
- Credit card processing (not collecting payment info)
- GDPR compliance for EU (focus is Richmond, VA locals)

---

## 🎯 SUCCESS METRICS TO TRACK

### Week 1:
- Total form submissions
- Hot leads (tour interest checked) vs guide-only downloads
- Most popular group sizes
- How many people select dates vs leave blank

### Conversion Tracking:
- Form fills → dispatcher follow-up calls
- Calls → actual bookings
- Revenue generated from this campaign

### Quality Indicators:
- Are leads legitimate? (vs spam)
- Are "hot leads" actually converting?
- What's the average response time from form submission to dispatcher contact?

---

## ❓ FAQ FOR JTZ

**Q: Do we need to create a thank-you page?**
A: Not required. The form can show an in-page success message. If you want a thank-you page later, we can add it.

**Q: How do we send the PDFs to customers?**
A: For now, manually email them after receiving the lead notification. Post-holidays, we can automate this.

**Q: What if our existing form handler doesn't work?**
A: Use the form-handler.php script I provided. It's plug-and-play ready.

**Q: Can we track which leads came from this specific page?**
A: Yes - the email subject line says "Tacky Lights Lead" and the CSV log tracks the source. If you use Google Analytics, you can also track form conversions.

**Q: What if we get spam submissions?**
A: The form-handler.php has built-in spam prevention (rate limiting). If you still get spam, we can add CAPTCHA later.

**Q: Can we customize the email format?**
A: Yes - just edit the HTML template in form-handler.php lines 120-180.

---

## 🔧 TECHNICAL REQUIREMENTS

### Server Requirements (if using form-handler.php):
- PHP 7.0 or higher
- mail() function enabled (or PHPMailer installed)
- Write permissions for CSV logging (optional)

### Browser Requirements (User-facing):
- Modern browsers: Chrome, Firefox, Safari, Edge (last 2 versions)
- Mobile: iOS 12+, Android 8+
- JavaScript enabled (for validation and formatting)

---

## 📞 NEXT STEPS

### Your Action Items:
1. ✅ Send EMAIL-TO-JTZ-FORM-SETUP.md to JTZ developers
2. ⏳ Wait for JTZ to implement (1-2 hours)
3. ✅ Test form using FORM-TESTING-GUIDE.md
4. ✅ Approve for production launch
5. 📊 Monitor first week of submissions

### JTZ Action Items:
1. Choose implementation path (existing handler vs custom script)
2. Update landing-page.html form action attribute
3. Complete testing checklist
4. Deploy to production
5. Send test submission to verify email delivery

---

## 🎄 POST-LAUNCH ENHANCEMENTS (Optional)

After the holiday season, if the campaign performs well:

### Phase 2 Upgrades:
1. **Automated PDF delivery** - Send guide immediately after form submission
2. **n8n workflow** - Automatic lead routing, CRM integration, email sequences
3. **Lead scoring** - Prioritize hot leads based on form data
4. **Retargeting** - Facebook pixel tracking for ad campaigns
5. **A/B testing** - Test different form copy/layouts

### Estimated Time for Phase 2:
- 4-6 hours to build n8n workflow
- 2-3 hours for automated PDF delivery
- 1 hour for lead scoring logic

**But for now: Keep it simple. Get it live this week.**

---

## ✅ FINAL CHECKLIST

Before sending to JTZ:

- [x] Email instructions created (EMAIL-TO-JTZ-FORM-SETUP.md)
- [x] Backup PHP script ready (form-handler.php)
- [x] Testing guide prepared (FORM-TESTING-GUIDE.md)
- [x] Summary documentation written (this file)
- [ ] Send package to JTZ team
- [ ] Schedule follow-up call to answer questions
- [ ] Set reminder to check first submissions

---

**Questions?** Review the FAQ section above or contact JTZ directly.

**Ready to launch?** Send the package to JTZ and get this campaign live! 🚀
