# Astrolabe announcements

Every copy of Astrolabe reads `news.json` here about every six hours and shows
the newest item when a member presses the megaphone at the top of their page.
Dan and Danny post here; nothing in this folder can run code on anyone's
computer.

## An item

```json
{
  "id": "short-unique-id",
  "date": "2026-11-14",
  "until": "2026-11-23",
  "title": "Up to 120 characters",
  "body": ["A paragraph.", "Another paragraph."],
  "image": { "name": "a-picture.webp", "alt": "What the picture shows" },
  "actions": [
    { "kind": "link", "label": "Read more", "url": "https://..." },
    { "kind": "chat", "label": "Start", "intent": "a-chat-name", "hint": "Send it when it reads right.", "phrase": "The words the member reads and sends to their agent." }
  ],
  "effect": { "name": "leaves", "when": "open" },
  "markCss": "#mark svg .globe-nodes circle { fill: #e2a33a; }"
}
```

- **Required:** `id` (lowercase letters, digits, hyphens), `date`, `title`.
  Newest `date` shows first.
- **`until`:** the day the megaphone stops sparkling for it, and the end of
  its mark look.
- **`image`:** a png, jpeg, webp or gif in `img/` here, under 2 MB. Never svg.
- **`actions`:** up to three buttons; the last one is the main button. A
  `chat` button puts its words in the member's chat box for them to read and
  send, so point its words at a guide that ships with Astrolabe.
- **`effect`:** `confetti`, `leaves`, `snow` or `sparkle`. `when: "open"` plays
  as the news opens; `"page"` plays once on each computer when the page loads.
  New effects arrive with a release.
- **`markCss`:** a look for the mark in CSS, every rule starting at `#mark`
  (optionally after `body.brain-working` or `body:not(.brain-working)`), plus
  `@keyframes` and `@media (prefers-reduced-motion: ...)`. No `url(`, no
  `@import`. It shows until `until`, or for a week.

Astrolabe checks every field and drops an item that breaks a rule, so a typo
hides that one item and leaves everything else alone.
