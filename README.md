# Click Quotes

A lightweight single-page web app that shows a cute quote wherever the user taps/clicks.
Each interaction creates:

- A floating quote text
- Heart particles
- Sparkle burst
- A short chime sound

This project is static and deploys easily on GitHub Pages.

## Demo Behavior

When someone opens the page:

1. The page is intentionally minimal.
2. On each click/tap, a random cute quote appears at that position.
3. Hearts and sparkles animate out from that point.
4. A soft chime plays.

## Project Structure

```text
cute-click-quotes/
|- cute_quotes.html   # main app page
|- quotes.json        # custom quote templates
```

If deploying on GitHub Pages, rename `cute_quotes.html` to `index.html`.

## Features

- Click/tap anywhere interaction (`pointerdown`)
- Dynamic quote text with `{name}` placeholder replacement
- Fallback quote set inside HTML if JSON is unavailable
- Particle effects (hearts + sparkles) with CSS animations
- In-browser generated chime using Web Audio API
- No build step, no dependencies, no framework

## Local Run

### Option 1: Open directly

Double-click the HTML file in your browser.

Note: some browsers may block `fetch("./quotes.json")` on `file://`, but the app still works using built-in fallback quotes.

### Option 2: Run a local static server (recommended)

```bash
# Python 3
python -m http.server 8000
```

Then open:

`http://localhost:8000/cute_quotes.html`

This ensures `quotes.json` loads correctly.

## Customization

### Change display name

In `cute_quotes.html`, update:

```js
const DISPLAY_NAME = "name";
```

All `{name}` placeholders in quotes will use that value.

### Edit quote list

Update `quotes.json` with an array of strings.
Use `{name}` wherever you want the display name inserted.

Example:

```json
[
  "Hi {name}, have a beautiful day!",
  "{name}, you are awesome!"
]
```

### Adjust visuals

In the `<style>` block:

- Color theme is controlled by CSS variables in `:root`
- Quote/heart/sparkle animations are defined in keyframes
- Timing can be tuned in animation durations and JS particle lifetimes

## Deploy on GitHub Pages

1. Create a public repository (example: `cute-click-quotes`)
2. Upload project files
3. Rename `cute_quotes.html` to `index.html`
4. Go to `Settings -> Pages`
5. Under `Build and deployment`:
- Source: `Deploy from a branch`
- Branch: `main`
- Folder: `/(root)`
6. Click `Save`
7. Wait for deployment (usually 1-3 minutes)

Your site URL will be:

`https://<your-username>.github.io/cute-click-quotes/`

## Share on WhatsApp as URL

### Direct share

Send your GitHub Pages URL directly.

### Prefilled WhatsApp message link

Use:

`https://wa.me/?text=ENCODED_MESSAGE`

Example (replace username):

`https://wa.me/?text=Try%20this%20cute%20quotes%20page%3A%20https%3A%2F%2F<your-username>.github.io%2Fcute-click-quotes%2F`

For direct contact prefill:

`https://wa.me/<countrycodephonenumber>?text=ENCODED_MESSAGE`

Example number format: `919876543210` (no `+`, no spaces).

## Troubleshooting

- Page opens but no custom quotes:
  - Ensure `quotes.json` is in the same folder as the HTML file.
  - Use a static server instead of `file://`.
- GitHub Pages shows 404:
  - Confirm file is named `index.html`.
  - Confirm Pages source is `main` and `/(root)`.
  - Wait a minute and hard refresh.
- No sound on first interaction:
  - Some browsers require user interaction before audio; click/tap once again.

## License

Use freely for personal sharing and learning.
