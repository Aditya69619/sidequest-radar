# SIDEQUEST — your next good thing

A live discovery radar for student builders. Find hackathons, workshops, open calls and community events in one clean, personalized feed.

## Run locally

1. Install Node.js 20 or newer.
2. Copy `.env.example` to `.env` and add a TinyFish API key from [agent.tinyfish.ai](https://agent.tinyfish.ai).
3. Run `npm start` and open `http://localhost:3000`.

Without a key, the app uses clearly marked sample cards so the experience is still demoable. Live search runs three parallel TinyFish Search queries across distinct sources/categories, then TinyFish Fetch reads the best pages for proof and details. The key stays on the server.

## TinyFish pipeline

`preferences → parallel Search (hackathons / workshops / open calls) → deduplicate → Fetch top pages → normalize + score → live cards with source links`

The TinyFish Search and Fetch REST APIs use `X-API-Key`. Search returns structured titles, snippets and URLs; Fetch returns clean page content. See [TinyFish Search & Fetch](https://www.tinyfish.ai/free-search-fetch).

## Deploy

Deploy as a Node web service on Render, Railway, or any host that supports Node 20. Set `TINYFISH_API_KEY` as a server-side environment secret and use `npm start`. Do not place the key in browser code or commit `.env`.
