# End-to-end tests run in CI only, in the pinned Playwright Linux image

The Stop hook runs only the fast tier (lint, types, unit, affected tests) to keep the coding loop quick and cheap in tokens. Playwright runs in CI inside the official pinned Linux container, because screenshots differ between Windows and Linux renderers; an agent may run a single spec in that container while debugging, never by default.
