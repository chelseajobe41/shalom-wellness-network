# Shalom Wellness Network — Website

This folder contains everything needed to publish your website on Netlify. No coding required.

> **First time setting this up?** Open **`SETUP.md`** in this folder for the full step-by-step: buying your domain, creating your Netlify account, connecting your domain, and turning on form emails. Takes about 45 minutes total (plus a wait for DNS).
>
> This README is the quick-reference version once you're set up.

## What's inside

- `index.html` — your complete website (all pages: Home, About, Protocol, Quiz, Stories, Contact)
- `kemunto.jpg` — your portrait, used in the "A Personal Message From Kemunto" section
- `esther-dow-transformation.png` — Dr. Esther Dow's before/after photo on the Stories page
- `why-am-i-always-tired.pdf` — your free guide / lead magnet, "Why Am I Always Tired, Hungry & Gaining Weight?"
- 4 background videos (.mp4) — used across the page heroes

---

## How to publish (drag-and-drop, takes about 2 minutes)

### Step 1 — Sign in to Netlify

1. Go to **https://app.netlify.com/** and sign in (or create a free account)

### Step 2 — Drag this folder onto the dashboard

1. Once signed in, you'll see a dashboard with your sites
2. Drag the **entire folder** (the one this README is in) onto the page where it says
   *"Want to deploy a new site without connecting to Git? Drag and drop your site output folder here"*
3. Netlify will upload everything and give your site a random URL like `https://lucky-cat-12345.netlify.app`
4. That's it — your site is live

### Step 3 — Rename the site (optional)

In **Site Settings → Site Information → Change site name**, rename it to something memorable like `shalom-wellness-network` so the URL becomes `https://shalom-wellness-network.netlify.app`.

### Step 4 — Connect your own domain (optional)

If you own `shalomwellnessnetwork.com` or another domain, go to **Domain Settings → Add custom domain** and follow Netlify's instructions. They walk you through it.

---

## How the forms email you (one-time setup, takes 30 seconds)

Both forms on your site (the Contact page booking form and the Metabolic Quiz share form) deliver submissions **directly to your Gmail at `mamamboga4life@gmail.com`** via FormSubmit.co. No Netlify dashboard configuration needed.

**One-time activation (do this once, after the site is live):**

1. Have someone (you, a friend, anyone) submit the Contact form on your live site once. Just fill it out and click Send.
2. Check the inbox at `mamamboga4life@gmail.com`. You'll see an email from **FormSubmit.co** asking you to verify.
3. Click the **Activate** link in that email.
4. Done. From now on, every submission from either form will land in your inbox immediately.

You only need to do this **once**. Both forms (Contact + Metabolic Quiz) email to the same address, so the single verification covers both.

**What you'll receive per submission:**

- **Contact form:** First name, last name, email, phone, state, what made them reach out, how they heard about you
- **Quiz form:** First name, email, their result zone (In Balance / Stressed / Inflamed), their score, and all 10 of their answers in plain English
- **Free guide signups:** First name, email, and which guide they requested (the lead magnet card on the Home page and Quiz page sends visitors the "Why Am I Always Tired, Hungry & Gaining Weight?" PDF and emails you their contact info)

Emails arrive formatted as a clean table, with a clear subject line so you can spot them at a glance.

---

## Making future updates

If you want to change text, swap a photo, or add a new story:

- **Small text changes** — let your developer know and they'll send you a new `index.html` to drop in
- **New photos** — give your developer the file and they'll wire it in
- **Updating the live site** — go back to your Netlify site, click **Deploys**, and drag the new folder onto the page where it says *"Need to update your site? Drag and drop your site folder here"*. The new version replaces the old one.

---

## Files you should NOT delete

Everything in this folder is needed. If you remove `index.html`, the site stops working. If you remove a video or photo, that section of the site shows a broken image.

---

## Questions

For technical help or updates, contact your developer (Chelsea at Visible Local).

For anything about the wellness content itself — that's all you, Kemunto.

*Wholeness for You. Hope for Generations.*
