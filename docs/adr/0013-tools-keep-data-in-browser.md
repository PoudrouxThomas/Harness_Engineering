# Tools keep visitor data in the browser and never call external APIs

Each tool is a lazy-loaded Angular feature in its own folder, and a lint boundary forbids importing another tool's code, which keeps parallel worktrees conflict-free. To rule out data breaches, a tool's data never leaves the visitor's device: tools may use `localStorage` and `sessionStorage`, but never cookies, never the app's database, and never any external API. Without server-side storage or outbound calls, a raw idea designed to collect or exfiltrate visitor data has nothing to work with.

## Consequences

- No tool backend endpoints, and no tool data in Postgres; the .NET API serves only intake, the triage API and metrics.
- Allowed inside tool folders: `localStorage`, `sessionStorage`.
- Banned inside tool folders: cookies, IndexedDB, Cache API, service workers, and every network API (`HttpClient`, `fetch`, `XMLHttpRequest`, `WebSocket`, `EventSource`, `navigator.sendBeacon`).
- Enforced by a lint rule on tool folders and backed by a Content Security Policy restricting `connect-src` to the app's own API.
- Any idea that needs server-side storage or an external API is off-topic and closed as `wontfix`.
