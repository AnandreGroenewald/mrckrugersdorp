# MR Computer Services Krugersdorp: website

The one-page website for **MR Computer Services Krugersdorp**, launching at **https://mrckrugersdorp.co.za**.

Everything lives in a few small files. There is nothing to install and nothing to build.

| File | What it does |
|---|---|
| `index.html` | The whole website (design, text and the little bit of code that runs it) |
| `images/` | Photos and the logo go here |
| `favicon.svg` | The little icon in the browser tab |
| `robots.txt` and `sitemap.xml` | Tell Google where to look |

To preview it, double-click `index.html`. It opens in your browser.

> **Right now the site is in PREVIEW MODE.** An orange ribbon sits at the top and Google is told **not** to list the page. Both come off on launch day (see step 5).

---

## 1. Swap in photos

Each photo spot on the page shows a dashed orange box marked **✏️ FILL IN: PHOTO**. You do **not** need to touch any code.

1. Save your photo with the **exact file name** below.
2. Put it in the `images/` folder.
3. Refresh the page. The photo replaces the dashed box on its own.

| Spot on the page | File name | Size (px) |
|---|---|---|
| Top of the page, next to the headline: shop front | `images/shop-front.jpg` | 1200 × 900 |
| Team: Jacky Du Preez | `images/team-jacky.jpg` | 600 × 600 (square) |
| Team: Anandre Groenewald | `images/team-anandre.jpg` | 600 × 600 (square) |
| Team: Rico Sinden | `images/team-rico.jpg` | 600 × 600 (square) |
| Team: the workshop team (wide photo) | `images/workshop-team.jpg` | 1600 × 700 |
| WhatsApp and Facebook link preview: shop front | `images/og-cover.jpg` | 1200 × 630 |
| The MRC logo | `images/mrc-logo.png` | 501 × 345 |

Tips:
- Save photos as **JPG** and keep each one **under 200 KB** so the site stays fast on a phone. Free tools such as squoosh.app shrink them.
- **Logo:** save the official logo from `https://www.mrcomputerservices.co.za/edotdev/wp-content/uploads/2024/05/mrc-computer-services.png` as `images/mrc-logo.png`. Until you do, the page loads the logo straight from the group website, so it always shows.
- Faces and the shop front look best in daylight, taken landscape on a phone.

## 2. Add prices

Every price spot reads **From R___** (with a **✏️ FILL IN** tag). Open `index.html`, search for `From R___` and type the price over the blanks, for example `From R350`. Then delete the little `✏️ FILL IN` tag next to it.

| Where | Spot |
|---|---|
| Services section | Laptop & PC repairs |
| Services section | Same-day parts |
| Services section | Upgrades & speed boosts |
| Services section | New & refurbished computers |
| Services section | Data transfers & backups |
| Services section | Home Wi-Fi & fibre setup |

Also fill in the **check-up fee** (search for `R___`). It appears in two places: **The MRC Repair Promise, step 2** and the quick answer **"What does it cost to check my laptop?"**.

Then update one more thing: near the top of `index.html`, in the FAQ block, the answer to "What does it cost to check my laptop?" says *"Message or call us for the current check-up fee."* Change it to include the fee so Google shows the same answer as the page.

The business cards say **Quote on request** on purpose. They need no price.

## 3. Add reviews

The page says **240+ reviews on Google** and has three review cards waiting for real reviews.

1. Open the branch's Google listing: https://maps.google.com/?cid=1700853532073906260
2. Pick three genuine reviews. Copy the words exactly as the customer wrote them.
3. In `index.html`, search for `paste the Google review here`. Replace the whole dashed `<span class="fill">…</span>` with:

```html
<p>"Paste the review here."</p>
<p class="who">Thandi · March 2026</p>
```

Use the customer's **first name**, then the **month and year**. Do this for all three cards.

## 4. Switch on tracking (Google Analytics and Meta Pixel)

The site already records the clicks that matter: WhatsApp, calls, directions, the free IT check and the contact form. It starts counting the moment you paste in the branch's own IDs. Until then it does nothing and nothing breaks.

1. Get the branch's own **GA4 Measurement ID** (looks like `G-AB12CD34EF`) and **Meta Pixel ID** (a long number). Use IDs that belong to this branch, not another branch's.
2. In `index.html`, near the top, find the two blocks marked **✏️ SWITCH ON**.
   - In the Google block, replace both copies of `G-XXXXXXXXXX` with the GA4 ID.
   - In the Meta block, replace `YOUR_PIXEL_ID` with the Pixel ID.
   - In each block, delete the `<!--` line above and the `-->` line below it (the "comment marks").
3. In the footer, find the `✏️ SWITCH ON` comment. Delete the `<!--` and `-->` around the sentence *"We count website visits with Google Analytics and Meta…"* so visitors can see it.
4. Open the site on your phone, tap a WhatsApp button, then check **GA4 → Reports → Realtime** and Meta **Events Manager → Test events**. You should see the event within a minute.

