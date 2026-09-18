# YAMS — handover

Everything needed to continue building aaryousus.com. Written 17 September 2026,
after four rooms were finished and deployed.

**If you are an AI or developer picking this up:** read this file, then read `index.html`.
The HTML is the source of truth for every colour, font, breakpoint and word. This file
explains the *why*, the taste, and the constraints that are not visible in the code.

---

## 1. Who and what

**Aarha Shah.** Spelling matters: A-A-R-H-A. Never "Arha". Pet name "Aaru", used only inside
copy, never in navigation. Instagram handle `@aaryousus`, which is also the domain.

**YAMS — Your Ally for Modern Sustainability.** A personal site, not a company site.
Aarha is a full-time strategy and sustainability consultant at Accenture, builds content
as `aaryousus`, and wants a space that is part portfolio, part personality, part platform.

**The positioning.** Sustainability is currently sold two ways: as a lifestyle aesthetic, or
as an apocalypse. YAMS is the third way — modern, practical, occasionally funny decisions
that individuals, brands and organisations can actually make. The goal over time is to build
an audience, then a venture.

**Motto:** *we'll figure.* Used throughout, including:
- The Gate: `we'll figure` above the arrow
- Profile copy: "not fancy ones. *we'll figure together.*"
- The first service is literally named around figuring things out
- Form confirmation: "we'll figure how to make it work :)"

**Signature wordplay:** `aaru sus.` / `are you sus?` — the domain carries it. It was removed
from the Gate for simplicity but can return in the footer.

---

## 2. The constraint that shapes everything

**Aarha is employed full time and her contract restricts running a business.** The site must
read as a personal space, portfolio and brand. Not a shop.

**Therefore, on the site there is:**
- No pricing. Not a number, not a range, not "from ₹X".
- No booking calendar and no payments.
- No words "services", "clients", "packages", "hire me", "available for work".
- No client names anywhere. Everything is anonymised the way her CV does it:
  "a global spirits manufacturer", "an Australian federal government department",
  "a leading international steel producer", "a global CPG major", and so on.
  Publicly nameable: Disney Star, SUSI, University of North Carolina, Accenture (employer).
- No client logos, no client deliverables, no internal methodology documents.
- Every deep dive carries: "Client and engagement names have been anonymised to maintain
  confidentiality."

**The offerings are framed as capability and conversation, never product.** People express
interest through a form; Aarha replies personally and settles any commercial detail off-site.

**Designed to switch on later.** When she is free to charge, the plan is Cal.com booking plus
Razorpay/Stripe on the "interested?" flow. Do not add it before she says so.

---

## 3. Her taste, learned the hard way

This section exists so nobody has to rediscover it. These are settled rules.

**Language**
- No em dashes or en dashes in visible text, ever. She finds them AI-looking. Use commas,
  full stops or colons. (Code comments are fine.)
- No vague, gassy, self-congratulatory lines. Every bullet must say something concrete.
  "Findings with sources, written to be used rather than filed" was rejected as school-essay
  language. "A prioritised action plan your team can agree on" was rejected as meaningless.
- Complete sentences in body copy. No fragment-style Instagram-caption writing.
- Direct, witty, specific. Jokes should come from competence, not from being cute.
- First-person headings go in quote marks so they read as the visitor's question:
  `"where do I start?"`, `"how does this matter for us?"`
- She writes and dictates fast; read the whole message before acting, and expect several
  distinct instructions inside one paragraph.

**Formatting parity — she notices everything**
- Inside any row of boxes: all headings the same number of lines, all sub-lines the same
  number of lines. Use forced `<br>` **and** prevent re-wrapping, or it breaks at some width.
- Credential bars (the "flag"): one-line headings, two-line sub-lines, last line pinned to
  the bottom so years align across the row.
- Equal-size boxes in a row. Card heads are equalised with a small script (`evenHeads()`),
  not a fixed min-height, so there is no dead space.
- Buttons in a row of cards must sit at the same height. They are pinned with `margin-top:auto`.
- Nothing may overflow horizontally. Grid children need `min-width:0`, or long dropdown text
  pushes the page wider than a phone screen. This caused a visible beige strip and took
  several rounds to find.
- Social rows never wrap. Android Chrome renders wider than iOS Safari, so what fits on an
  iPhone may break on Android. Both rows use `flex-wrap:nowrap` with horizontal scroll.

**Layout preferences**
- Minimal, image-led, generous type. Text must not be tiny.
- Photo on the left, heading and subheading beside it. This pattern repeats across rooms.
- Circles for portraits, never rectangles. A true circle, with equal width and height set
  explicitly (stretching a flex item once turned it into an oval).
- Body text runs the full width, matching the width of any table or bar beneath it.
- Each room is a separate page. No scrolling between rooms.
- Nothing is selected by default on filter pages. Options reveal content when clicked.

**Process**
- Always send two files: a **preview** with images embedded as base64 (so it renders in chat)
  and a **deploy** `index.html` referencing plain filenames. She will otherwise report
  "the photos are not loading" when previewing the deploy file.
