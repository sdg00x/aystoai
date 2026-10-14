# Architecture

How aystoai.com is put together, so you can find things before you change them.

## Principles

- **One file per page.** Each page carries its own HTML, CSS and JavaScript. Nothing is shared at build time because there is no build.
- **Config at the bottom.** Values that change (links, IDs, offer text) sit in a `CONFIG` object at the bottom of the page script, not scattered through the markup.
- **Works without JavaScript where it matters.** Links, copy and the booking fallback all work if a script fails. JavaScript adds the demo call, calculator, filters and animation on top.
- **Fast on a phone.** No framework, fonts preconnected, audio loads only when someone presses play.

## Page map

```text
aystoai.com
├── /                      site/index.html            Clinics
├── /business              site/business/index.html   Local businesses
│   └── /websites          → 301 to /business (site/_redirects)
└── /blog                  site/blog/index.html       Article index
    ├── /blog/speed-to-lead
    ├── /blog/missed-calls
    ├── /blog/price-dms
    ├── /blog/no-shows
    ├── /blog/patient-recall
    ├── /blog/clinic-website
    ├── /blog/google-reviews
    └── /blog/ai-medical-advice
```

Netlify serves `/blog/missed-calls` from `blog/missed-calls.html` automatically, so links can drop the `.html`.

## Clinic homepage: section order

| # | Section id | Purpose | Interactive parts |
| --- | --- | --- | --- |
| 1 | hero | Headline, main CTA, phone mockup | Plays `media/clinic-call.mp3` with a live caller UI |
| 2 | `problem` | The cost of missed calls | Scroll reveal |
| 3 | `offer` | The 14 day receptionist offer | Founding places counter from `CONFIG` |
| 4 | `admin` | Jobs taken off the team | |
| 5 | `services` | Receptionist first, automation after | Demo call player |
| 6 | `calculator` | Missed call cost calculator | Inputs update the monthly figure live |
| 7 | `usecases` | Clinic types | |
| 8 | `how` | Steps to go live | |
| 9 | `founder` | Samuel, why AYSTO exists | Photo or initials from `CONFIG` |
| 10 | `blog` | Latest articles | |
| 11 | `faq` | Common questions | |
| 12 | `book` | Booking | Calendly popup, email fallback |

## Local business page: section order

| # | Section id | Purpose |
| --- | --- | --- |
| 1 | hero | 7 day website offer, mockup preview cards |
| 2 | `problem` | What a weak site costs |
| 3 | `how` | Mockup first, pay when happy |
| 4 | `prices` | Two packages, from £950 |
| 5 | `addons` | Booking, AI chat, video |
| 6 | `case-study` | Client write-up (template, placeholders until the first case study) |
| 7 | `faq` | Questions |
| 8 | `mockup` | Free mockup request form (Formspree) |

## Third-party services

| Service | Where it's called | If it's down |
| --- | --- | --- |
| Calendly | Booking buttons, `CALENDLY_URL` | Buttons fall back to an email to `CONTACT_EMAIL` |
| Formspree | Mockup and contact forms | Form falls back to opening an email |
| Plausible | One script tag in `<head>` | Page works as normal, stats pause |
| Google Fonts | `<link>` in `<head>` | System fonts take over |

No API keys or secrets live in this repo. Formspree form IDs and Calendly links are public by design.

## Audio

| File | Plays on | Notes |
| --- | --- | --- |
| `site/media/clinic-call.mp3` | Clinic hero and services | Current demo: "Ava" answering for a clinic |
| `site/media/demo-call-v1.mp3` | Not linked | Earlier take, kept for reference |
| `site/business/plumbing-call.mp3` | `/business` | Trades example |

Audio uses `preload="none"` or `"metadata"`, so nothing downloads until someone presses play.

## Changing things safely

1. Run the site locally (see the README).
2. Change copy in the HTML, values in `CONFIG`, colours in the `:root` block.
3. Check the page on a phone-sized window as well as desktop.
4. Push to `main`. Netlify deploys it.
