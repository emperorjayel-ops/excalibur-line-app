# CLAUDE.md — Excalibur Line

Created by OPS' Broker

## Project

**Excalibur Line** — the app for OMNI-PRESENT SOLUTIONS, INC's overhead magnetic hover-rail line (Fort Valley, Georgia first): line information, memberships (Join / Black Card), and the public face of the Excalibur Line. Owner: Honorable Jay Ladon Dickey Sr. EL.

Front domain: **excaliburline.token** (regular fallback: champlainflyer.com). Google Play package: `com.omnipresentsolutions.excaliburline`.

## Tech in this folder

- `index.html` — the entire app: one self-contained HTML file (HTML/CSS/JavaScript inline, no build step, no framework, no server). Edit it directly.
- `privacy.html` — the hosted privacy policy page for the Play Store listing.
- `README.md` — project note. Keep it accurate when behavior changes.

There is no backend. Anything that looks like an account, sign-up, or payment today is session-only in the browser unless this file says otherwise.

## Standing rules (apply to every change)

- **Cross-platform, no exceptions:** must work on the owner's Samsung Galaxy S9 (SM-G960U), iPhones (Safari/WebKit), all other phones, and laptops/desktops. Responsive at every width.
- **Adjust to the device:** runtime feature detection and progressive enhancement — WebGL2 → WebGL1 → CSS fallback; camera AR → non-camera 3D preview → CSS; auto quality scaling; honor reduced-motion and low-power signals. Never hard-require a capability; degrade gracefully instead.
- **Lane separation:** Excalibur Line material stays Excalibur Line. No HIIYAH telecom branding in here; the hover train belongs to this project only.
- **Branding:** the gold sword-in-the-stone in front of the bullet train is the symbol — wordless as an icon, "Excalibur Line" across the top in header form. Train lettering is exactly "Excalibur Line" / "Fort Valley Georgia". The train is an overhead magnetic hover train hanging below a single top rail with a visible gap — no wheels, no ground track, **no train horn** (arrivals are announced by a speaker).
- **One-picture rule:** visuals blend into one seamless picture — matched lighting, perspective, color, shadows. Logos merge into the design with no visible outlines or background-box edges; never a pasted-on sticker look.
- **Cross-app sidebar:** every app in this family (Excalibur Line, FinSwap, HIIYAH, Dominion Network, PMI God's Eye) carries a sidebar linking to all the others. Keep it intact and uniform.
- **Credit:** the line "Created by OPS' Broker" / "Shared by OPS' Broker" stays in the files. Do not remove it, do not add any other creator name.
- **Honesty:** never present a demo, session-only feature, or simulation as live. Label anything not yet live as demo/preview until it is connected and verified working.

## ⭐ REAL PAYMENTS — the top requirement

Payments in this app must be **real transactions on the real Bitcoin blockchain**, not simulation.

Current state (verified 2026-11-25): the Join and Black Card payment flows are **demo only** — they build a demo payment request with a code, show no Bitcoin address, take no real payment, and sign-ups are session-only. That is the thing to fix.

Required implementation:

1. Replace the demo payment flow with **real wallet integration** on the open-source Bitcoin stack: **Bitcoin Core + Counterparty** (the same stack FinSwap uses).
2. Accepted payment assets: **Bitcoin (BTC), PERFECTCERTS, WEALTHTICKET** (Counterparty assets on the Bitcoin blockchain), and **Alpine Gold-backed currencies**.
3. **End users transact from their own real wallets.** Build receive addresses / payment requests / QR codes that the user's own wallet signs and broadcasts. Scan-to-send handoff to the user's wallet is the correct pattern.
4. **Never hold, request, receive, store, or transmit a user's seed phrase or private key — server-side or anywhere else.** No custodial key storage, ever. The public Bitcoin address alone is what a payment flow needs.
5. Confirmations and amounts must be checked against the real chain (Bitcoin Core / a Counterparty node or a public Counterparty API), not assumed from the UI.
6. Until a payment path is actually connected and verified with a real (even tiny) transaction, keep it labeled demo — then remove the demo label only for the path that is verified live.
7. Note: the app currently carries a SoFi referral link/button. Flag it to the owner before any store submission; do not silently expand advertising.

## Working notes

- Test every change at phone width (Galaxy S9) and desktop width before calling it done, and check Safari/WebKit behavior for anything using newer APIs.
- Report only completed, verified results. An attempt is not a result.
