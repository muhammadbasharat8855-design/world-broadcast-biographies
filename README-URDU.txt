WORLD BROADCAST BIOGRAPHIES — ADMIN SETUP
==========================================

Admin email already entered in the login page:
Muhammadbasharat8855@gmail.com

WHAT THIS PACKAGE CONTAINS
- admin.html: private admin login and biography publishing panel
- biographies.html: public biographies page
- admin-config.js: public Supabase project settings (two placeholders only)
- schema.sql: database table
- functions/api/[[path]].js: protected server API
- assets/wbb.css: admin/public biography styling

IMPORTANT
- The login uses a secure email sign-in link (magic link), not a dummy password.
- The admin account must first be invited/created in Supabase Authentication.
- GitHub Pages alone cannot run the protected API. Deploy this same GitHub repository using Cloudflare Pages.
- NEVER put a Supabase service_role/secret key in admin-config.js or any public GitHub file.
- Do not send passwords or secret keys in ChatGPT.

SETUP — FOLLOW IN THIS ORDER

1) SUPABASE DATABASE
Open https://supabase.com/dashboard and select your existing project.
Open SQL Editor > New query.
Open schema.sql from this package, copy all its contents, paste into SQL Editor, and press Run.
Then open Storage and create a bucket named:
biography-images
Set the bucket to Public.

2) SUPABASE ADMIN USER
Open Authentication > Users.
Invite this exact email:
Muhammadbasharat8855@gmail.com
Accept the invitation from your Gmail inbox.
The website checks this exact email as the only allowed administrator.

3) SUPABASE PUBLIC CONFIG
Open Project Settings > API.
Copy:
- Project URL
- anon / publishable public key
Open admin-config.js in the GitHub repository and replace only:
PASTE_SUPABASE_PROJECT_URL_HERE
PASTE_SUPABASE_ANON_OR_PUBLISHABLE_KEY_HERE
Do not use the service_role key here.

4) UPLOAD PACKAGE FILES TO GITHUB
Extract this ZIP.
Upload these items into the ROOT of your existing repository:
- admin.html
- biographies.html
- admin-config.js
- assets/ (whole folder)
- functions/ (whole folder, including api/[[path]].js)
- schema.sql (optional to keep as a reference)
Do not delete or overwrite your existing index.html, style.css, or script.js.

5) CLOUDFLARE PAGES
Open https://dash.cloudflare.com
Workers & Pages > Create > Pages > Connect to Git.
Choose your existing GitHub repository.
Framework preset: None
Build command: leave empty
Build output directory: /
Deploy.

6) CLOUDFLARE SECRETS
In Cloudflare Pages > your project > Settings > Variables and Secrets, add:
SUPABASE_URL = your Supabase Project URL
SUPABASE_ANON_KEY = your anon/publishable public key
SUPABASE_SERVICE_ROLE_KEY = your Supabase service_role/secret key (mark as SECRET)
ADMIN_EMAIL = Muhammadbasharat8855@gmail.com
Save and redeploy.
The service_role key belongs ONLY in Cloudflare Secrets, never in GitHub files.

7) AUTH REDIRECT URL
After Cloudflare gives your site URL, open Supabase > Authentication > URL Configuration.
Add this Redirect URL:
https://YOUR-CLOUDFLARE-SITE.pages.dev/admin.html
Replace the example domain with your actual Cloudflare Pages domain.

8) LOGIN
Open:
https://YOUR-CLOUDFLARE-SITE.pages.dev/admin.html
The email is already filled in. Press Send login link.
Open the link received in Gmail. Then add biographies, upload a photo, and publish.
Public biographies appear at:
https://YOUR-CLOUDFLARE-SITE.pages.dev/biographies.html

WHAT IS NOT DONE AUTOMATICALLY
This package cannot sign into your Supabase or Cloudflare accounts or create the Auth user for you.
Those account actions must be completed inside your own logged-in dashboard. The package is configured for your email, but the two Supabase public settings and Cloudflare secrets still need your project's own values.
