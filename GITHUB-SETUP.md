# Bamboo Sushi — GitHub Pages setup

## What's in this folder

```
index.html            ← the site (67 KB, was 698 KB)
images/
  brand/              ← logo (PNG + WebP)
  food/               ← plated food photos
  awards/             ← award plaques + press clippings
  gallery/            ← storefronts, signage, dining room
  menu/               ← menu page photos
  team/               ← staff photos
.nojekyll             ← tells GitHub not to run Jekyll (faster, fewer surprises)
.gitignore            ← keeps junk files out of the repo
```

**Rule to remember:** `index.html` and the `images/` folder must always sit
side by side. The site points at photos using *relative paths* like
`images/food/seared-ahi-tuna-sashimi-emerald-coast.webp` — meaning
"starting from wherever index.html is, go into images/food/…".

Move one without the other and every photo breaks.

---

## One-time setup

1. Go to github.com → **New repository**
2. Name it `bamboo-sushi` — make it **Public** (Pages is free on public repos)
3. Do NOT check "Add a README"
4. On the next screen click **uploading an existing file**
5. Drag this entire folder's contents in (index.html + the images folder)
6. Click **Commit changes**
7. Go to **Settings → Pages**
8. Source: *Deploy from a branch* · Branch: `main` · Folder: `/ (root)` · **Save**
9. Wait ~60 seconds. Your site is live at
   `https://YOURNAME.github.io/bamboo-sushi/`

## Pointing bamboo-sushi.com at it

1. Settings → Pages → **Custom domain** → enter `www.bamboo-sushi.com` → Save
2. At your domain registrar, add a **CNAME** record:
   - Host: `www`
   - Value: `YOURNAME.github.io`
3. For the bare domain, add four **A** records pointing at:
   `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`
4. Back in Settings → Pages, tick **Enforce HTTPS** once it's available
   (can take up to 24 hours)

---

## Swapping a photo later

1. Open the repo → `images/` → the right folder
2. **Add file → Upload files**, drop the new photo in
3. Keep the same filename to swap in place, or use a new descriptive one
   and update `index.html`
4. Commit. The site updates in about a minute.

## Filename rules — do not break these

- **All lowercase.** GitHub Pages runs on Linux. `Photo.JPG` and `photo.jpg`
  are different files there, even though Windows treats them as the same.
  This is the #1 cause of "it worked on my computer" broken images.
- **Hyphens, never spaces or underscores.** Google reads hyphens as word
  breaks; underscores it does not.
- **Describe the photo, include a keyword and a city where it's true.**
  `sushi-boat-menu-toryu-soryu-ouroboros.webp` — good.
  `IMG_4471.jpg` — invisible to search.

---

## Limits to stay under

| Limit | Value | Where you are |
|---|---|---|
| Repo / published site size | 1 GB | ~5 MB |
| Bandwidth | 100 GB/month (soft) | fine unless you go viral |
| Single file | 100 MB | largest is 333 KB |
| Browser-upload file size | 25 MB | fine |

**Worth knowing:** GitHub's terms say Pages isn't meant for sites "primarily
directed at facilitating commercial transactions." A marketing site that
links out to your ordering platform is on the safe side of that line. If you
ever move ordering onto the site itself, switch hosts — Cloudflare Pages has
no such clause and the migration is a DNS change, because relative paths
carry over untouched.
