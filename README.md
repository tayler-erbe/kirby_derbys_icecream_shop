# 🍦 Kirby Derby's Ice Cream

A family-owned (pretend-play) ice cream shop website for Charlie & Wesley Erbe.

This is a **faux website for pretend play** — but it's built so that if it ever
becomes a real business, the real pieces just plug in. No rebuild needed.

**Live domain (planned):** KirbyDerbysIcecream.com

---

## Folder structure — IMPORTANT

Your repo must look exactly like this. The `images` folder has to sit next to
`index.html`, and the image filenames must match exactly:

```
kirby-derbys/
├── index.html
├── README.md
├── .nojekyll
└── images/
    ├── kirbyDerbysIcecreamShop_LogoBanner.png  (big hero sign)
    ├── KirbyDerbyIceCream.png             (small logo — nav + footer)
    ├── icecream.png                       (cartoon cone — Kirby's avatar)
    ├── KirbyDerbyBrothers.png             (photo of the brothers)
    ├── chocolate.png
    ├── old_fashion_vanilla.png
    ├── cookiedough.png
    ├── cookiemonster.png
    ├── chocolate_chip_mint.png
    ├── orange_mango_strawberry.png
    ├── raspberry_blueberry_strawberry.png
    └── rainbow_sherbert.png
```

All 13 flavors have real tub photos wired in. (Double Chocolate currently
reuses chocolate.png — swap it if you get a separate double-chocolate photo.)

---

## The site has 5 parts (all in index.html)

1. **Home** — the logo sign with cartoon cones, the brothers photo, info cards
2. **Flavors** — all 13 flavors with circular photo frames
3. **Shop** — cart with real math, 5-gallon-per-flavor limit, $25/gallon,
   $15 flat shipping, 2-week disclaimer, pretend checkout
4. **Game** — "Scoop Stacker," tap falling scoops before 3 stack up
5. **Chat** — "Kirby," a friendly rule-based helper bot

---

## How to test it

Open `index.html` in a web browser. Everything works offline — no build step.
(The images load from the `images/` folder, so keep them together.)

---

## How to put it on GitHub Pages (test/dev)

1. Create a new GitHub repository (e.g. `kirby-derbys`)
2. Upload **everything**: `index.html`, `.nojekyll`, `README.md`, AND the whole
   `images` folder with all 4 pictures inside it
3. In the repo: **Settings → Pages**
4. Under "Build and deployment," set **Source** to `Deploy from a branch`
5. Pick branch `main` and folder `/ (root)`, then **Save**
6. Wait ~1 minute. Live at: `https://YOUR-USERNAME.github.io/kirby-derbys/`

---

## How to go live on the real domain later (Vercel)

1. Push this repo to GitHub
2. At vercel.com, **Add New Project** and import the repo
3. Vercel auto-detects it as a static site — no settings needed
4. In the project's **Domains** tab, add `KirbyDerbysIcecream.com`

---

## Adding the other 12 flavor photos

When you have a flavor photo:

1. Put the image file in the `images/` folder
2. Open `index.html`, find the `FLAVORS` list (near the bottom, in the script)
3. Find that flavor and change `img:null` to `img:'images/YOUR-FILE.png'`

Example — for chocolate:
```
{ id:'chocolate', name:'Chocolate', emoji:'🍫', ... img:'images/chocolate.png', ... }
```

That's it. The photo auto-crops into the circular frame. Any flavor still set
to `img:null` just shows its emoji as a placeholder — nothing breaks.

---

## Making it "real" later — the plug-in spots

Open `index.html` and search for these tags:

- `[PLUG-IN: PAYMENT]` — the `checkout()` function. A real payment processor
  (like Stripe) goes here. **Needs a small backend** so the secret key is never
  in this public file — Vercel serverless functions make this easy.
- `[PLUG-IN: AI]` — the `getKirbyReply()` function. To make Kirby a real AI,
  replace the rule-based replies with a call to a small backend that talks to
  the Anthropic API. **The API key stays on the server, never here.**
- `[PLUG-IN: IMAGES]` — adding the remaining flavor photos (see above).
- `[PLUG-IN: CONTACT]` — the footer. Add real contact info only when you're
  ready for it to be public.

The game and the shopping cart math stay 100% static forever — only payment
and the real AI chatbot need that small backend.

---

Built for play. Ready for real. 🌈
