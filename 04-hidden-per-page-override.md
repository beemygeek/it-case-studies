# 4. "Only one page looks wrong" — finding a hidden override

**Environment:** WordPress site with a commercial theme

## Situation
After updating the site logo in the theme's global settings, every page showed the new logo **except the homepage**, which kept showing the old one. The user's first guess was caching.

## Investigation
1. **Ruled out caching** — fetched the homepage logged out with caching bypassed: the HTML itself referenced the *old* image file, so the server was generating the wrong markup, not serving a stale copy.
2. **Ruled out the global setting** — re-read the theme's options page after a fresh reload: the new logo was saved correctly.
3. **Asked what's different about this page** — the homepage is a separate page object with its own settings. Expanding the editor's collapsed "page custom options" panel showed a per-page **"Override header settings: Yes"** with its own custom logo pointing to the old file.

This override lived in that page's metadata, so it was invisible from the global theme settings and the customizer.

## Action
Set the per-page override back to **No**, cleared the stale custom logo, saved, and verified the live homepage both logged in and logged out.

## Result
All pages consistent. Documented the cause so future "one page is different" reports check per-page overrides **first**.

## Lessons
- When one item differs from the rest, find what's *unique* to that item before blaming the shared system.
- Verify with an anonymous request — admin sessions can mask what users actually see.
