# AENZO LABS Website

Premium dark-and-gold, responsive Web3 marketing website.

## Live website
https://aenzo-labs-website.onrender.com/

## Deploy on Render
Use a Static Site connected to this repository. Leave the build command blank and set publish directory to `.`. The entry point is `index.html`.

## Current features
- Responsive marketing landing page and service directory
- Telegram, X and Binance community links
- Optional live announcements/campaign feed
- Admin dashboard at `/admin.html` with email/password sign-in
- Supabase SQL setup for posts, admin allowlist, and persistent home-page view counter
- Public configuration template at `/config.js`

## One-time setup required for live database features
I cannot create resources inside your Supabase account without account authorization. To enable live posts and persistent views:

1. Create a project at https://supabase.com/dashboard.
2. Open **SQL Editor** and run all of `supabase-setup.sql`.
3. In **Authentication → Users**, create your admin user. Copy the user's UUID.
4. In SQL Editor, run this command after replacing the placeholder with your actual UUID:
   `insert into public.admin_users (user_id) values ('YOUR-ADMIN-USER-UUID');`
5. Open Supabase **Project Settings → API** and copy the Project URL and the public anon/publishable key.
6. Edit `config.js`: fill in `url` and `anonKey` using the Project URL and **public** key. Do not use a service-role/secret key.
7. Commit the config.js change to GitHub. Render should redeploy the static site.
8. Open `/admin.html`, enter the same Project URL and public key, then sign in with your admin email and password. Publish an update to test.
9. Open the main website and confirm the published update and view counter appear.

## Security notes
- Do not put service-role/secret keys in browser files or send them in chat.
- Only user IDs listed in `public.admin_users` can write posts when the included SQL policies are active.
- The public key is designed for browser use; Row Level Security protects writes.
- The view counter counts page loads, not unique visitors; automated traffic may be included.
- Investment returns and campaign results are not guaranteed.