- Validate the JS with `node --check` and the HTML tag balance before sending. A bad escape
  once shipped a blank page.
- Check image crops by actually viewing them before shipping.

---

## 4. Design system

All tokens live in the `:root` block at the top of `index.html`.

```
--paper   #FAF6EC   warm background, the default
--bone    #FFFDF8   raised surfaces, portfolio background
--ink     #141509   all dark text, dark fields
--olive   #4E6141   secondary text, rules, mid-green cards
--olive-deep #1E2618 dark rooms (deep dives, the form)
--ochre   #E9A81D   highlight, card heads, buttons on dark
--ochre-deep #B8791C small ochre text on light backgrounds (contrast)
--blue    #2440E8   the pop: active filters, links, primary pills, timeline
--sage    #D9DFC6   tints
--cream   #FFF9EC   text on dark
```

**Colour logic.** Rooms move through colour: Gate paper, profile paper flipping to near-black,
portfolio bone with dark deep dives, help room paper with green and ochre cards, form near-black.
Blue means "this does something" — filters, links, primary buttons — and appears nowhere else.
Card sets use a green-to-yellow ramp (`#1E2618 → #E9A81D`) assigned **by class, not by
`nth-child`** (positional colours broke when elements were inserted into the grid).

**Type.** Three faces, all free:
- **Bricolage Grotesque** (Google, variable) — wordmark, headings, numbers, buttons.
  Condensed at large sizes via `font-stretch`, letter-spacing around −.05em.
- **Instrument Serif Italic** (Google) — asides, the motto, sub-lines, quotes. Never body copy.
- **Satoshi** (Fontshare, 400/500/700) — body, labels, small text.
- **No monospace anywhere.** She dislikes typewriter faces. Small text is plain Satoshi 500.

**Shape and motion.** Two radii: 0 or 12–14px for blocks, 999px for pills. No soft grey
shadows. A paper-grain overlay at 4% opacity sits over everything. Motion is restrained and
respects `prefers-reduced-motion`.

---

## 5. Architecture

One file, `index.html`. Plain HTML, CSS and vanilla JS. No build step, no framework, no
dependencies beyond two font CDNs. This was deliberate: Aarha maintains it herself, and
anything with a toolchain would rot.

**Rooms are sections toggled by classes on `<body>`:**
- `.gate` — always first. `body.locked` prevents scrolling; clicking the arrow adds
  `body.leaving` then `body.entered`, which removes the Gate entirely so you cannot scroll back.
- `.hi` — Hi, I'm AARHA. Default room.
- `.pf` — Portfolio. Shown by `body.on-pf`.
- `.hp` — How I Can Help You. Shown by `body.on-hp`.
- `.fm` — Let's Collaborate (the form). Shown by `body.on-fm`.

**Content lives in JS objects near the bottom**, which is where to edit copy:
- `COPY` — the two profile states, subheadings and credential bars
- `P` — every project, written **once** and reused wherever it appears, so the same
  engagement reads identically under every filter
- `CATS` — portfolio compartments for the three lenses (skills, tech, industry)
- `TL` — the timeline
- `WALL` — the four content thumbnails and their post links
- `WHOS` and `OFFERS` — the help room's three audiences and their offerings.
  The form's dropdowns are generated from `OFFERS`, so editing an offering name updates
  the form automatically.

**Images** sit at the **repo root**, not in a folder. Folder uploads to GitHub failed
repeatedly; root-level filenames removed the problem. Current files: `circle-real.jpg`,
`circle-pro.jpg`, `circle-help.jpg`, `wall-reel-sus.jpg`, `wall-li-500.jpg`,
`wall-reel-cook.jpg`, `wall-li-talk.jpg`.

---

## 6. What is built

**Room 0 — The Gate.** YAMS at poster scale, the full form beneath, `we'll figure` and a
single arrow low on the screen. Scroll locked; one way in; the Gate is destroyed on entry.

**Room 1 — Hi, I'm AARHA.** Circle photo left, heading right with AARHA in blue. Two states
toggled by pills: *the real me* (paper background) and *the real me, professionally*
(near-black, ochre accents). Each state changes the subheading, the copy, the photo, the
credential bar and the colours. Bar has four items: two gold medals, full time strategy
consultant, global community leader (U.S. Department of State), content creator — and on the
professional side: global sustainability consulting, content creator, experience across
industries, Value 360 Award. Two blue pills at the foot lead to the portfolio and the help room.

**Room 2 — Aarha's Portfolio.** Horizontal timeline (Education, Disney Star, SUSI, Accenture,
aaryousus & YAMS) with a blue line, filled dots and equal cards, scrollable on mobile with a
fade and a "scroll timeline" hint. Then *explore my work by:* with three filters — skills,
technical expertise, industry — nothing selected until clicked. Each shows eight tiles in the
green-to-yellow ramp with line icons. Clicking opens a full-page deep dive sliding in from the
right: heading, four-word subheading, two paragraphs, then "key work done" as a beige table of
anonymised engagements, then the confidentiality note. Content Creation & Public Speaking has a
special deep dive with the social links and four thumbnail tiles linking to real posts.

