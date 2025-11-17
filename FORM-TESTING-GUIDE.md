# Form Testing Guide for JTZ Developers

**Purpose:** Ensure the tacky lights landing page form works correctly before going live

---

## PRE-LAUNCH TESTING CHECKLIST

### ✅ Step 1: Backend Setup Verification

- [ ] Form handler endpoint is configured (either existing or new PHP script)
- [ ] Email recipient address is correct: `sedan@tntauto.com`
- [ ] Test email was received successfully
- [ ] Email contains all form fields
- [ ] HTML email renders correctly (not showing as plain text)

---

### ✅ Step 2: Form Functionality Tests

#### Test Case 1: Complete Form Submission (Happy Path)
**Fill out:**
- First Name: "John"
- Last Name: "Smith"
- Email: "john.smith@test.com"
- Phone: "8045551234"
- Tour Date: Select tomorrow's date
- Group Size: "5-8 people"
- ✅ Check "I'm interested in booking a professional tacky lights tour"

**Expected Result:**
- ✅ Form submits successfully
- ✅ Success message displays
- ✅ Email arrives at sedan@tntauto.com with subject: "New Tacky Lights Lead: John Smith"
- ✅ Email body shows "Tour Interest: YES" and includes the **HOT LEAD** warning
- ✅ All fields are populated in the email
- ✅ Phone number is formatted: (804) 555-1234

---

#### Test Case 2: Minimum Required Fields Only
**Fill out:**
- First Name: "Jane"
- Last Name: "Doe"
- Email: "jane@test.com"
- Phone: "5555551234"
- Leave tour date BLANK
- Leave group size BLANK
- ❌ DO NOT check tour interest checkbox

**Expected Result:**
- ✅ Form submits successfully
- ✅ Email shows "Tour Interest: No"
- ✅ Email shows "Preferred Date: Not specified"
- ✅ Email shows "Group Size: Not specified"
- ✅ NO hot lead warning appears

---

#### Test Case 3: Validation - Missing Required Fields
**Fill out:**
- First Name: "Test"
- Leave all other fields BLANK

**Expected Result:**
- ❌ Form does NOT submit
- ⚠️ Browser shows validation errors for empty required fields
- ⚠️ No email is sent

---

#### Test Case 4: Validation - Invalid Email Format
**Fill out:**
- First Name: "Test"
- Last Name: "User"
- Email: "notanemail" (invalid format)
- Phone: "1234567890"

**Expected Result:**
- ❌ Form does NOT submit
- ⚠️ Browser shows "Please enter a valid email address"
- ⚠️ No email is sent

---

#### Test Case 5: Phone Number Auto-Formatting
**Type in phone field:**
Start typing: "8041234567"

**Expected Result:**
- ✅ As you type, it auto-formats to: "(804) 123-4567"
- ✅ Formatted version is what appears in the email

---

### ✅ Step 3: Mobile Responsiveness Tests

**Test on:**
- [ ] iPhone (Safari)
- [ ] Android (Chrome)
- [ ] Tablet (iPad/Android tablet)

**Verify:**
- [ ] Form fields are easy to tap on mobile
- [ ] Date picker works on mobile devices
- [ ] Dropdown (group size) is accessible
- [ ] Submit button is visible without scrolling
- [ ] Success message displays properly on small screens
- [ ] No horizontal scrolling required

---

### ✅ Step 4: Browser Compatibility Tests

**Test in:**
- [ ] Chrome (latest version)
- [ ] Firefox (latest version)
- [ ] Safari (desktop + mobile)
- [ ] Edge (latest version)

**Verify:**
- [ ] Form displays correctly
- [ ] Phone formatting works
- [ ] Date picker functions
- [ ] Form submits successfully
- [ ] No JavaScript errors in console

---

### ✅ Step 5: Email Notification Quality Check

**Review the email that arrives and verify:**

- [ ] **Subject line** is clear: "New Tacky Lights Lead: [Name]"
- [ ] **From address** shows properly (not going to spam)
- [ ] **Reply-To** is set to customer's email (so you can reply directly)
- [ ] **All fields** are included in email body
- [ ] **Hot lead warning** appears when tour_interest is checked
- [ ] **Timestamp** is accurate
- [ ] **Email is readable** (not garbled HTML)
- [ ] **Links work** (email and phone links are clickable)

---

### ✅ Step 6: Security & Spam Prevention Tests

#### Test Case: Rapid Resubmission
**Action:**
Submit the form, then immediately submit again (within 3 seconds)

