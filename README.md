# Peros 40th: website setup

The website is `index.html`, with its settings in `config.js`.
RSVPs and photos go to **your own Google Sheet and Google Drive** through a small
Google Apps Script (`party-backend/Code.gs`). Guests don't need any account.

## 1. Connect the RSVP form and photo uploads (about 10 minutes)

1. Create a new Google Sheet, for example "Peros 40th RSVPs".
2. In the sheet, open **Extensions → Apps Script**.
3. Delete the sample code and paste in everything from `party-backend/Code.gs`. Save.
4. In the toolbar, pick the function **setup** and press **Run**. Google asks you to
   authorise the script: choose your account, then **Advanced → Go to project → Allow**.
   This creates the *RSVPs*, *Photos* and *Summary* tabs and a Drive folder called
   "Peros 40th - photo album".
5. Press **Deploy → New deployment**, choose type **Web app**, and set:
   - Execute as: **Me**
   - Who has access: **Anyone**
6. Press **Deploy** and copy the **Web app URL** (it ends in `/exec`).
7. Paste it into `config.js` as `endpoint: "https://script.google.com/macros/s/…/exec"`.

Optional: set `NOTIFY_EMAIL` at the top of `Code.gs` to get an email on each RSVP.
After any later change to `Code.gs`, use **Deploy → Manage deployments → Edit → New version**
so the same URL keeps working.

**Where to see responses:** the *Summary* tab shows the totals: families coming, adults,
kids, total people, who is staying 1 night, 2 nights or coming for dinner only, and how
many families and kids are interested in the Kita (half day, full day, maybe).
The *RSVPs* tab has one row per family. If a family replies again under the same name,
their row is updated rather than duplicated.
Photos land in the Drive folder, named after the person who shared them.

## 2. Put the website online with GitHub Pages

1. On GitHub, open the repository's **Settings → Pages**.
2. Under *Build and deployment*, choose **Deploy from a branch**, select **main** and
   **/ (root)**, and save.
3. After a minute or two the site is live at `https://esaygin.github.io/Peros40/`.

The page tells search engines not to index it.

## 3. Settings in `config.js`

- `style`: `"alpine"`, `"noir"` or `"porcelain"`.
- `showStylePicker`: set to `false` once you've chosen a style.
- `photoDeadline`: for example `"20 November 2026"`, so you have time to print the album.
- `contactPhone`: your number, if you want guests to message you.

Before sending the link, submit a test RSVP and a test photo, then delete the test row
and test file.
