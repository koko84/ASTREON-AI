# ASTREON AI — Multilingual AI workspace

**Tagline:** Intelligence Beyond Limits.

This repository contains the deployable web MVP for ASTREON AI. It includes a responsive React interface, multilingual chat UI, browser speech input/output where supported, information/legal pages, and a server-side AI chat endpoint.

## What works in this build

- Responsive chat interface for phones, tablets, and desktop browsers.
- Conversation requests sent to a server endpoint; the provider secret is read only on the server.
- Multilingual replies depend on the configured model/provider.
- Speech-to-text and text-to-speech use browser capabilities and vary by device, language, and browser.
- The active chat is saved locally in the current browser on the same device; it is not synced to an account or cloud.
- About, How to Use, Privacy Policy, Terms of Use, and Contact pages.
- Basic request validation and a simple in-memory rate limit in the included API examples.
- Vercel-compatible serverless endpoints in `/api` and a local Express API in `/server`.

## Not included yet — do not advertise these as live features

- User registration, login, password reset, or persistent cloud chat history (only the active chat is stored locally in the browser).
- Subscription checkout, billing portal, invoices, or paid plan enforcement.
- Real image generation, image editing, file upload, or PDF/document analysis.
- Admin dashboard, analytics dashboard, or customer support ticket system.
- Production-grade distributed rate limiting, abuse monitoring, or a formal security audit.
- A published Android APK. Capacitor configuration is included, but Android packaging requires Android build tooling and testing.

The interface labels unavailable image/document tools as planned features. Keep those labels until the corresponding backend integrations are implemented and tested.

## Requirements

- Node.js 20 or later (recommended).
- An AI provider account and server-side API key for live AI replies. Provider usage may cost money; hosting this code for free does not make model inference free.

## Run locally

1. Install dependencies: `npm install`
2. Copy `.env.example` to `.env` and add a valid provider key to `AI_API_KEY`.
3. In terminal 1, start the API: `npm run server`
4. In terminal 2, start the web app: `npm run dev`
5. Open the local URL printed by Vite.

Never commit `.env`, API keys, or other credentials. Never put provider keys in variables prefixed with `VITE_`.

## Deploy the web MVP to Vercel

1. Upload this project to a GitHub repository.
2. Import that repository in Vercel. The project uses Vite; the normal build command is `npm run build` and output directory is `dist`.
3. In Vercel Project Settings → Environment Variables, add:
   - `AI_API_KEY` — secret key from the chosen provider
   - `AI_BASE_URL` — provider-compatible API base URL (for OpenAI-compatible APIs, normally `https://api.openai.com/v1`)
   - `AI_MODEL` — model name enabled for that provider account
4. Redeploy after adding or changing environment variables.
5. Test `/api/health`, then send a short test message in the app.

The `/api` directory contains Vercel serverless functions. The local Express server is provided for local development or a compatible Node host; do not assume a Vercel static deployment will run the Express process.

## Important production work before public commercial launch

- Choose the legal operator and publish accurate business/contact details.
- Review privacy, terms, age requirements, and consumer rules for each target country with a qualified adult/legal professional.
- Select a payment provider that explicitly supports the operator's country and business structure. Do not enable paid plans until checkout, webhook verification, subscription status, cancellations, refunds, and tax handling are implemented and tested.
- Add a database and authentication provider before promising accounts or saved history.
- Replace the in-memory rate limiter with a shared store (for example Redis) before scaling; serverless instances do not share memory.
- Configure provider spending limits, monitoring, request quotas, and abuse protection.
- Add real image and document services only after their upload, storage, privacy, and cost controls are implemented.
- If using advertising, obtain approval first, add the correct publisher code, consent controls where required, and real ad placements. Placeholder areas are not live ads and do not guarantee approval.
- Test accessibility, mobile behavior, API failures, and security before launch.

## Environment variables

See `.env.example`. Keep all secrets on the server. The current MVP does not collect payments or create user accounts.

## Contact

Project contact: karim071984@gmail.com

---

ASTREON AI is an evolving software project. The legal pages in this repository are starter disclosures, not legal advice or a guarantee of compliance with Google AdSense, Google Play, or any country's laws. Update them to match the actual production architecture before launch.
