# Fluxon AI — Landing Page

Single-file static landing for fluxon-ai.com. Deploys to Vercel in ~60 seconds.

## Files
- `index.html` — the entire page. Tailwind via CDN. No build step.
- `vercel.json` — security headers.

## Local preview (5 seconds)
```bash
open index.html
# or
python3 -m http.server 8000   # then http://localhost:8000
```

## Deploy to Vercel — 3 ways, pick fastest

### Option A: Vercel CLI (fastest, ~60 seconds)
```bash
npm i -g vercel
cd /Users/gullycoder/in/fluxon-landing
vercel --prod
```
Follow prompts. Accept defaults. Vercel detects static site automatically.

### Option B: Drag-and-drop (no CLI)
1. Go to https://vercel.com/new
2. Drag the `fluxon-landing` folder onto the page
3. Click Deploy

### Option C: GitHub + Vercel auto-deploy
```bash
cd /Users/gullycoder/in/fluxon-landing
git init && git add . && git commit -m "Initial Fluxon landing"
gh repo create fluxon-landing --public --source=. --push
```
Then on vercel.com → Import Project → Pick the repo → Deploy.

## Connect fluxon-ai.com domain (5 minutes)

After Vercel deploys (gives you a `*.vercel.app` URL):

1. **In Vercel dashboard** → your project → Settings → Domains → Add `fluxon-ai.com`
2. **In your domain registrar** (Namecheap / GoDaddy / wherever you bought fluxon-ai.com):
   - Add an `A` record: `@` → `76.76.21.21`
   - Add a `CNAME` record: `www` → `cname.vercel-dns.com`
3. Wait 5–60 minutes for DNS to propagate
4. Vercel auto-provisions SSL

## Form setup (the demo request form)

The form posts to a placeholder Formspree URL. Replace before deploy:

1. Go to https://formspree.io/, sign up free, create a form
2. Copy your form endpoint (looks like `https://formspree.io/f/abc123`)
3. In `index.html`, find `REPLACE_WITH_YOUR_FORM_ID` and replace with your form ID
4. Submissions go straight to your email

Alternative: Tally.so, Typeform, or a simple `mailto:` link if you want zero infrastructure.

## What to verify before YC submits

- [ ] Page loads on mobile (test on phone, not just desktop)
- [ ] LinkedIn link goes to your real profile
- [ ] Form submits to YOUR email, not the placeholder
- [ ] No Lorem Ipsum, no `[REPLACE]` markers
- [ ] fluxon-ai.com resolves and serves the page (DNS propagated)
- [ ] SSL working (https:// not http://)
- [ ] Open Graph preview correct (paste fluxon-ai.com into a Slack/Twitter draft to test)

## What it intentionally does NOT have

Per the "don't perfectionize" principle:
- No animations beyond CSS hover transitions
- No video embed (recorded demo lives elsewhere — link from email)
- No blog, no /demo route, no /pricing page
- No analytics yet (add Plausible after YC)
- No contact form spam protection (Formspree handles it free tier)

If YC accepts: rebuild as Next.js. Until then, this is enough.
