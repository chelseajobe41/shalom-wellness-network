# Shalom Wellness Network — Setup Guide

Step-by-step for getting your website live with your own domain name. No coding required.

**Total time, end to end: about 45 minutes** (plus 1 to 24 hours for the domain to fully connect).

---

## What you'll do

1. **Buy your domain name** (the address people type, like `shalomwellnessnetwork.com`) — about 10 minutes, around $10 to $15 for the first year.
2. **Publish the website to Netlify** (the free service that hosts your site) — about 5 minutes.
3. **Connect your domain to Netlify** so visitors typing your URL land on your site — about 10 minutes plus a wait.
4. **Turn on your form emails** so every contact form, quiz submission, and free-guide signup lands in your Gmail — about 1 minute.

You only do all of this **once**. After that, the site runs on its own.

---

## Step 1 · Buy Your Domain Name

A domain is the address visitors type to find your site. You buy it once a year from a registrar.

### Recommended registrar: Cloudflare

Cloudflare sells domains at exact cost (the cheapest option around) and has a clean interface. You can use any registrar — Namecheap, GoDaddy, Google Domains, Squarespace Domains all work. Cloudflare is the recommendation.

### What to do

1. Go to **https://dash.cloudflare.com/sign-up** and create a free account using `mamamboga4life@gmail.com`.
2. Once signed in, click **Domain Registration** in the left sidebar → **Register Domains**.
3. In the search box, type **shalomwellnessnetwork.com** and press Enter.
4. If it's available, click **Purchase**. Expect about **$10 to $11 for one year**, paid by credit card.
5. If your first choice isn't available, try variations:
   - `shalomwellness.com`
   - `shalomwellness.net`
   - `kemuntowellness.com`
   - `wholeness4you.com`
   - `feelgreatwithkemunto.com`
6. Complete checkout. Cloudflare may ask you to verify your email address before the purchase finalizes — check your inbox and click the verification link they send.

**You now own your domain.** Keep the Cloudflare login handy; you'll need it in Step 3.

---

## Step 2 · Publish the Website to Netlify

Netlify is the free service that will host your website files and serve them to anyone who visits.

### Create your Netlify account

1. Go to **https://app.netlify.com/signup** and sign up with `mamamboga4life@gmail.com`.
2. When asked how you want to deploy, pick **"Deploy without Git"** (or just close the prompt — you can deploy from the dashboard).

### Drag the website onto Netlify

1. From the Netlify dashboard, look for the panel that says:
   > *"Drag and drop your site output folder here"*
2. Find the **`shalom-wellness-deploy`** folder on your Mac (the folder this guide is inside).
3. Drag the **entire folder** onto that panel and drop it.
4. Netlify uploads everything. After 30 to 60 seconds, the site is live at a randomly generated URL like:
   - `https://lucky-cat-12345.netlify.app`

**Your website is live.** It works, but the URL is random. Step 3 swaps it for your real domain.

### Rename the Netlify URL (optional but recommended)

1. In your Netlify dashboard, click your new site.
2. Click **Site configuration → Site details → Change site name**.
3. Rename it to something memorable like `shalom-wellness-network`.
4. Save. Your URL becomes `https://shalom-wellness-network.netlify.app` (this is your **backup URL** — your real domain still goes through Step 3).

---

## Step 3 · Connect Your Domain to Netlify

This is the step that makes `shalomwellnessnetwork.com` actually load your site.

### In Netlify

1. From your Netlify site dashboard, click **Domain management** (left sidebar).
2. Click **Add a domain** under "Custom domains".
3. Type your domain (`shalomwellnessnetwork.com`) and click **Verify**.
4. When Netlify asks if you own this domain, click **Yes, add domain**.
5. Netlify will give you **two options**. Pick option A or B below:

#### Option A · Easier (use Netlify DNS)

Netlify can manage all the DNS settings for you. This is the easier path.

1. Netlify will show you **two nameserver addresses** that look like `dns1.p01.nsone.net` and `dns2.p01.nsone.net` (the exact addresses vary).
2. **Copy both nameservers.**
3. Go back to Cloudflare → click your domain → **DNS** → look for **Nameservers** at the top.
4. Click **Change nameservers** and paste in the two Netlify addresses.
5. Save. Cloudflare will say "this will move DNS away from Cloudflare" — that's fine, click confirm.

#### Option B · Keep Cloudflare DNS

If you want to keep using Cloudflare's DNS (slightly faster), point your domain at Netlify with two records.

