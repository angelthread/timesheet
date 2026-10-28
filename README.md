# Timesheet

A time tracker in one HTML file. Log hours by date, item and description, and mark time as "Not charged". Entries are grouped into Monday–Sunday weeks, with daily totals and a weekly summary. Each week's remaining budget carries into the next week as its starting budget.

There's no server and no database. Your data is saved as a JSON file in a GitHub repository you choose, and every save is a commit.

## Use it

Open the GitHub Pages site for this repo, or open `index.html` directly in a browser.

### Turn on GitHub Pages (once)

1. In this repo go to **Settings → Pages**.
2. Under **Build and deployment** choose **Deploy from a branch**, branch `main`, folder `/ (root)`, and save.
3. After a minute the site is live at `https://<your-username>.github.io/timesheet/`.

### Connect your data (once per browser or device)

GitHub Pages needs this repo to be public on a free plan, so keep your data in a **separate private repo**:

1. Create a private repo, e.g. `timesheet-data`. Tick "Add a README" so it has a `main` branch.
2. Create a [fine-grained personal access token](https://github.com/settings/personal-access-tokens/new):
   - Repository access: **Only select repositories** → `timesheet-data`
   - Permissions: **Contents → Read and write**
3. In the app, click **Connect GitHub**, enter your username, `timesheet-data` and the token, then click **Connect and load**.

The app creates `data/timesheet.json` on the first save. After that, changes upload about a second after you make them. The token is stored only in that browser's local storage and is only sent to `api.github.com`. Click **Disconnect** to remove it.

If you edit on two devices at once, the app notices the file changed and asks which version to keep.

## How the budget works

- **Remaining budget** = starting budget − charged hours that week. "Not charged" hours don't count.
- A week's starting budget is the previous week's remaining budget. Type a different number in any week to override it (for example, a top-up). Later weeks carry on from there.

## Downloads

- **Download all (JSON)**: everything, plus computed weekly summaries. You can load it back with **Import JSON**.
- **Entries CSV** and **Weekly summary CSV**: for Excel or Google Sheets.

Since the data file lives in Git, you can also see the full history in the data repo's commit log.
