# Inventory

An Android app for counting stock and managing inventory — built to replace spreadsheets, manual tallies, and guesswork with something faster and more reliable.

Everything runs on your device. There's no account, no server, and no internet connection required — your products, counts, and history stay on your phone.

## Download

Grab the latest APK here: **[Download Inventory](https://github.com/Safu1islam/inventory-app-releases/releases/latest)**

This link always points to the newest version. Check back here (or use **Check for Updates** inside the app) whenever a new release ships.

### Installing the APK

Since the app isn't distributed through the Play Store, Android will walk you through a couple of one-time security steps the first time you install it:

1. Download the APK using the link above (usually opens in your browser).
2. Tap the downloaded file to open it.
3. If prompted **"Install unknown apps"**, allow it for your browser — this is a one-time permission per app.
4. If Google Play Protect scans the file and shows a warning because the app has few installs, choose **Install anyway** (or "More details" → "Install anyway"). This is standard for any app installed outside the Play Store, not specific to this app.
5. Tap **Install**, then open the app.

Updating later works the same way, and your data is preserved automatically as long as you install over the existing app rather than uninstalling first.

## What it does

- **Scan to count** — use your camera to scan barcodes and count stock instantly, fully offline.
- **Import existing files** — bring in inventory or count sheets from Excel (`.xlsx`) or CSV, including inconsistent or messy spreadsheets exported from other vendor systems.
- **Inventory hub** — organize products by vendor/list, with quick actions for physical counts, sales, deliveries, returns/removals, and transfers.
- **Stock counting** — count against a saved list or an external count sheet, see expected-vs-counted differences, and resolve discrepancies with a clear trail.
- **Product search & scanning** — look up any product by barcode, SKU, or name across your whole catalogue, including related matches when a code is shared across variants.
- **Reports & export** — export inventory or count results as Excel or CSV, with the option to choose exactly which columns to include.
- **Backup & restore** — save or replace your entire local database, so you can move your data between devices or recover from a wipe.
- **Locations** — track which location each product's stock belongs to, and filter or count by location.
- **Activity history** — a full log of stock movements (sales, deliveries, returns, transfers, adjustments) for every list.

📖 **[Read the full User Manual](USER_MANUAL.md)** for a complete, screen-by-screen walkthrough of every feature, menu, and gesture in the app — including a full troubleshooting/FAQ section covering every error message you might see. It's detailed enough to answer nearly any "how do I…" question, so feel free to search it, skim it, or paste it into an AI assistant and ask it to walk you through a specific task.

## Getting started

1. **Open the app.** The Dashboard shows your product count, total units, and any low/out-of-stock items at a glance.
2. **Bring in your first products**, either way works:
   - Tap **Import Products** on the Inventory screen and choose an Excel or CSV file, or
   - Go to **Inventory → Import Count Sheet** to bring in a list as a vendor inventory you can count against later.
3. **Do a count.**
   - From **Stock Count**, start a new session against a saved list, or import an external count sheet on the spot (with or without existing quantities).
   - Scan items with the camera, or search and enter counts manually.
   - When you finish, review the differences between expected and counted quantities before saving.
4. **Manage day-to-day stock** from the **Inventory** tab: record sales, deliveries, returns/removals, and transfers per vendor list, and view the activity log any time.
5. **Export when you need to** — from a count session or the Inventory screen, choose Excel or CSV, and pick which columns to include.
6. **Back up your data** occasionally from **More → Backup & Restore**, especially before switching devices.

## Importing spreadsheets

The importer is built to tolerate real-world files, not just a clean template:

- Works with a `SKU` / `VENDOR SKU` / `COUNT` template, or a looser layout as long as it has a quantity column and at least one identifier (SKU, barcode, or name).
- Understands raw exports from other vendor systems directly — including files with no `COUNT` column, blank vendor SKUs, or vendor/total summary rows mixed into the sheet.
- If a file doesn't match a known layout automatically, you'll get a column-mapping screen to tell the app which column is which.
- Accepts both `.xlsx` and `.csv`.

## Frequently asked questions

**Do I need an internet connection?**
No. Everything — scanning, counting, importing, exporting — works fully offline. The only time the app goes online is to check for a newer version, and that's optional.

**Will I lose my data when I update?**
No, as long as you install the new APK over the existing app (rather than uninstalling first). Your products, counts, and history are stored locally and are preserved across updates.

**Android says the app is unsafe or unrecognized. Is it safe to install?**
That warning (from Google Play Protect) appears for any app installed outside the Play Store with a low install count — it isn't specific to this app. See the SHA-256 checksum listed on each [release](https://github.com/Safu1islam/inventory-app-releases/releases) if you'd like to verify the file you downloaded matches what was published.

**Why isn't the source code here?**
This repository is intentionally APK-only, so it can be linked to directly from the app's update checker and downloaded without needing sign-in. It doesn't include the app's source.

## Feedback

Found a bug or have a feature request? Open an issue on this repository, or reach out directly — this app is under active development and real feedback shapes what gets built next.
