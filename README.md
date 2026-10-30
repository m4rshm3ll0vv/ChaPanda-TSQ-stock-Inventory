# ChaPanda TSQ Stock Management — setup

This is a deployable starter website. It is **not live yet** until you create/configure the Supabase project and publish the site.

## Included
- Mobile-friendly staff login
- Shared daily stock records with Supabase Realtime
- Date selector
- Exactly 7 display columns
- Stock total = Stock Balance + Stock in - Stock out
- Stock usage = Stock out (always equal)
- Activity log showing staff email and timestamp

## 1. Create the shared database
1. Create a project at https://supabase.com/
2. Open SQL Editor and run all of `schema.sql`.
3. In Project Settings → API, copy the Project URL and anon/public key.
4. Open `index.html` and replace:
   - `PASTE_SUPABASE_PROJECT_URL`
   - `PASTE_SUPABASE_ANON_KEY`

## 2. Import the item list
Use the Supabase Table Editor → `inventory_items` → Insert rows.
Import `items.csv` (CSV import option) with columns `item_name,sort_order,active`.
The starter extracted 78 unique item descriptions from your workbook.
Do not import the spreadsheet's calculated columns as item names.

## 3. Create staff accounts
In Supabase → Authentication → Users, add one account per staff member (email + temporary password). Staff log in individually on the website. Give each staff member their own account; do not share passwords.

## 4. Publish the website
1. Create a free static site project on Netlify or Cloudflare Pages.
2. Upload `index.html` as the site root (or connect a Git repository containing it).
3. Once published, test login and updates with two phones.
4. Generate one QR code pointing to the final HTTPS website URL and print it for the shop.

## Important
- The website URL and QR code do not exist until hosting is completed.
- Keep the Supabase anon/public key in the frontend only; never put a service-role key in `index.html`.
- This starter permits authenticated staff to edit stock records and read the activity log. Restrict account creation to the owner/admin in Supabase.
- Test the workflow before relying on it for official stock counts.
- If the business needs role-based managers, approval of edits, or item management from the website, those can be added in a next version.
