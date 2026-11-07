# Olem Electrical

Demo website for **Olem Electrical** — domestic, commercial and industrial
electrical wiring, materials supply and consultancy. Suite F6, Central Plaza,
Central Business District, Abuja.

Built by [IconEdge Technologies LTD](https://github.com/owenwebDe).

Same engine as the TK-OLA and Fidotech demos — GSAP 3.13 + Lenis motion layer,
Three.js hero, the ported liquid-glass refraction — with its own identity and
its own hero scene.

## Running it

Static HTML. No build step, no dependencies to install.

```bash
npx serve .          # or any static server
```

Deploying: point Vercel, Netlify or any static host at this folder. `vercel.json`
and `netlify.toml` are included and only set cache and security headers.

## The look

Midnight navy ground, dusk blue structure, a slash of sunset orange.

| Token | Value | Job |
|---|---|---|
| `--paper` | `#070C16` | midnight navy ground |
| `--paper-2` | `#0D1524` | dusk — raised bands and panels |
| `--paper-3` | `#162034` | deepest surface / image placeholder |
| `--ink` / `--ink-2` | `#EEF2F8` / `#8795AC` | text and muted text |
| `--brand` | `#4C7DC4` | dusk blue — eyebrows, rules, step numbers, the conductor field |
| `--accent` | `#FF7A3D` | sunset orange — buttons, one word per headline, hovers |

Unlike the Fidotech build, the structural colour here clears **4.7:1** on the
ground, so dusk blue carries 12px text itself. That is what leaves orange free to
be a slash: it appears on the primary buttons, one word in each headline, the
supply numbers and the hover states, and nowhere else. Used more widely it stops
being a slash.

Orange buttons take near-black text — white on `#FF7A3D` is 2.6:1 and fails.

Every corner is square: `--r` and `--r-lg` are both `0`.

## The hero

Olem does **no solar**, so the flat solar-panel field used on the sister sites
would have been the wrong picture. `assets/hero3d.js` instead draws a grid of
upright conductors whose height is the load they carry; a current pulse crosses
the grid and the bars light from dusk blue up to sunset orange at peak.

The geometry is pivoted at its foot (`geo.translate(0, 0.5, 0)`) so bars grow
upward instead of centring, and the camera sits lower than on the panel sites —
the field is read across, not looked down on.

## The page

| Section | What it carries |
|---|---|
| Hero | the h1, the three facts, two actions, the conductor field |
| What we do | four service lines as an auto-running rail |
| Materials | the supply arm, as a bento |
| The work | four photographs |
| How it works | quote → deposit → test → handover, including when money changes hands |
| Why people call us | the referral statement |
| Get a quote | the form |
| Contact | address, phone, WhatsApp |

## The quote form

Olem has **no email address on file** and the site has no backend, so the form in
`#quote` composes its five fields into a single WhatsApp message and opens it.
It works on any static host, the enquiry arrives complete, and the client keeps a
copy in their own chat.

It is wired in `assets/app.js` (`quoteForm()`), and deliberately **before** the
reduced-motion bail-out — the form is the page's transaction, not an animation,
so it works with every effect switched off. The number lives in one place, the
`data-wa` attribute on the form.

To switch it to email later, replace the `window.open` call with a POST to a form
service; the field names (`job`, `where`, `size`, `name`, `detail`) are already
sensible.

## What the client asked for that is NOT in here

They asked for **sales and payment** and for **past projects**. Both are partly
open, and the gaps are deliberate rather than faked:

- **No live checkout.** The page explains how payment works — deposit to book
  the dates, balance on handover, by transfer or card — but there is no payment
  button, because that needs their Paystack or Flutterwave business account and
  public key. With the key it is about twenty lines of JavaScript and an amount
  coming from the quote; no backend needed for Paystack inline. **No account
  numbers are printed anywhere on the site** — none were supplied, and inventing
  them would be worse than useless.
- **No past projects.** None were supplied. The "The work" section therefore
  describes the *kind* of work and what is in each photograph — it does not claim
  any specific completed job, and there are no case studies, client names or
  figures. When real project photographs arrive, that section takes them as-is.
- **No prices.** The materials section says prices are quoted against your list,
  which is true and also avoids publishing cable prices that move weekly.

## Photographs are placeholders

**All four photographs in `assets/img/` are licensed stand-ins, not Olem's work.**
They are credited in `credits.html` under CC BY / CC BY-SA licences and were shot
in Europe and America. Four is thin — the sister sites carry twelve — which is
why this page leans on type, the bento and the 3D field instead. Real photographs
of Olem's own boards, risers and finished rooms would change this page more than
anything else in the repo.

## Still to confirm with the client

- **Email address** — there is none on the site at all right now
- **Logo** — the page uses a placeholder ring-and-bolt mark in dusk blue and orange
- **Payment account** — Paystack or Flutterwave, to turn the payment step into a button
- **Past projects** — photographs, and whether any client may be named
- Whether the address is "Suit F6" or "Suite F6" — written as **Suite** here
- Office hours, and whether they take emergency call-outs
- Any registration (CAC, NEMSA) they want shown — none is claimed at present
