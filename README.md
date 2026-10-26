# AENZO LABS Website

Responsive dark-and-gold marketing website for AENZO LABS.

## Live website
https://aenzo-labs-website.onrender.com/

## Deploy on Render
Connect this repository as a **Static Site**. Leave the build command blank and set the publish directory to `.`. The website entry point is `index.html`.

## Included in the repository
- Responsive marketing landing page and service directory
- Telegram, X and Binance Community links
- Optional updates/campaign feed in the public site
- Admin dashboard at `/admin.html`
- Supabase schema with Row Level Security policies

## Admin and database setup (required once)
1. Create a Supabase project at https://supabase.com/dashboard.
2. In Supabase, open **SQL Editor**, run the contents of `supabase-setup.sql`.
3. In **Authentication > Users**, create your own admin user and confirm its email as needed.
4. Copy that user's UUID. In SQL Editor run: `insert into public.admin_users (user_id) values ('YOUR-USER-UUID');` replacing the placeholder with the real UUID.
5. Open **Project Settings / API** and copy the Project URL and the public anon/publishable key. Never use a service-role or secret key in the website.
6. Visit `/admin.html`, enter the URL and public key, then sign in using the admin email and password you created.
7. To show posts on the public website, set `window.AENZO_PUBLIC_CONFIG = { url: "YOUR_SUPABASE_PROJECT_URL", anonKey: "YOUR_PUBLIC_ANON_KEY" }` in a small config script loaded before the updates-feed script in `index.html`. Only the public anon/publishable key is suitable for browser use; database policies protect writes.

## Important limits
The dashboard and feed code are committed, but live database publishing will not work until a Supabase project and admin user are created and configured. Persistent visitor analytics/view counting is not implemented yet. Do not publish secret/service-role keys. The website does not promise investment returns or guaranteed campaign results.
