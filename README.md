# JARVIS Pocket Assistant

A responsive, installable progressive web app (PWA) starter for phones and tablets. It includes a voice-ready chat UI, text-to-speech replies, browser shortcuts, local notes, date/time, a safe basic calculator, and an optional OpenAI Responses API backend with web search.

> This is a starter project, not an unrestricted device-control agent. Browsers do not let a website silently control every installed app or access private phone data. Each capability needs a supported API, integration, and often permission.

## Features
- Responsive phone/tablet UI with an animated assistant orb.
- Speech recognition where supported by the browser, plus typed input fallback.
- Browser speech synthesis for replies.
- Shortcuts to common websites and web searches.
- Notes saved in this browser's local storage (not synced across devices).
- Time/date and safe arithmetic calculator.
- OpenAI Responses API integration with web search; API key stays server-side.
- PWA manifest/service worker for installability.
- Production Basic Authentication using JARVIS_ACCESS_PASSWORD.

## Run locally
1. Install Node.js 20 or newer.
2. Copy `.env.example` to `.env`.
3. Set `OPENAI_API_KEY` and choose a long unique `JARVIS_ACCESS_PASSWORD`.
4. Run `npm start`.
5. Open `http://localhost:3000`.

No npm packages are required. Without an API key, browser shortcuts, notes and calculator work, but AI chat does not. OpenAI API usage may incur separate charges.

## Deploy on Render
1. In Render choose **New → Blueprint** and connect this repository.
2. Render reads `render.yaml` and asks for `OPENAI_API_KEY` and `JARVIS_ACCESS_PASSWORD`.
3. Enter secrets only in Render's environment variable prompt; never commit them to GitHub or paste them into chats.
4. Deploy and open the HTTPS URL on your phone/tablet. Use **Add to Home Screen** / **Install app**.
5. Allow microphone access if asked. Speech recognition varies by browser and device.

## Configuration
- `OPENAI_MODEL`: defaults to `gpt-6-astra`; change it to any model enabled for your API account.
- Notes are local to each device/browser and may be cleared if site data is cleared.
- For broader Android device control, a native Android app with explicit permissions is generally more capable than a browser PWA; iOS has stricter OS restrictions.

## Security
- Do not commit `.env` or API keys.
- The production site requires HTTP Basic Authentication.
- The lightweight in-memory per-IP rate limiter is not production-grade abuse protection.
- Recent chat messages are sent to the configured model when AI chat is enabled. Notes are not sent unless copied into chat.