**Expected Result:**
- ⚠️ Second submission should be blocked with message: "Form submitted too quickly"
- This prevents bots from spamming the form

---

#### Test Case: SQL Injection Attempt (Security Check)
**Fill out:**
- First Name: `'; DROP TABLE users; --`
- Email: `test@test.com`
- Other required fields normally

**Expected Result:**
- ✅ Form submits successfully
- ✅ Email shows the literal string (not executed as code)
- ✅ No database errors occur
- This confirms input sanitization is working

---

### ✅ Step 7: Optional Features (If Implemented)

#### Google Analytics Tracking (If Added)
- [ ] Open Google Analytics Real-Time dashboard
- [ ] Submit form
- [ ] Verify event appears: "form_submit" with category "Tacky Lights Campaign"
- [ ] Check if event_label correctly shows "Tour Interest - Hot Lead" vs "Guide Download Only"

#### CSV Logging (If form-handler.php is used)
- [ ] Check if `tacky-lights-leads.csv` file was created in same directory as form-handler.php
- [ ] Verify it contains headers: Timestamp, First Name, Last Name, Email, Phone, Tour Interest, Date, Group Size, IP
- [ ] Verify each submission appends a new row
- [ ] Verify data is properly escaped (no CSV injection)

---

## COMMON ISSUES & TROUBLESHOOTING

### Issue: Email Not Received

**Check:**
1. Is the PHP mail() function working on your server?
   - Test with a simple mail() script
2. Is the email going to spam folder?
   - Check spam/junk folder
3. Is the "From" address valid?
   - Some servers require From address to match domain
4. Are there server logs showing mail errors?
   - Check PHP error logs

**Quick Fix:**
If mail() doesn't work, use PHPMailer or SendGrid instead.

---

### Issue: Form Submits But Page Doesn't Respond

**Check:**
1. Is the form handler returning proper JSON response?
2. Are there JavaScript errors in browser console? (Press F12)
3. Is CORS blocking the request?

**Quick Fix:**
Add this to the top of form-handler.php:
```php
header('Access-Control-Allow-Origin: *');
header('Content-Type: application/json');
```

---

### Issue: Phone Number Not Formatting

**Check:**
1. Is JavaScript enabled in browser?
2. Are there console errors?
3. Is the phone input field ID correct? (should be `id="phone"`)

**Quick Fix:**
Test in a different browser. This is client-side only and doesn't affect form submission.

---

### Issue: Date Picker Not Working on Mobile

**Check:**
1. Mobile browsers should use native date picker
2. Is the input type="date"?
3. Some older Android browsers don't support date inputs

**Quick Fix:**
It's okay if the native picker doesn't show - users can still type dates manually (YYYY-MM-DD format).

---

## PRODUCTION READINESS CHECKLIST

Before going live with real customers:

- [ ] All test cases above passed successfully
- [ ] Email notifications arriving within 1 minute
- [ ] Form works on mobile devices (iPhone & Android tested)
- [ ] No JavaScript console errors
- [ ] Form handler configured with correct recipient email
- [ ] Spam prevention working (rapid resubmission blocked)
- [ ] Success message is user-friendly and accurate
- [ ] No sensitive data is being logged insecurely
- [ ] SSL certificate is valid (https:// - secure connection)
- [ ] Form is accessible (can be filled out with keyboard only)

---

## POST-LAUNCH MONITORING

**Week 1 Actions:**

1. **Check daily** (first 3 days):
   - Are emails arriving?
   - Are there any spam submissions?
   - Are customers completing the form?

2. **Review form submissions**:
   - What percentage check "tour interest"?
   - What are common group sizes?
   - Are dates being selected or left blank?

3. **Track conversion**:
   - How many form fills → actual bookings?
   - Are hot leads (tour interest checked) converting better?

4. **Monitor issues**:
   - Any customer complaints about form not working?
   - Any emails bouncing?
   - Any spam submissions getting through?

---

## SUPPORT CONTACTS

**If you encounter issues:**

- **Technical Questions:** Contact Ethan (TNT team)
- **Email Delivery Issues:** Check with your hosting provider
- **PHP Errors:** Check server error logs (/var/log/apache2/error.log or similar)

---

## TEST DATA CLEANUP

**Before going live:**

- [ ] Delete all test submissions from email inbox
- [ ] Clear test entries from CSV log file (if using form-handler.php)
- [ ] Reset any analytics test data
- [ ] Remove any debug code or console.log() statements

---

**Ready to Launch?**

Once all checklist items are complete, the form is ready for production!

Good luck with the tacky lights campaign! 🎄
