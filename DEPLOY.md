# Putting this site live on GoDaddy

This site is plain static HTML — one `index.html` file plus an `images/` folder.
There is no database, no PHP, no build step, and no server code. That makes it
about as easy to host as a website gets: **whatever you upload is what visitors see.**

The only real question is *which GoDaddy product* the restaurant is paying for,
because two of them can host this and one of them cannot.

---

## Step 1 — Find out what GoDaddy plan they actually have

Log in at godaddy.com and open **My Products**. Look at what's listed:

| What you see | What it means | Can it host this site? |
|---|---|---|
| **Web Hosting** / **cPanel Hosting** / **Linux Hosting** | Real hosting with a File Manager and FTP | **Yes** — see Option A |
| **Website Builder**, **Websites + Marketing**, **Airo Sites** | GoDaddy's drag-and-drop builder | **No** — see Option B |
| Only a **Domain** (no hosting line item) | They own the name, nothing is hosted | **Yes, but** — see Option C |

If more than one is listed, the one currently serving bamboo-sushi.com is
whichever the domain's DNS points at. When in doubt, call GoDaddy support and ask
"is my plan cPanel hosting or Websites + Marketing?" — they'll tell you in a minute.

---

## Option A — GoDaddy Web Hosting (cPanel). The easy path.

This takes about ten minutes.

1. Download this repo as a ZIP (green **Code** button on GitHub → **Download ZIP**),
   then unzip it on your computer.
2. In GoDaddy: **My Products → Web Hosting → Manage → cPanel Admin**.
3. Open **File Manager**.
4. Go into the **`public_html`** folder. This folder *is* the website.
5. If there's an existing site in there you're replacing, select everything and
   move it into a new folder called `old-site-backup` first. Don't delete it until
   the new site is confirmed working.
6. Upload **`index.html`** into `public_html`.
7. Upload the whole **`images`** folder into `public_html`, so you end up with
   `public_html/images/food/...`, `public_html/images/menu/...`, and so on.
   - Faster method: zip the `images` folder, upload the single zip, then use
     File Manager's **Extract** button.
8. Visit the domain. Done.

**The one thing that breaks this:** if the `images` folder doesn't sit *next to*
`index.html`, every photo shows as a broken icon. The final layout must be exactly:

```
public_html/
├── index.html
└── images/
    ├── awards/
    ├── brand/
    ├── food/
    ├── gallery/
    └── menu/
```

Folder and file names are **case-sensitive** on the server. `Images/` will not work.

---

## Option B — GoDaddy Website Builder (Websites + Marketing)

**This one cannot host this site,** and it's worth being clear about why: the builder
is a closed system. You get their drag-and-drop blocks and their templates. There
is no way to upload your own `index.html` and have it become the page. There's no
"custom HTML page" escape hatch — their embed widget only drops a small snippet
*inside* one of their blocks, which won't work for a full site like this one.

So there are three honest choices:

1. **Switch the GoDaddy plan to cPanel Web Hosting**, then follow Option A.
   Costs money, keeps everything under one GoDaddy login. Call support and ask
   them to move you — they do this all day.
2. **Keep the domain at GoDaddy, host the files somewhere free** (Option C below).
   This is what I'd recommend. It costs nothing and the site loads faster.
3. **Rebuild this design inside their builder.** Not realistic — the custom layout,
   the awards carousel, the lightbox and the menu tabs don't exist as builder blocks.

---

## Option C — Keep the GoDaddy domain, host the files free

The domain stays with GoDaddy exactly as it is. Only the *hosting* moves. Visitors
never see a difference — bamboo-sushi.com still works normally.

**Cloudflare Pages** and **Netlify** both do this free, with automatic HTTPS, and
both can deploy straight from this GitHub repo — meaning any future change pushed
to the repo goes live on its own, with no re-uploading.

Rough shape of it:

1. Create a free account at Cloudflare Pages (or Netlify).
2. Connect this GitHub repository. Leave the build command **empty** and set the
   output directory to **`/`** — there's nothing to build.
3. It gives you a working temporary address like `bamboo-sushi.pages.dev`.
   Check the site there first.
4. Add `bamboo-sushi.com` as a custom domain in their dashboard. They'll show you
   the DNS records to create.
5. In GoDaddy: **My Products → Domain → DNS → Manage Zones**, and enter those
   records. Changes usually take effect within an hour.

Do step 3 before step 4. Confirm the site works on the temporary address, and only
then repoint the real domain.

---

## Before going live — a short checklist

- [ ] Open the site and click through it on a phone, not just a computer.
- [ ] Test the **Order Online** buttons — they point at the live ordering system.
- [ ] Test the three **location** links and phone numbers.
- [ ] Tap several photos to confirm the enlarge/lightbox works.
- [ ] Confirm HTTPS is on (padlock in the address bar). GoDaddy hosting includes a
      free certificate; you may need to switch it on in cPanel under **SSL/TLS**.

## Updating the site later

Whatever route you pick, updating is the same idea: change `index.html`, then
either re-upload it (Option A) or push to GitHub and let it deploy itself (Option C).
Option C is genuinely less work over time.
