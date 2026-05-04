---
name: browser-playwright
description: When the agent needs to view, navigate, screenshot, or interact with web pages — especially SPAs and JavaScript-rendered sites. Use when WebFetch returns incomplete/empty content, or when visual inspection of a page is needed.
metadata:
  version: 1.0.0
---

# Browser Capability (Playwright MCP)

You have access to a headless Chromium browser via the Playwright MCP server. This gives you full browser capability including rendering JavaScript/React/SPA pages that WebFetch cannot handle.

## When to use this skill

- **WebFetch fails or returns empty/partial content** — many modern sites (React, Next.js, Vue, Angular) render client-side and return minimal HTML to static fetchers.
- **You need to see what a page looks like** — take screenshots for visual QA or review.
- **You need to interact with a page** — fill forms, click buttons, navigate through flows.
- **You need rendered text** — extract the actual visible text after JavaScript execution.

## Available MCP tools

The Playwright MCP server provides these tools (prefixed with `mcp__playwright__` or similar):

### Navigation
- `browser_navigate` — navigate to a URL and wait for the page to load
- `browser_go_back` / `browser_go_forward` — browser history navigation

### Content extraction
- `browser_snapshot` — get an accessibility snapshot of the current page (structured text representation)
- `browser_take_screenshot` — capture a screenshot of the current page or a specific element
- `browser_get_text` — extract visible text content from the rendered page

### Interaction
- `browser_click` — click on an element (by text, selector, or coordinates)
- `browser_type` — type text into an input field
- `browser_select_option` — select an option from a dropdown
- `browser_hover` — hover over an element
- `browser_press_key` — press a keyboard key
- `browser_scroll` — scroll the page

### Tabs
- `browser_tab_list` — list open tabs
- `browser_tab_new` — open a new tab
- `browser_tab_select` — switch to a specific tab
- `browser_tab_close` — close a tab

## Usage patterns

### Quick page check
1. `browser_navigate` to the URL
2. `browser_snapshot` to get structured text content
3. Optionally `browser_take_screenshot` for visual verification

### Visual QA
1. `browser_navigate` to the URL
2. `browser_take_screenshot` to capture the rendered page
3. Read the screenshot image to verify layout and content

### Form interaction
1. `browser_navigate` to the page
2. `browser_click` or `browser_type` to fill in fields
3. `browser_click` to submit
4. `browser_snapshot` to verify the result

## Important notes

- The browser runs **headless** — there is no visible window.
- Vision capability is enabled — screenshots are returned as images you can analyze.
- PDF capability is enabled — you can render and read PDF content.
- The browser has a **no-sandbox** flag set for compatibility with the server environment.
- Each agent session gets its own browser context (cookies/state are not shared between agents).
- Navigation timeout is 60 seconds by default; action timeout is 5 seconds.
- Prefer `browser_snapshot` over `browser_take_screenshot` when you only need text content — it's faster and more structured.
