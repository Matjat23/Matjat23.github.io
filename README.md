# My American Year

This is the code for my website, live at https://matjat23.github.io. It is a personal documentary of my year in the US: every place I visit becomes a chapter with photos, short video loops, my own narration and a few tips. The goal is to visit 100 US cities before August 2027.

## How it's built

The whole site is one HTML page with plain CSS and JavaScript, no framework and no build step on the server. Chapters, photos and captions live in one `FILM` object at the top of the script, and the page renders the home view or a chapter from the URL hash (`#chapter-tampa`).

Some details:

- The map is the US from the us-atlas TopoJSON, projected with D3 (geoAlbersUsa) ahead of time, so the page only draws saved SVG paths.
- Videos are short silent loops that only load and play while they're on screen.
- The language switch (English, Swedish, French) keeps English as the source in the page. `i18n.js` has the interface text and chapter text, and `i18n-caps.js` has every photo caption. Missing translations fall back to English.
- Each chapter also has its own small page under `chapter/` with its own preview image, so a shared link shows that city instead of the home page.
- The cartoon avatar in the About section follows the mouse and types out a short greeting in the current language.

## Photos

I process the photos locally before they go here. A Python script (Pillow, pillow-heif and FFmpeg) resizes them, removes all EXIF data including GPS, makes WebP thumbnails for the grids and turns videos into 8 second loops. Only places, food and views go on the site, no faces of friends or strangers.