**Room 3 — How I Can Help You.** *first, who are you?* and three tall cards with icons in
circles overlapping the top: one person, building something, an organisation. All green;
the selected one turns ochre with a triangle pointing down. Click again to collapse. Selecting
reveals *then, here is what I can solve* and the offerings: ochre head with number, quoted
heading and italic sub-line, dark green body with bullets, and an *interested?* button that
opens the form pre-filled. On mobile the offerings appear directly beneath the tapped card.
At the foot, *Interested to take this further?* with a *let's collaborate →* button.

**Room 4 — Let's Collaborate (the form).** Photo left, LET'S COLLABORATE right. Fields: who
they are (radio, pre-filled), tell me a little more about you (options change per audience),
name, email, phone (optional), what would you like to talk about (generated from the offerings),
tell me a bit more, preferred time (concrete IST slots), Sus Blog subscribe checkbox.
Custom validation names exactly what is missing in a red bar; email and phone format checked.
On success: a centred popup plus an inline confirmation, and a seven-day per-device lock so
nobody can send repeatedly. Delivery via **Web3Forms**, key `28f3eaaa-9149-40ec-b0b0-ec89b91e3ec4`,
registered to `aaryousus.com`. The submission is composed into a readable email body.

---

## 7. Accounts and how deployment works

| Thing | What it does |
|---|---|
| **Porkbun** | Owns `aaryousus.com`. Nameservers point to Cloudflare. |
| **Cloudflare** | Serves the site. Worker project named "yams". Three custom domains attached: `aaryousus.com`, `www.aaryousus.com`, `yams.aaryousus.com`. `wrangler.toml` tells it to serve the repo as static files. |
| **GitHub** | Repo "Yams" (owner Aarhashah). Holds `index.html`, the images, `robots.txt`, `wrangler.toml`, and these docs. Cloudflare redeploys automatically on every commit. |
| **Web3Forms** | Delivers form submissions to Aarha's inbox. Free plan. |

**The deploy routine, every time:**
1. Any new image: GitHub → Add file → Upload files → **choose your files** (not folder drag) → Commit.
2. `index.html` → pencil → Ctrl+A → Delete → paste new version → Commit changes.
3. Wait about 40 seconds, check in a **private/incognito tab** (caching otherwise shows the old version).

`wrangler.toml` must never be deleted. `robots.txt` currently blocks search engines and must be
changed on 7 October.

---

## 8. Plan to launch, 9/10 October 2026

Done: Gate, profile, portfolio, help room, form. Live on the domain.

Remaining:
- **Sus Blog** — the blog room. Name is "Sus Talk" in the older blueprint but she has since
  referred to it as the Sus Blog; confirm with her. Four recurring columns were agreed:
  *Sus or Legit?* (a claim examined, with a stamped verdict), *Red Flags* (greenwashing,
  claim versus fine print), *Asking for a Friend* (reader questions), *The Rabbit Hole*
  (long form). Sources listed at the foot of every post, numbered and linked. Publishing route
  still open: Substack-first, own CMS, or hybrid.
- **Sus IRL** — the feed and the four platform links.
- **You Can Help Me** — three intakes (spot a problem, pick my next topic, put something here)
  and a public wall of submitted ideas with statuses.
- **R U SUS** — the quiz room. Two quizzes, six archetypes each, share images. Build the quiz
  engine natively in React-free vanilla JS, driven by a JSON structure, not an embedded tool.
- **Menu, header and footer** — the persistent bar with the small YAMS mark and an **Index**
  overlay listing all rooms. This replaces the temporary "back to profile" links in each room.
  Footer carries the socials, a contact link and "re-enter through the gate".
- **Then:** mobile pass, proofreading, link and form testing, 404 page, favicon, social share
  images, unblock search engines, launch.

Suggested order: menu and footer next, since the rooms are accumulating and navigation is
currently held together with individual back buttons.

---

## 9. Open items

See `OPEN-TASKS.md` in the same repo. The important ones:
- Three live domains but the Web3Forms key is registered to one. Redirect `www.` and `yams.`
  to `aaryousus.com` in Cloudflare before launch.
- Automatic reply email to people who submit needs Web3Forms paid (~$8/month). Template drafted.
- Sus Blog auto-subscribe needs a mailing tool (Buttondown or Substack) once the blog exists.
- LinkedIn live embeds need full post URLs containing the activity ID.
- University of North Carolina department name unverified and currently omitted.

---

## 10. How to start the next chat

Attach or paste **three files**: this one, `index.html`, `OPEN-TASKS.md`. Ideally add them to
the Claude project so every new chat sees them automatically.

Then say: *"Continuing the YAMS website build. Read the handover. We're building [room]."*

Two practical notes. Screenshots are the most expensive thing in a conversation and are why
the previous chat filled up — describe problems in words where possible, and send one image
rather than five. And when something is wrong, she will say so directly; that is useful signal,
not a reason to over-apologise. Fix the thing, explain what actually caused it if it was a bug
rather than a preference, and move on.
