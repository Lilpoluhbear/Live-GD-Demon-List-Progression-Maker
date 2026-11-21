# APL Demon List and Progression List

A single-page website for Geometry Dash players who want to plan which extreme demons to beat and in what order. It shows the live All Rated Extreme Demon List (AREDL) and lets each visitor build their own progression list from it.

## What it does

- **Demon List.** Shows every level on the AREDL, ranked, with the level image, rank, publisher, verifier and level ID. A search box filters by name, publisher, verifier or level ID.
- **Progression List.** A personal list of the levels you chose. Levels always stay in AREDL rank order.
- **Adding and removing.** Clicking a level in the Demon List opens a confirmation ("Are you sure you want to add this to your Progression List?"). Clicking a level in the Progression List opens the matching remove confirmation. The red X cancels and the green check confirms.
- **Beaten levels.** Hovering a level in the Progression List shows a green check button. Clicking it tints the row green. Click it again to undo.
- **Level video.** Clicking a level's image opens its verification video in a new tab.
- **Live updates.** The list reloads from the AREDL every 5 minutes while the page is open. A saved copy is used if the AREDL cannot be reached.

## Files

| File | Purpose |
| --- | --- |
| `index.html` | The whole site (HTML, CSS and JavaScript in one file). |
| `logo.png` | Optional. Your APL logo, shown top left. Without it the page shows plain "APL" text. |
| `bg.jpg` | Optional. Your background image. Without it the page uses a red gradient. |

Put `logo.png` and `bg.jpg` in the same folder as `index.html`.

## Hosting

The site is a static file, so any static host works, for example GitHub Pages, Cloudflare Pages, Neocities, Vercel or GitLab Pages. Upload `index.html` (plus the optional images) and open the link you get.

## Data sources

- Level list: `https://api.aredl.net/v2/api/aredl/levels` (rank, name, level ID, status).
- Level details: `https://api.aredl.net/v2/api/aredl/levels/<id>` (publisher, verifier, verification video, used for the image). Details load for each level as it scrolls into view and are saved in the browser.

The level image is the thumbnail of the verification video on YouTube.

## Where data is stored

Each visitor's Progression List and beaten marks are saved in their own browser (localStorage). Lists are not shared between people or devices, and clearing browser data erases them.

## Known limits

- The AREDL does not provide a creator or a publish date, so those are not shown.
- Levels with no verification video show the level name where the image would be.
- Details load as you scroll, so publisher and verifier show "..." briefly for new rows.
- If the AREDL changes its API or blocks requests from other websites, the page shows an error message. Report the message to whoever maintains the site.
- This was written without being able to test against the live API from the build environment, so check it after each change.
