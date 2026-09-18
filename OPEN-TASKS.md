# YAMS — open tasks

Running list. Update as things get done. Paste this into a new chat along with
`index.html` and any AI or developer can pick up exactly where we left off.

Site: aaryousus.com · Hosting: Cloudflare (Worker, project "yams") · Repo: GitHub "Yams"
Target launch: 9/10 October 2026

---

## Blocking

- [x] **Web3Forms access key** wired in (form "YAMS Collaborate", domain `aaryousus.com`).
- [ ] **Test the form on the live site** (not a preview file — the key is domain-locked)
      and confirm the email actually arrives.

## Domain housekeeping — do before launch

- [ ] **Decide one canonical domain and redirect the others.** The site currently answers on
      `aaryousus.com`, `www.aaryousus.com` and `yams.aaryousus.com`. Three live addresses
      splits search ranking and, more urgently, the Web3Forms key is registered against
      `aaryousus.com` only, so the form may fail on the other two.
      Fix: in Cloudflare add redirect rules sending `www.` and `yams.` to `aaryousus.com`.
      Alternative: add all three as allowed domains in the Web3Forms form settings.
- [ ] **Delete `robots.txt`'s `Disallow: /`** on 7 October so search engines can index the site.

## Deferred features (agreed, not built)

- [ ] **Automatic reply email** to anyone who submits the form. Needs Web3Forms paid tier
      (~$8/month). Template drafted and stored in this repo's README when built.
- [ ] **Sus Blog auto-subscribe.** The form captures the checkbox now; actually adding people
      to a list needs a mailing tool (Buttondown or Substack, both free). Wire up when the
      blog room is built.
- [ ] **Payment and booking layer.** Deliberately switched off while Aarha is employed
      full-time — the site must not read as a business. When that changes: add Cal.com
      booking plus Razorpay/Stripe to the "interested?" flow. No prices anywhere until then.
- [ ] **LinkedIn live embeds** in the Content Creation deep dive. Needs the full post URLs
      (the `...-activity-7xxxxxxxxx-...` form), not `lnkd.in` short links. Currently thumbnails.
- [ ] **University of North Carolina department name** in the portfolio — left out because
      it couldn't be verified.

## Rooms still to build

- [ ] Menu, header and footer (do this next: navigation is currently individual back buttons)
- [ ] Sus Blog
- [ ] Sus IRL
- [ ] You Can Help Me
- [ ] R U SUS (quiz)
- [ ] 404 page, favicon, social share images

## Recently finished

- [x] How I Can Help You room and the Let's Collaborate form, deployed
- [x] Web3Forms key wired in and the email body formatted for readability
- [x] Seven-day per-device lock so nobody can submit repeatedly
- [x] Confirmation popup on send
- [x] HANDOVER.md written

## Built and locked — do not change without asking

- The Gate, Hi I'm Aarha (both toggle states), Aarha's Portfolio (3 filters, timeline,
  deep dives), How I Can Help You, the Let's Collaborate form.
- Formatting rules that have already been settled: no em dashes anywhere in visible text;
  flag bars have one-line headings and two-line sub-lines; images sit at the repo root,
  not in a folder; every room is a separate page with no scrolling between them.
