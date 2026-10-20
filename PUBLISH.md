The website reads https://raw.githubusercontent.com/TodorPapazov/good-morning-ai/main/catalog.json on every visit. Editing the app copy does not publish an episode. This repo does.

Done means today's date is the first id in catalog.json and the audio file is in this repo.

1. Produce the phone MP3 (80kbps mono is fine).
2. Base64-encode the MP3 bytes. No line breaks. Do not upload the raw MP3.
3. Create audio/YYYY-MM-DD.b64 with that text, on branch main, using the GitHub create-or-update file tool. owner TodorPapazov, repo good-morning-ai.
4. Read catalog.json and its blob SHA. Prepend today's episode. Do not remove older ones. Write it back with that SHA.

Episode shape:
{
  "id": "YYYY-MM-DD",
  "air": "Tuesday, October 20",
  "slot": "6:30 a.m. ET",
  "title": "short headline",
  "dek": "one line",
  "audio": "b64:https://raw.githubusercontent.com/TodorPapazov/good-morning-ai/main/audio/YYYY-MM-DD.b64",
  "host": "Leo Ward",
  "show": "Good Morning AI",
  "clock": { "duration": 300.0, "starts": { "open": 2.55, "spacex": 20, "anthropic": 60, "openai": 100, "nvidia": 140, "google": 180, "close": 230 } },
  "sections": [
    { "id": "open", "kicker": "Cold open", "headline": "", "dek": "", "reaction": "", "paragraphs": [""], "sources": [] }
  ]
}

Section ids must be open, spacex, anthropic, openai, nvidia, google, close.
Each news section's sources are { name, handle, href } with a real https://x.com/.../status/... link.
