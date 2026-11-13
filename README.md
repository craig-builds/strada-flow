# Strada Flow — AI social media marketing studio

**Status:** private beta, being tested with two real businesses.

## The problem
Owners of small food and service businesses know social media matters, but don't have time to plan content, design posters or keep prices and menus accurate across posts. Generic AI tools make things up, such as wrong prices or off-brand visuals, which is damaging for a business that sells from a fixed menu.

## What it does
- **Learns each business** from onboarding details, a menu or service sheet, logo, photos and website, and keeps a separate profile and brand kit per client.
- **Plans and drafts** Facebook and Instagram stories, posts and ads in the business's voice. Designs are made in Canva so they stay on-brand and editable.
- **Keeps facts exact.** Menu items and prices come from the client's own data, not the model's imagination, and AI-made product images are flagged for human review.
- **Human in the loop.** Nothing is published until the owner approves it, and paid ad spend is off in the beta.
- **Publishes with progress.** Approved posts go out through the official Meta Graph API, with live status and clear, plain-English errors if something fails.

## Highlights
- Multi-client by design: each person signs in with their own account and can only ever see their own business.
- Cost-aware AI: uses free-tier or open models by default, with automatic fallbacks so the tool keeps working when a quota runs out.
- Built with Claude Code as my AI pair-programmer, with every change reviewed and tested.

## Stack
Python (FastAPI), Next.js and TypeScript, Vercel with private blob storage, Meta Graph API, Canva, Cloudflare Workers AI (Claude optional).

## Security
- Invite-only sign-up, salted password hashing, lockout after repeated failures, signed HttpOnly session cookies and cross-site request protection.
- Per-client data isolation enforced on every route; no secrets in the repo; the codebase and its history were scanned before this write-up.
- Customers never see raw provider errors, keys or account identifiers.

## Issues encountered & how I solved them
- **Generic AI tools invented menu items and prices** that didn't exist, which is unacceptable for a business that sells from a fixed menu. I solved this by making the client's own onboarding data (menu, prices, services) the only source of truth the content generator can draw facts from, with AI-made product imagery always flagged for human review rather than auto-published.
- **Free-tier AI models hit rate limits mid-task.** I built automatic fallbacks between providers so content generation keeps working on a quota failure instead of silently stalling for the client.
- **Multi-client isolation was the single highest-risk area** — one business ever seeing another's data would end the product. I enforced per-client scoping on every data-access route, not just at the UI layer, and had the codebase and its git history scanned for leaked secrets before treating any environment as production-ready.
- **Posting on a client's behalf through the Meta Graph API** meant failures (expired tokens, rejected media, rate limits) needed to be legible to a non-technical owner rather than surfaced as raw API errors, so every failure path is translated into plain-English status before it reaches the dashboard.

## Result
A working private beta, in real use by two paying-adjacent businesses, generating on-brand, price-accurate social content that owners approve before it goes out via the official Meta Graph API — with nothing published automatically and paid spend deliberately switched off until the beta proves itself.

## About this repository
This is a **showcase repository**. Strada Flow is a commercial product in development, so the source is private. © Craig Chadley Johnson. All rights reserved. See [LICENSE](LICENSE).

Built by [Craig Chadley Johnson](https://github.com/craig-builds) — johnsoncraig.dev@gmail.com
