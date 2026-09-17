# Aab-E-Hayat Health Care Juice — Deployment Guide

This project is 100% serverless and static. There are **no separate `.env` files, no `package.json`, and no `wrangler.toml`** required. Everything is managed directly inside your **Cloudflare Dashboard** and deployed freely on **Vercel / GitHub Pages**.

---

## 1. Deploy Frontend (Static — GitHub Pages or Vercel)
1. Push this folder to your GitHub repo.
2. In **Vercel** or **GitHub Pages**, select the repository and click **Deploy**.
3. Done! Your single-product store (`index.html`) and admin dashboard (`admin.html`) are live immediately.

---

## 2. Deploy Backend (Cloudflare Worker)
1. Log in to [dash.cloudflare.com](https://dash.cloudflare.com/) → **Compute (Workers & Pages)** → **Create Worker**.
2. Name your worker (e.g. `aabe-hayat-api`) and click **Deploy**.
3. Click **Edit Code**, delete whatever is inside, and paste the entire code from [`worker.js`](./worker.js).
4. Click **Deploy**.
5. Copy your worker URL (e.g. `https://aabe-hayat-api.your-account.workers.dev`).
6. In [`index.html`](./index.html#L155), your worker URL is already configured:
   ```javascript
   window.CLOUDFLARE_WORKER_URL = "https://aabe-hayat.infisparks.workers.dev";
   ```

---

## 3. Adding Your Razorpay & Shiprocket Keys (Inside Cloudflare)
In your Cloudflare Worker dashboard:
1. Go to **Settings** → **Variables and Secrets**.
2. Click **Add** under **Environment Variables** for each key:
   - `RAZORPAY_KEY_ID` (Your live Razorpay Key)
   - `RAZORPAY_KEY_SECRET` (Your Razorpay Key Secret)
   - `SHIPROCKET_EMAIL` (Your Shiprocket login email)
   - `SHIPROCKET_PASSWORD` (Your Shiprocket password)
   - `SHIPROCKET_PICKUP_LOCATION` (e.g. `work`)
3. Click **Deploy / Save**. The worker will automatically read them immediately.

---

## Pre-Configured Firebase RTDB Credentials
- **Firebase Database**: `https://aabe-hayat-default-rtdb.firebaseio.com`
- **Database Secret**: `HKRBfNsCEPVfmHk6yNZpZhBZkYpMtsNSkkQtFqxF`
- **Admin Dashboard Master Password**: `admin123`
