# Campus Issue Tracker — GitHub Pages Demo

## Current version
- QR/location-aware issue reporting
- Camera or gallery photo selection
- Image compression before storage
- Current device date/time
- Optional browser GPS capture
- Anonymous-style report form (no name/phone field)
- Admin/staff/principal demo login
- Issue status tracking
- Public board
- Local demo storage

## IMPORTANT: how data is stored right now
This is a static HTML demo. Reports and compressed photos are stored in the browser's `localStorage`.

That means:
- Data is available only in that browser/device/origin.
- Opening the site on another phone does NOT show the same reports.
- Clearing browser/site data can remove the demo data.
- GitHub Pages hosts the files; it is NOT the database.

## Next step for a real college system
Replace the `store`/`db` functions with a shared backend such as:
- Supabase PostgreSQL for issue data
- Supabase Storage for photos
- Supabase Auth for admin/staff accounts
- Row Level Security for permissions

The frontend screens can remain largely the same.

## GitHub Pages
Upload `index.html` and `style.css` to a repository and enable GitHub Pages.

The QR-code page already allows the hosted website base URL to be entered so location QR codes can point to the real site.

## Security note
The passwords in this demo are only demo passwords. Do NOT use them for a real deployment.

## Supabase connection added
This build is prepared for the Supabase project used by the team.

1. In `index.html`, replace `PASTE_YOUR_SUPABASE_PUBLISHABLE_KEY_HERE` with the project's publishable key.
2. Run `supabase_migration.sql` in Supabase SQL Editor.
3. Create a Storage bucket named `issue-photos` and make it PUBLIC for this test version.
4. Run `storage_test_policies.sql`.
5. Push `index.html` and `style.css` to GitHub Pages.
6. Submit a complaint from one device, then open the site on another device. The same database record should appear.

IMPORTANT: The SQL policies in this test version intentionally allow anonymous reads/updates/deletes. This is ONLY for learning/testing. Before real college use, replace them with proper Supabase Auth + role-based RLS and a private photo bucket.
