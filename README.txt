PESOPLAN — CLOUD SYNC + PHONE/COMPUTER APP

WHAT THIS VERSION DOES
- Preserves the existing PesoPlan tracker, categories, forms, wishlist, reports and history.
- Keeps local browser saving as an offline/local fallback.
- Adds Supabase email/password account sign-in and sign-up.
- Stores one private JSON record per user in Supabase.
- First sign-in uploads this browser's existing data if the cloud account has no record.
- If cloud data already exists, it becomes the active data on this device. A copy of this
  browser's pre-login data is kept in localStorage under pesoplan_data_v1_before_cloud_login.
- Sync checks for remote changes every 15 seconds and when the app regains focus.
- Uses Row Level Security so signed-in users can only access their own row.

IMPORTANT: CLOUD SETUP IS REQUIRED BEFORE THE CLOUD BUTTON CAN WORK.

A. CREATE A SUPABASE PROJECT
1. Go to https://supabase.com/ and create a free account/project.
2. In the project dashboard, open Project Settings > API (or API Keys).
3. Copy the Project URL.
4. Copy the Publishable key (or legacy anon/public key).
   NEVER copy a service_role key or secret key into the website.

B. CREATE THE DATABASE TABLE
1. Open SQL Editor in your Supabase project.
2. Open the included supabase-setup.sql file in a text editor.
3. Copy all SQL and run it in Supabase SQL Editor.
   This creates the table and user-only Row Level Security policies.

C. ADD YOUR PROJECT SETTINGS
1. Open supabase-config.js in a text editor.
2. Replace YOUR_SUPABASE_PROJECT_URL with your Project URL.
3. Replace YOUR_SUPABASE_PUBLISHABLE_OR_ANON_KEY with your Publishable/anon key.
4. Save the file.

D. PUBLISH THE WEBSITE FOR BOTH DEVICES
1. Create a GitHub repository named pesoplan.
2. Upload ALL files and folders from this package, keeping their structure.
3. In GitHub: Settings > Pages > Deploy from a branch.
4. Choose main and /(root), then Save.
5. Wait for GitHub Pages to publish your HTTPS website.

E. AUTHENTICATION EMAIL SETTINGS
Supabase may require email confirmation for new accounts. Check Authentication > URL Configuration
and set your Site URL to the published GitHub Pages URL. Add that URL to the allowed redirect URLs.
For a simple email/password flow, confirm the email if Supabase sends a confirmation message.

F. INSTALL ON DEVICES
- Android: open the published URL in Chrome > menu > Install app / Add to Home screen.
- iPhone: open the published URL in Safari > Share > Add to Home Screen.
- Computer: open the published URL in Chrome or Edge and use the install icon/menu if offered.
Sign in using the SAME PesoPlan email/password on every device.

DATA AND SYNC NOTES
- Cloud sync requires internet. Without internet, the app continues to save locally in that browser.
- When online, it checks for changes every 15 seconds and when the page is focused.
- This starter uses a single-record, last-write-wins sync model. Avoid editing the same account
  simultaneously on multiple devices; the most recent saved version may replace an earlier one.
- Existing local data is uploaded on the first sign-in only when the cloud row does not exist.
- If the cloud row already exists, it is loaded and local pre-login data is backed up in that
  browser's localStorage. Use the app's Export Backup before connecting if you want an extra copy.
- Local browser storage is not a substitute for cloud backup. Export backups regularly.
- Do not share your password or secret/service_role keys.