1. In Cloudflare → DNS → **Add record**:
   - **Type**: `A`
   - **Name**: `@` (or leave blank — means "the root domain")
   - **Content**: `75.2.60.5`
   - **Proxy status**: **DNS only** (click the orange cloud to gray it out — this matters)
   - Save.
2. Add a second record:
   - **Type**: `CNAME`
   - **Name**: `www`
   - **Content**: your Netlify site URL without `https://` (for example `shalom-wellness-network.netlify.app`)
   - **Proxy status**: **DNS only** (gray cloud)
   - Save.

### Wait for it to connect

After either option, you wait. DNS changes usually take **15 minutes to 2 hours** but can take up to **24 hours** in rare cases.

Once it's connected, Netlify will automatically issue a **free SSL certificate** (the green padlock that says your site is secure). You don't have to do anything for this.

Open `https://shalomwellnessnetwork.com` in your browser. When you see your site load with the padlock, you're done with Step 3.

---

## Step 4 · Turn On Form Emails

Your site has three forms that need to email you:

1. **Contact page** — the booking form
2. **Quiz page** — every quiz submission emails you the visitor's answers
3. **Free guide signup** — the lead magnet on the Home and Quiz pages

All three submit through **FormSubmit.co** straight to `mamamboga4life@gmail.com`. To turn them on, you just need to verify your email address **once**.

### How

1. On your live website, fill out the **Contact form** with any test info (use your own name and email).
2. Hit Send.
3. Open `mamamboga4life@gmail.com`. You'll get an email from **FormSubmit.co** with subject "Confirm your email" or similar.
4. Click the **Activate** button inside that email.
5. Done. From now on, every form submission lands in your inbox.

You only do this **once**. The single verification covers all three forms.

### What you'll get per submission

| Form | You receive |
|---|---|
| Contact | First name, last name, email, phone, state, what made them reach out, how they heard about you |
| Quiz | First name, email, their zone (In Balance / Stressed / Inflamed), score, and all 10 answers in plain English |
| Free guide | First name, email, which guide they downloaded |

If a quiz-taker also clicks "Book My Free 15-Min Call", you'll get a **second email** tagged "⏰ Quiz visitor wants a 15-min call" so you know to reach out and schedule.

---

## After everything is live

### Set up email forwarding (optional)

If you ever want emails sent to `kemunto@shalomwellnessnetwork.com` (your custom domain) to forward to your Gmail, you can set that up in Cloudflare under **Email → Email Routing**. It's free. Skip this step for now unless you want a professional email address.

### Add a professional Gmail (optional, costs money)

Google Workspace lets you have `kemunto@shalomwellnessnetwork.com` as a real Gmail-style inbox. It's $6 per user per month. Skip this unless you want it; the FormSubmit setup works perfectly with your existing `mamamboga4life@gmail.com`.

### Update the Unicity affiliate URLs

The site currently uses `ufeelgreat.com/c/Josephine` for the "Join the Feel Great Protocol" button. If Unicity gives you a new referral code (like `c/Kemunto`), let your developer know and they'll update the links.

---

## When you need help

### Site won't load after I add the domain
DNS takes time. Wait an hour and try again. If after 24 hours it still doesn't load, double-check that you pasted the nameservers exactly as Netlify gave them.

### Form emails aren't coming through
1. Check your spam folder.
2. Make sure you clicked the **Activate** link in the FormSubmit verification email. Until you do, submissions are held but not delivered.
3. Test the form again. If still nothing, email Chelsea.

### I want to change text on the website
Email Chelsea. She'll send you an updated `index.html` to drop into Netlify the same way you did the first deploy (drag the new folder onto the Deploys panel).

### Something broke
Email Chelsea at the same address you use for other projects.

---

## Summary checklist

- [ ] Bought domain at Cloudflare (`shalomwellnessnetwork.com`)
- [ ] Created Netlify account
- [ ] Dragged `shalom-wellness-deploy` folder onto Netlify, site is live
- [ ] Renamed Netlify URL to something memorable
- [ ] Added custom domain in Netlify
- [ ] Updated nameservers (Option A) OR added DNS records (Option B) in Cloudflare
- [ ] Waited for DNS to propagate; `https://shalomwellnessnetwork.com` loads
- [ ] Submitted the Contact form once and clicked the FormSubmit activation email

When all eight boxes are checked, you're live and forms email you. You're done.

*Wholeness for You. Hope for Generations.*
