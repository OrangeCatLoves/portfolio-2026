# Low Wei Bin: portfolio

One page, no build step, no database. Everything is in `index.html`.

## For Claude Code

This page is finished. **Do not rewrite it or split it into a framework.** Make small edits in place only.

## Folders

- `photos/` holds every photo.
- `videos/` holds the two project demo videos.
- `logos/` holds the three company logos shown on the Experience boarding passes.

## Where each file goes

| File | Slot in `index.html` | How to find the slot |
|---|---|---|
| `photos/weibin-1` | First page, photo 1 | search `Your photo 1` |
| `photos/weibin-2` | First page, photo 2 | search `Your photo 2` |
| `photos/weibin-3` | First page, photo 3 | search `Your photo 3` |
| `photos/dog.png` | About me, first card (Professor Woof) | search `hc-dog` |
| `photos/web/ratchetcat.jpg` | About me, second card (OrangeRatchetCat) | search `hc-cat` |
| `photos/weibin-2.JPG` | About me passport, the holder's photo on the first page | search `Marina Bay at night` |
| 6 photos in `photos/web/aboutme/` | About me passport, Traveller page (left), the scattered prints | search `class="pp-album"` |
| `photos/gamer/valorant-logo.svg` | About me passport, Gamer page (left) | search `valorant-logo` |
| `photos/gamer/overwatch-logo.png`, `photos/gamer/widowmaker.webp` | About me passport, Gamer page (right) | search `overwatch-logo` |
| `videos/valorant-gameplay.mp4`, `videos/overwatch-gameplay.mp4` (not added yet) | About me passport, Gamer pages, the clip at the bottom | search `gameplay clip` |
| 8 songs in `audio/`, e.g. `audio/starboy.mp3` | About me passport, Music page, the play buttons and the "On air" panel under them | search `class="pp-songs"` |
| `logos/shopback.jpg` | Experience, ShopBack boarding pass | search `logos/shopback` |
| `logos/continental.jpg` | Experience, Continental (AUMOVIO) boarding pass | search `logos/continental` |
| `logos/growthbeans.jpg` | Experience, Growthbeans boarding pass | search `logos/growthbeans` |
| `photos/internships/continental-1.jpg` to `-5.jpg` | Experience, the "5 photos" button on the Continental (AUMOVIO) pass | search `id="snaps1"` |
| `photos/internships/growthbeans-1.jpg` to `-3.jpg` | Experience, the "3 photos" button on the Growthbeans pass | search `id="snaps2"` |
| 15 photos named after places | Exchange photo grid | search `class="xph"` |
| `videos/minitude.mp4` | Projects, first postcard (Minitude) | search `videos/minitude.mp4` |
| `videos/guesstheflag.mp4` | Projects, second postcard (GuessTheFlag) | search `videos/guesstheflag.mp4` |
| `videos/ouruniverse.mp4` | Projects, third postcard (OurUniverse) | search `videos/ouruniverse.mp4` |

The exchange photos are named after the place, for example `Seattle.JPG`. Each button in the grid has the place name in its caption. Match them by name, ignoring upper and lower case, spaces, full stops and the file extension. The 15 places are:

UMD (University of Maryland), Washington D.C., Philadelphia, New York, Boston, Toronto, Chicago, Seattle, San Francisco, Yosemite, Los Angeles, Las Vegas, Grand Canyon, Orlando, Miami.

## How to swap a file in

- **First page photo:** replace `<div class="slot">Your photo 1</div>` with `<img src="photos/FILE" alt="Low Wei Bin">`.
- **About me photo:** change the `src` of the `<img>` inside the card's `<span class="hart">`.
- **Company logo:** change the `data-src` of the `<img>` inside `<span class="pass-logo nologo">`. The page loads it and only shows the logo once it has loaded, so a missing file hides the logo instead of showing a broken image.
- **Internship photos:** put the files in `photos/internships/` with the names above, or change the `data-src` of each `<img>` inside `<div class="snaps">`. One `<img>` per photo: add or remove lines to change how many there are, and the button's count follows. Until a file is there, its print shows a striped "Photo N". `data-cap="..."` on an `<img>` gives that print its own short caption instead of "1 / 5". Use web-sized copies (about 1600 px on the long side), like the ones in `photos/web/`.
- **Exchange photo:** replace `<span class="slot">Photo</span>` inside the button with `<img src="photos/FILE" alt="PLACE NAME">`. Keep the caption span after it.
- **About me photos (Traveller):** the page shows the web-sized copies in `photos/web/aboutme/` (about 1600 px, turned upright). The full-size originals stay in `photos/aboutme/`, which git ignores. To swap one, make a web-sized copy and change the `src` of its `<img>` inside `<div class="pp-album">`.
- **Gameplay clip:** replace the whole `<div class="pp-clip pp-clip-ph">…</div>` with `<video class="pp-clip" src="videos/FILE" autoplay muted loop playsinline></video>` (the comment above each one has the exact line). Keep each video under 25 MB.
- **Song:** put the audio file in `audio/` with the name in that song's `data-src` (for example `audio/starboy.mp3`), or change the `data-src`. `.mp3`, `.m4a` and `.mp4` all play. Until the file is there, its play button is faded with "coming soon". To add a song, copy one `<li>` and change its `data-src`, `data-name` and title.
- **Video:** change the `src` of the `<video>` on that project's postcard (search its file name, as in the table above). Keep `autoplay muted loop playsinline`.

The page already crops every photo to fit its frame, so no extra styling is needed.

## Two things that break on a live site but not on a laptop

- **File names are case-sensitive.** `Seattle.JPG` and `seattle.jpg` are different files. Use the exact name and extension.
- **Spaces in file names** must be written as `%20` in the `src`, for example `photos/New%20York.JPG`.

## Things to confirm with Wei Bin

- The order of the 15 exchange stops on the map was guessed.
- The About text says "building and explore new tech tools". "Exploring" may be what was meant.

## Deploy

The site runs as a Cloudflare Worker named `portfolio-2026` (static files only, set up in `wrangler.jsonc`) and is served at weibinlow.com. Every push to `main` on GitHub deploys it automatically through Workers Builds. Claude Code should push to GitHub and stop there.

Build settings, in the Cloudflare dashboard under Workers & Pages → portfolio-2026 → Settings → Builds:

- Git repository: `OrangeCatLoves/portfolio-2026`, production branch `main`
- Build command: none
- Deploy command: `npx wrangler deploy`
- Root directory: `/`

If a push does not show up on the site, check that page for a "disconnected from your Git account" banner. Click **Manage** next to the repository and give the Cloudflare app access to this repo on GitHub, then push again.

**Each file must be 25 MB or smaller, or Cloudflare will not deploy it.** Check the two videos.
