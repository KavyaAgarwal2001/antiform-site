# Antiform — landing page

Single-file, no build step. `index.html` is the whole site.

## 1. Push the redesign

Your repo is already on GitHub, connected, and pushed (`main` tracking `origin/main`) — that part's done. You just need to commit and push the latest `index.html`/`README.md` changes.

Run each line below **on its own**, not as one pasted block — pasting a whole block into Terminal can choke on lines that start with `#` (zsh tries to run them as commands instead of treating them as comments):

```
cd "/Users/kavyaagarwal/Projects/Build a Company/antiform-site"
```

```
git add -A
```

```
git commit -m "Redesign: nav, focus section, Web3Forms"
```

```
git push
```

If `git push` asks you to log in and rejects your normal password — that's expected, GitHub dropped password auth a while back. You'd need a Personal Access Token (github.com → Settings → Developer settings → Personal access tokens) instead. Say the word if you hit this and I'll walk through it.

If `git commit` says "nothing to commit," run `git status` and paste me what it says.

*(Starting completely fresh instead? Easiest no-terminal path: new repo on github.com → "uploading an existing file" → drag in `index.html` and `README.md` → commit.)*

## 2. Turn on GitHub Pages

GitHub repo → **Settings → Pages** → Source: "Deploy from a branch" → Branch: `main`, folder `/ (root)` → Save.

Your site goes live at `https://<your-username>.github.io/antiform/` within a minute or two.

## 3. Make the waitlist form actually work

The form posts to [Web3Forms](https://web3forms.com) — chosen over Formspree because the free tier is 250 submissions/month (vs. 50) and setup is one field, not a dashboard. Takes 2 minutes:

1. Go to [web3forms.com](https://web3forms.com) → **Create your Form** (app.web3forms.com).
2. Enter your email and verify it (one email, no password/account in the usual sense).
3. Your dashboard shows an **Access Key** — copy it.
4. In `index.html`, find this line near the form:
   ```html
   <input type="hidden" name="access_key" value="YOUR_WEB3FORMS_ACCESS_KEY">
   ```
   Replace `YOUR_WEB3FORMS_ACCESS_KEY` with your real key. It's safe to leave in client-side code — it's not a secret, just an alias to your inbox.
5. Commit and push again. Every signup lands straight in your inbox, and is also stored in the Web3Forms dashboard for 30 days.

## 4. Custom domain later

Once you register a domain (antiform.com / .io / .co):
- Add a file named `CNAME` to this folder containing just your domain, e.g. `antiform.com`.
- Point the domain's DNS to GitHub Pages (A records to GitHub's IPs, or a CNAME record if using a subdomain — GitHub's docs walk through both).
- Add the same domain in repo Settings → Pages → Custom domain.

## Editing later

The tagline, the geology line, the three focus cards (Measurement / Modeling / Infrastructure), and the form copy all live in plain text inside `<body>` in `index.html` — easy to change without touching CSS. The "BUILDING" status pill in the nav is the same — just edit the text inside `.status-pill`.
