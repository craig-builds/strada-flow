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

## About this repository
This is a **showcase repository**. Strada Flow is a commercial product in development, so the source is private. © Craig Chadley Johnson. All rights reserved. See [LICENSE](LICENSE).

Built by [Craig Chadley Johnson](https://github.com/craig-builds) — johnsoncraig.dev@gmail.com
