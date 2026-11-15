BROADCAST BIOGRAPHIES — WEBSITE FILES

WHAT IS INCLUDED
- index.html: public website
- admin.html: private sign-in and biography management page
- assets/: design and website scripts
- supabase-setup.sql: database table and security rules

IMPORTANT
This website uses Supabase for login and database storage. Do not upload a Supabase service_role key anywhere in these files. Only the project URL and anon/public key belong in assets/config.js.

SETUP (ONE TIME)
1. Create a free project at https://supabase.com/
2. In Supabase, open SQL Editor, create a new query, paste all of supabase-setup.sql and run it.
3. In supabase-setup.sql, replace admin@example.com with the exact administrator email BEFORE running the SQL. If already run, edit the email in the policies and run the script again.
4. In Supabase, open Project Settings > API. Copy Project URL and anon/public key.
5. Open assets/config.js and replace the two PASTE_... values with your Project URL and anon/public key.
6. In Supabase Authentication, create a user with the same admin email and a strong password. Use that email/password at admin.html.
7. Upload ALL files and folders from this ZIP into the ROOT of your GitHub Pages repository. Keep the assets folder and its files together.
8. Open your website URL. Public biographies marked Published appear on the home page. Open /admin.html to sign in and add/edit/delete biographies.

ADDING A BIOGRAPHY
Admin panel > sign in > fill in the name, role, country, photo URL, biography and optional LinkedIn post URL > choose Publish > Save biography.

LINKEDIN NOTE
This lets you attach a LinkedIn post URL to a biography. It does NOT automatically import every post from a personal LinkedIn profile. That requires LinkedIn API access and permissions.

PHOTO NOTE
For now, paste a publicly accessible image URL. Do not paste a private/local phone file path.

TROUBLESHOOTING
- "Complete Supabase setup": config.js still has placeholder values.
- Login fails: confirm the user exists in Supabase Authentication and email matches the email in SQL policies.
- Website shows no stories: confirm the SQL ran, the row is Published, and the browser config has the correct URL and anon key.
- Never share your Supabase password or service_role key.

This package is a ready-to-configure website starter. The Supabase project and one-time settings above are required before login and online publishing can work.