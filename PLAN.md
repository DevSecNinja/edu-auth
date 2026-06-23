# Plan: EDU Zero Trust MFA Visualizer

An interactive, customer-facing web page that lets a CIO/IT manager pick a **persona**
(Admin, Non-teaching staff, Teacher, Student) and their **device reality** (company vs personal,
managed/MAM/unmanaged, 1:1 vs shared) and instantly see a **Good → Better → Best** path up a
Zero Trust maturity ladder — with concrete, non-technical, actionable steps. It directly answers
"students can't use a phone" and "TAP is too much admin work," grounded in the Microsoft Learn
*Passwordless for Students* guidance.

## Format & hosting

- **Single self-contained `index.html`** (vanilla JS + CSS + inline SVG). No build step, no npm
  dependencies, GitHub-Pages-ready, nothing to maintain. Deliberately avoiding a React/Vite build —
  it adds dependency upkeep without better visuals at this scope.
- **Hosting:** GitHub Pages (static, public repo).
- **Branding:** customer-facing, clean & neutral, **no Microsoft internal logos**. Accessible palette.

## Axes & personas

- **Primary axes:** Persona × Maturity level.
- **Context modifiers** within each: device ownership (company vs BYOD/personal), device management
  (Entra-joined/Intune managed | MAM-only | unmanaged), and 1:1 vs **shared** device.
- **Personas:** Admins, Non-teaching staff, Teachers, Students.
- Platform is intentionally **not** a primary axis (kept as context only).

## Content model (grounded in MS Learn "Passwordless for Students")

Maturity ladder (Zero Trust aligned), 4 rungs:

- **L0 Password-only** = the RISK (what NOT to stay on). Show what it fails to mitigate.
- **L1 Baseline / "Mitigate something today"**: Conditional Access basics, block legacy auth,
  MFA where possible, MAM for BYOD.
- **L2 Better**: device compliance signals, phishing-resistant where feasible, scoped admin.
- **L3 Best / Gold (Zero Trust)**: phishing-resistant passwordless everywhere; for **Admins** =
  phishing-resistant MFA + PIM + separate cloud-only account + optional PAW ("no excuses").

Single north-star (phishing-resistant) for all personas; only the *in-between* steps differ by
device reality.

### Student passwordless menu (device-bound, phishing-resistant)

- 1:1 Windows → Windows Hello for Business (TPM)
- 1:1 macOS → Platform SSO + Secure Enclave
- 1:1 iOS/Android → Passkeys in Authenticator (if mobile allowed)
- Shared Windows/macOS → **FIDO2 security keys** (MS recommendation for shared devices)
- Bootstrap for all = **Temporary Access Pass (TAP)** — no phone needed
- Conditional Access: require compliant device + phishing-resistant auth strength
- Authentication Methods policy: include students for TAP/FIDO2, exclude from Phone/SMS/Authenticator as needed

### Make TAP painless (reduce admin overhead)

- TAP-only, no password (enforce passwordless from day 1)
- Generate/distribute TAP at device handout / Autopilot enrollment
- **Delegate TAP creation to teachers / local IT** (scoped Authentication Administrator role)
- Self-service: enable methods, student calls IT for a TAP only when setting up
- Multi-use TAP with a sensible lifetime to reduce reissue churn
- Monitor rollout via Authentication Methods Activity reports

## Interaction & visuals

1. Selector panel: pick Persona + device ownership + management + 1:1/Shared.
2. Output: highlighted recommended rung on the maturity ladder + a **Good / Better / Best** card
   stack with concrete actionable steps (identity method, device control, access/CA, what risk it mitigates).
3. Animated SVG maturity ladder (4 rungs) showing current vs target and the in-between steps.
4. Admin track shown as a fixed "no excuses" gold lane (phish-resistant + PIM + separate account + PAW).
5. Dedicated "Students without phones" explainer + "Make TAP painless" checklist.
6. Non-technical tooltips / glossary (TAP, FIDO2, WHfB, CA, PIM, PAW, MAM).
7. CIO exec-summary banner ("why act now").
8. Print/export-friendly CSS so SEs can hand a one-pager to customers.

## Files to create

- `index.html` — the entire app (content data, selector logic, SVG ladder, glossary) in one portable file
- `README.md` — what it is, how to use, deploy note, MS Learn source links, "guidance not official MS doc" disclaimer
- `.github/workflows/pages.yml` — optional auto-deploy to GitHub Pages (or just enable Pages on root)
- Existing `LICENSE`, `renovate.json5` — left as-is

## Verification

1. Open `index.html` locally: every persona × device combination renders a coherent recommendation
   with no console errors.
2. Basic a11y pass: keyboard-navigable controls, aria labels, AA color contrast.
3. Print preview produces a clean customer-ready one-pager.
4. MS Learn reference links resolve; GitHub Pages render matches local.

## Open considerations

- File structure: single `index.html` (recommended, max portability) vs split files.
- Localization for Western EU (NL/FR/DE) is out of scope for v1, but content data will be structured
  to allow adding it later.

## Source

- Microsoft Learn — *Passwordless for Students (M365 Education)*:
  https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/protect-passwordless-students
