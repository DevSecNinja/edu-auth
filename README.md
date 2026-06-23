# edu-auth — Zero Trust MFA Guardrails for Education

An interactive, **non-technical** web page that helps schools choose the
right multi-factor authentication (MFA) and Zero Trust guardrails — **per person and per device** —
and shows a realistic *Good → Better → Best* path instead of an all-or-nothing leap.

It directly tackles two objections heard constantly in K-12 / EDU:

- *"We can't do MFA for students — they don't have a phone or can't use one in class."*
- *"Temporary Access Pass is too much admin work."*

## Who it's for

Built to be shown to **CIOs and IT managers**. Plain language, a glossary, and a printable one-pager
make it a useful conversation tool in customer meetings.

## What's inside

- **Interactive selector** — pick a persona (Admin, Non-teaching staff, Teacher, Student) and the
  device reality (organisation-owned vs personal, managed / MAM / unmanaged, personal vs shared) to
  get a tailored recommendation.
- **Maturity ladder** — a 4-rung visual (L0 Password-only → L3 Zero Trust) highlighting the
  recommended target for the selection.
- **Good / Better / Best cards** — concrete, actionable steps with a short "why it helps" for each.
- **Admin gold lane** — the non-negotiable four: phishing-resistant MFA, PIM, separate cloud-only
  account, and an optional Privileged Access Workstation.
- **"Students without a phone" section** — the phone-free, phishing-resistant menu plus a checklist
  to make Temporary Access Pass (TAP) low-effort for IT.
- **Plain-language glossary** and hover tooltips for jargon (TAP, FIDO2, Windows Hello, PIM, PAW, MAM).
- **Print / save** button producing a clean customer-ready one-pager.

## How to use

Open `index.html` in any modern browser — no build step, no dependencies, no server required.

## Deploy to GitHub Pages

A workflow is included at `.github/workflows/pages.yml` that publishes the repository root.

1. Push to the default branch.
2. In the repository, go to **Settings → Pages** and set the source to **GitHub Actions**.
3. The site publishes automatically on each push, at `https://<owner>.github.io/edu-auth/`.

(Alternatively, enable Pages directly on the root of the branch — the site is a single static file.)

## Source &amp; disclaimer

This is independent enablement material, **not an official Microsoft document**. Always validate
against current Microsoft Learn guidance and your own licensing. Primary reference:
[Passwordless for Students — Microsoft 365 Education](https://learn.microsoft.com/en-us/microsoft-365/education/guide/1-reference/protect-passwordless-students).
