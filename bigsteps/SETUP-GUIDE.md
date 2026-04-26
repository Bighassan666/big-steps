# 🛍️ BIG STEPS FASHION — Setup & Deployment Guide
## Get Your Store Live in Under 30 Minutes (100% Free)

---

## WHAT YOU NEED (ALL FREE)
1. **Supabase** account → https://supabase.com (free database)
2. **Paystack** account → https://paystack.com (free, Ghana ✓)
3. **Vercel** account → https://vercel.com (free hosting)
4. **GitHub** account → https://github.com (free, for deployment)

---

## STEP 1 — Set Up Your Database (Supabase)

1. Go to https://supabase.com and click **Start your project**
2. Sign up with Google (free)
3. Click **New Project** and fill in:
   - **Project name**: bigsteps-fashion
   - **Database Password**: Choose a strong password (save it!)
   - **Region**: Choose closest to you
4. Wait ~2 minutes for project to set up
5. Click **SQL Editor** in the left sidebar
6. Click **New query**
7. **Copy and paste the entire contents** of `supabase-setup.sql` into the editor
8. Click the green **Run** button
9. You should see "Database setup complete!"

### Get Your Supabase Keys
1. In Supabase, click the **Settings** icon (gear) → **API**
2. Copy the **Project URL** (looks like: `https://xxxxxxxxxxxx.supabase.co`)
3. Copy the **anon public** key (a very long string)
4. Save both — you'll need them in Step 3!

---

## STEP 2 — Set Up Paystack (Ghana Payments)

Paystack supports **MTN Mobile Money**, **Telecel Cash**, and **Bank** transfers in Ghana — automatically!

1. Go to https://paystack.com and click **Create a free account**
2. Fill in your business details (use your real name/business name)
3. Choose **Ghana** as your country
4. Verify your email
5. Go to **Settings** → **API Keys & Webhooks**
6. Copy your **Public Key** (starts with `pk_test_` for testing, `pk_live_` for live)

> ⚠️ Start with `pk_test_` for testing. Switch to `pk_live_` when ready for real money.

### Link Your Bank / Mobile Money
1. In Paystack dashboard, go to **Settings** → **Business Settings**
2. Add your bank account details OR your MTN MoMo number
3. Paystack will verify and send payments there!

---

## STEP 3 — Configure Your Store

Open your `index.html` file in any text editor (Notepad, VS Code, etc.)

Find this section near the top of the `<script>` block:

```javascript
const CONFIG = {
  supabaseUrl:        'YOUR_SUPABASE_URL',
  supabaseAnonKey:    'YOUR_SUPABASE_ANON_KEY',
  paystackPublicKey:  'YOUR_PAYSTACK_PUBLIC_KEY',
  adminPassword:      'admin123',     // ← CHANGE THIS!
  storeEmail:         'your@email.com',
  ...
};
```

Replace each value:
- `YOUR_SUPABASE_URL` → paste your Supabase Project URL
- `YOUR_SUPABASE_ANON_KEY` → paste your Supabase anon key
- `YOUR_PAYSTACK_PUBLIC_KEY` → paste your Paystack public key
- `admin123` → **change to a strong secret password!**
- `your@email.com` → your real email address

**Example after editing:**
```javascript
const CONFIG = {
  supabaseUrl:        'https://abcdef123456.supabase.co',
  supabaseAnonKey:    'eyJhbGciOiJIUzI1NiIs...',
  paystackPublicKey:  'pk_test_abc123...',
  adminPassword:      'MySecurePass2025!',
  storeEmail:         'bigsteps@gmail.com',
  ...
};
```

Save the file.

---

## STEP 4 — Deploy to Vercel (Free Hosting)

### Option A: Drag & Drop (Easiest — 2 minutes)
1. Go to https://vercel.com and sign up with GitHub
2. Click **Add New** → **Project**
3. At the bottom, look for **"Or deploy without Git"** → **Continue with CLI / drag & drop**
4. Drag your `index.html` file directly onto the Vercel page
5. Your store will be live at a URL like: `bigsteps-fashion.vercel.app`

### Option B: Via GitHub (Recommended for easy updates)
1. Go to https://github.com and create a new repository called `bigsteps-fashion`
2. Upload your `index.html` file to the repository
3. Go to https://vercel.com → **Add New Project**
4. Select your GitHub repository
5. Click **Deploy**
6. Your store goes live!

To update your store later: just edit `index.html` on GitHub and Vercel auto-redeploys.

---

## STEP 5 — Get a Custom Domain (Optional, Free)
1. In Vercel, go to your project → **Settings** → **Domains**
2. Add a domain like `bigstepsfashion.com` (you'd buy this for ~$12/year)
3. Or keep the free `.vercel.app` domain!

---

## ADMIN PANEL GUIDE

**URL:** `yoursite.vercel.app` → click **Admin** in the navigation

**Default Login:**
- Password: `admin123` (change this immediately!)

**What you can do:**
- 📊 **Dashboard** — See revenue, orders, product count
- 👔 **Products** — Add, edit, delete products with photos
- 📦 **Orders** — View customer orders, update status (pending/paid/shipped/delivered)
- ⚙️ **Settings** — Update admin password

**Adding Products:**
1. Go to Admin → Products
2. Click "Add Product"
3. Fill in name, price, category, description
4. Paste an image URL (from Google Images, your own hosting, etc.)
5. Click Save

**To add real product images:**
- Upload photos to https://imgbb.com (free) and copy the direct URL
- Or use Google Drive: upload photo → right-click → Get link → copy URL

---

## PAYMENT METHODS AVAILABLE

| Method | How it works |
|--------|-------------|
| MTN Mobile Money | Customer enters MoMo number on Paystack checkout |
| Telecel Cash | Customer enters Telecel number on Paystack checkout |
| Bank Transfer | Customer sees your account details |
| Visa/Mastercard | Card payment (supported by Paystack) |

Paystack deposits your earnings to your linked bank account every weekday!

---

## TESTING YOUR STORE

Before going live, test with Paystack's test mode:
- Use your `pk_test_` key first
- Test card: `4084 0840 8408 4081`, any future date, any CVV
- For MoMo testing, Paystack provides test numbers in their docs

---

## TROUBLESHOOTING

**Products not showing?**
→ Make sure you ran the SQL in Supabase and entered the correct keys in CONFIG

**Payments not working?**
→ Check your Paystack public key is correct. Make sure it's `pk_live_` for real payments.

**Admin login not working?**
→ Default password is `admin123`. Check the CONFIG section in your HTML.

**Page not loading?**
→ Check browser console (F12) for error messages

---

## SUPPORT
Need help? The Paystack support team is available at support@paystack.com
Supabase docs: https://supabase.com/docs

---
*Big Steps Fashion — Built with ❤️ in Ghana 🇬🇭*
