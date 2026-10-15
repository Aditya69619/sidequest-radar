# SIDEQUEST — your next good thing

A live discovery radar for student builders. Find hackathons, workshops, open calls and community events in one clean, personalized feed.

## Run locally

1. Install Node.js 20 or newer.
2. Copy `.env.example` to `.env` and add a TinyFish API key from [agent.tinyfish.ai](https://agent.tinyfish.ai).
3. Run `npm start` and open `http://localhost:3000`.

Without a key, the app uses clearly marked sample cards so the experience is still demoable. Live search runs three parallel TinyFish Search queries across distinct sources/categories, then TinyFish Fetch reads the best pages for context. Open any live result and choose **Verify with TinyFish Agent** for a goal-directed check of current dates, location, and registration status. Agent checks are on demand because they can consume TinyFish wallet credits. The key stays on the server.

## TinyFish pipeline

`preferences → parallel Search (hackathons / workshops / open calls) → deduplicate → Fetch top pages → normalize + score → live cards → optional Agent verification of a selected event`

TinyFish Search returns structured titles, snippets and URLs; Fetch reads the best pages; the Web Agent follows a goal on a selected event page and returns structured verification details. All three use the server-side `X-API-Key`. Search and Fetch are free; Agent runs can use wallet credits. See [TinyFish Search & Fetch](https://www.tinyfish.ai/free-search-fetch) and the [Agent API guide](https://www.tinyfish.ai/blog/web-scraping-in-python).

## Deploy

Deploy as a Node web service on Render, Railway, or any host that supports Node 20. Set `TINYFISH_API_KEY` as a server-side environment secret and use `npm start`. Do not place the key in browser code or commit `.env`.
