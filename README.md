# Low Wei Bin: portfolio

One page, no build step, no database. Everything is in `index.html`.

## For Claude Code

This page is finished. **Do not rewrite it or split it into a framework.** Make small edits in place only.

## Folders

- `photos/` holds every photo.
- `videos/` holds the two project demo videos.

## Where each file goes

| File | Slot in `index.html` | How to find the slot |
|---|---|---|
| `photos/weibin-1` | First page, photo 1 | search `Your photo 1` |
| `photos/weibin-2` | First page, photo 2 | search `Your photo 2` |
| `photos/weibin-3` | First page, photo 3 | search `Your photo 3` |
| `photos/dog.png` | About me, first small frame | search `class="ab-ph"` |
| `photos/ratchetcat.png` | About me, second small frame | search `ab-ph2` |
| 15 photos named after places | Exchange photo grid | search `class="xph"` |
| GuessTheFlag video | Projects, first video frame | search `GuessTheFlag video goes here` |
| OurUniverse video | Projects, second video frame | search `OurUniverse video goes here` |

The exchange photos are named after the place, for example `Seattle.JPG`. Each button in the grid has the place name in its caption. Match them by name, ignoring upper and lower case, spaces, full stops and the file extension. The 15 places are:

UMD (University of Maryland), Washington D.C., Philadelphia, New York, Boston, Toronto, Chicago, Seattle, San Francisco, Yosemite, Los Angeles, Las Vegas, Grand Canyon, Orlando, Miami.

## How to swap a file in

- **First page photo:** replace `<div class="slot">Your photo 1</div>` with `<img src="photos/FILE" alt="Low Wei Bin">`.
- **About me photo:** replace `<span class="slot">Photo</span>` inside the frame with `<img src="photos/FILE" alt="">`.
- **Exchange photo:** replace `<span class="slot">Photo</span>` inside the button with `<img src="photos/FILE" alt="PLACE NAME">`. Keep the caption span after it.
- **Video:** replace the whole `<div class="slot">…</div>` inside `<figure class="vid">` with `<video src="videos/FILE" autoplay muted loop playsinline></video>`.

The page already crops every photo to fit its frame, so no extra styling is needed.

## Two things that break on a live site but not on a laptop

- **File names are case-sensitive.** `Seattle.JPG` and `seattle.jpg` are different files. Use the exact name and extension.
- **Spaces in file names** must be written as `%20` in the `src`, for example `photos/New%20York.JPG`.

## Things to confirm with Wei Bin

- The order of the 15 exchange stops on the map was guessed.
- The About text says "building and explore new tech tools". "Exploring" may be what was meant.

## Deploy

Wei Bin deploys this himself on Cloudflare Pages. Claude Code should push to GitHub and stop there.

Settings to use on Cloudflare Pages:

- Framework preset: None
- Build command: `exit 0`
- Build output directory: `/` (the repo root, where `index.html` is)

**Each file must be 25 MB or smaller, or Cloudflare Pages will not deploy it.** Check the two videos.
