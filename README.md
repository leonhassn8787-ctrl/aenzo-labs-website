# AENZO LABS Website

Premium, responsive dark-and-gold website for AENZO LABS — Web3 marketing, community growth, and campaign services.

## Live website

https://aenzo-labs-website.onrender.com/

## Deploy on Render

This repository is intended to run as a **Static Site**.

- Build command: leave blank
- Publish directory: `.` (the repository root)
- Main page: `index.html`
- Admin page: `admin.html`

After changing files on the `main` branch, confirm the Render deployment finishes successfully before testing the live site.

## Website features

- Responsive landing page and service directory
- Telegram, X, and Binance Community links
- Public campaign/announcement feed
- Admin page at `/admin.html`
- Supabase-backed post management and persistent view counting, when configured

## Supabase setup

The browser configuration is stored in `config.js`. It must contain only the Supabase project URL and a public anon/publishable key. **Never place a service-role key or other secret in a browser file.**

The project has already been prepared with database schema and access policies. If the database needs to be initialized in a new Supabase project, review and run `supabase-setup.sql` in the Supabase SQL Editor. Do not rerun setup instructions blindly against a production database.

## Admin access

1. Open `/admin.html` after the latest Render deployment is live.
2. Sign in or complete the owner-authorized registration flow shown by the dashboard.
3. Confirm the owner email using Supabase Authentication if email confirmation is enabled.
4. If sign-in is rejected, check the Supabase Authentication user and the admin authorization RPC/policies. Do not add an arbitrary user UUID or disable Row Level Security as a workaround.

## Troubleshooting

- **Admin page shows Not Found:** verify the Render service is connected to this repository and the `main` branch, the publish directory is `.`, and the latest deployment is successful. The file `admin.html` must exist in the published root.
- **Admin page opens but login fails:** check `config.js`, Supabase Auth, and the owner authorization setup.
- **Posts or view counts do not update:** check Supabase project settings, database migrations/policies, and browser console errors.

## Security and limits

Public browser keys are designed to be visible; database permissions must be enforced by Supabase Row Level Security and server-side authorization. Never commit passwords, service-role keys, or private API secrets. Marketing results and investment returns are not guaranteed.