Events the site sends: `whatsapp_click` (with the service name), `call_click`, `directions_click`, `health_check_click`, `form_whatsapp_send` (with what the person needs and how they found us). In GA4, mark the first two and the last two as **key events** so they show up as leads.

## 5. Launch day

**Before you go live**
- Search `index.html` for `✏️`. There should be nothing left except the lines you have already dealt with.
- Make sure `images/og-cover.jpg` and `images/mrc-logo.png` are in place.
- Check the link to the Nelspruit branch page opens the right page (it is the only sister-branch link not copied word for word from the group site).

**Take off the preview markings** in `index.html`:
1. Delete the orange ribbon: everything from `<!-- PREVIEW RIBBON …` down to `<!-- /PREVIEW RIBBON -->`.
2. Delete the line `<meta name="robots" content="noindex">` **and** the comment above it (`PREVIEW MODE: delete the next line on launch day`). This is what lets Google list the site.

**Connect mrckrugersdorp.co.za**

> ⚠️ **Do the email records first, or email will stop working.**
> Before you change anything, open the domain's current DNS settings and copy **every existing email record** into the new DNS: the **MX** records, the **SPF** record (a TXT record starting `v=spf1`), any **DKIM** records, and the Microsoft 365 verification record (a TXT record starting `MS=`). Check they all match, **then** point the website records.

1. Free hosting that works well here is **GitHub Pages**: repository **Settings → Pages → Deploy from a branch → `main` / root → Save**. Cloudflare Pages or Netlify also work.
2. In Pages, type `mrckrugersdorp.co.za` as the custom domain, then tick **Enforce HTTPS** once it becomes available.
3. At the domain's DNS host, point the website records at the host. For GitHub Pages: four **A** records for `@` to `185.199.108.153`, `185.199.109.153`, `185.199.110.153`, `185.199.111.153`, and a **CNAME** for `www` to `<github-username>.github.io`. (Check GitHub's Pages help for the current addresses.)
4. Wait for DNS to update (usually under an hour, sometimes longer), then open https://mrckrugersdorp.co.za on your phone.

**After launch**
- Tap every button on a real phone: WhatsApp opens with a message ready, Call dials 011 273 0060, Directions opens Google Maps.
- Add the new website address to the Google listing so customers can find it.
- Add `https://mrckrugersdorp.co.za/sitemap.xml` in Google Search Console.

## When something changes

- **Opening hours** appear in four places, so change all four: the **Come say hello** table, the footer, the `openingHoursSpecification` in the data block near the top of `index.html`, and `MRC_HOURS` in the script at the bottom (it drives the green or orange "Open now" badge).
- **Phone or WhatsApp number:** search `index.html` for `27112730060` (calls) and `27718651567` (WhatsApp) and replace every one.

## Fill-in list

Every item still waiting on the branch. Search `index.html` for `✏️` to find them.

| # | What is needed | Where it shows | What to give us |
|---|---|---|---|
| 1 | Shop-front photo | Top of the page, beside the headline | `images/shop-front.jpg`, 1200 × 900 |
| 2 | Price: Laptop & PC repairs | Services card | `From R___` |
| 3 | Price: Same-day parts | Services card | `From R___` |
| 4 | Price: Upgrades & speed boosts | Services card | `From R___` |
| 5 | Price: New & refurbished computers | Services card | `From R___` |
| 6 | Price: Data transfers & backups | Services card | `From R___` |
| 7 | Price: Home Wi-Fi & fibre setup | Services card | `From R___` |
| 8 | Check-up fee | Repair Promise, step 2 | `R___` |
| 9 | Check-up fee | Quick answers: "What does it cost to check my laptop?" (also the FAQ data block near the top) | `R___` |
| 10 | Google review 1 | Reviews | Words, first name, month and year |
| 11 | Google review 2 | Reviews | Words, first name, month and year |
| 12 | Google review 3 | Reviews | Words, first name, month and year |
| 13 | Photo: Jacky Du Preez | Team | `images/team-jacky.jpg`, 600 × 600 |
| 14 | Photo: Anandre Groenewald | Team | `images/team-anandre.jpg`, 600 × 600 |
| 15 | Photo: Rico Sinden | Team | `images/team-rico.jpg`, 600 × 600 |
| 16 | Photo: the workshop team | Team (wide card) | `images/workshop-team.jpg`, 1600 × 700 |
| 17 | Parking or landmark tip | Come say hello | One short line, e.g. "Parking in front of the shop" (only if true) |
| 18 | Link-preview photo | WhatsApp and Facebook shares | `images/og-cover.jpg`, 1200 × 630 |
| 19 | Google Analytics ID | `<head>` block marked SWITCH ON | The branch's own `G-…` ID |
| 20 | Meta Pixel ID | `<head>` block marked SWITCH ON | The branch's own Pixel ID |
| 21 | Tracking sentence | Footer comment marked SWITCH ON | Remove the comment marks once 19 and 20 are live |

Not marked on the page but still to do: save the official logo as `images/mrc-logo.png` (step 1), and the launch-day steps in step 5.
