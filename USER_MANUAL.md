# Inventory — User Manual

Inventory is an offline stock-management and physical-counting app for Android. Everything — products, vendor lists, counts, transfers, and history — is stored in a local database on your device. There is no account to create, no server, and no internet connection required for any core feature; the only feature that ever reaches the internet is the optional "Check for Updates" button. Because everything lives on your device, the app is only as safe as your phone: use **Backup & Restore** regularly, and never uninstall the app without restoring a backup first, since uninstalling deletes the database permanently.

---

## 1. Getting Around

The app has four tabs at the bottom of the screen:

- **Home** — the Dashboard: totals, low-stock alerts, and recent activity.
- **Inventory** — your standalone product catalog and your Vendor Inventory lists; also where you import and export.
- **Scan** — opens the camera to look up a product by barcode.
- **More** — everything else: Stock Count workflows, Report Templates, Inventory History, Locations, Backup & Restore, and Storage/About/Update info.

The Scan tab's camera only runs while that tab is on screen — switching tabs turns it off, so it isn't draining your battery in the background.

---

## 2. Dashboard (Home tab)

The Dashboard is a read-only summary screen:

- Four stat tiles: **Products** (how many distinct products), **Total Units**, **Low Stock**, and **Out of Stock**.
- A **Stock Count** shortcut card that jumps straight into the Stock Count module.
- **Recent Activity** — the last few stock transactions, with a **View all** link to the full Inventory History.
- **Low Stock Items** — up to 10 products at or below their minimum stock level; tap any one to open its Product Detail screen.

Pull down on the screen to refresh the numbers.

---

## 3. Inventory (standalone catalog & Vendor Lists)

The Inventory tab has two sections stacked on one screen:

### 3.1 Vendor Inventory (your imported lists)

At the top, a horizontally-scrolling row of cards, one per imported vendor list. Tap a card to open that list. Each card also has a **⋮** (three-dot) menu with:

- **Start Physical Count** — begin counting this list.
- **Record Sale** / **Record Delivery** — opens a search screen to pick an item and log a quantity change.
- **Record Return / Removal** — for damaged, expired, or otherwise reduced stock.
- **Record Transfer** — move quantity from one location to another.
- **Import Sales Report** / **Import Delivery Report** — bulk-apply a spreadsheet of sales or deliveries instead of entering them one at a time.
- **View Activity** — this list's full change log.

### 3.2 Products (your standalone catalog)

Below the vendor lists is your own product catalog — items you created directly or copied in (not tied to any vendor list). Each product card shows its name, any extra columns you've chosen to display, and its current quantity. Tap a product to open its Product Detail screen.

Tap the small **chevron (⌄)** on the right of a product card to expand a per-location stock breakdown in place, without leaving the list — useful for checking where units actually are before deciding to transfer or count them.

### 3.3 Top toolbar (Inventory screen)

- **Import products** (upload icon) — bulk-import a spreadsheet of products straight into the standalone catalog.
- **Import vendor list / count sheet** (checklist icon) — bring in a new Vendor Inventory list.
- **Export inventory** (share icon) — export your current product list as Excel or CSV, choosing which columns to include (see §7 below).
- **Customize inventory** (columns icon) — choose which columns appear on each product card (Product, Size, Quantity, Location, Barcode, SKU, Vendor, Cost, Price). At least one column must stay selected.
- **+** floating button — create a new standalone product from scratch.

### 3.4 Search, filters, and locations

- A search box filters both products and (indirectly) what you see on screen by name, SKU, or vendor SKU.
- Filter chips: **All**, **In Stock**, **Low Stock**, **Out of Stock**.
- If you've created any Locations, a second row of chips lets you filter the whole screen down to one physical location (or "All Locations"). When a location is selected, each product's quantity shown is that location's stock, not the total.

---

## 4. Products — creating, editing, and stock actions

### 4.1 Creating or editing a product

Open the **+** button on Inventory, or tap the pencil icon on a Product Detail screen to edit.

Required: **Product Name**, and at least one of **Barcode** or **Product Code (SKU)** (a validation message appears if both are blank). Everything else — Category, Unit, Minimum Stock Level, Opening Stock, Cost Price, Selling Price — is optional.

- **Category** and **Unit** are "quick-add" dropdowns: pick an existing value, or choose **Add New…** at the bottom of the list to type a brand-new one on the spot without leaving the form.
- The barcode field has a small camera icon that opens a quick scanner just to fill in that field.
- Duplicate barcodes are blocked: if you try to save a barcode already used by another product (or another size/variant), you'll see "A product with this barcode already exists."

### 4.2 Sizes / variants

A product can optionally be split into **Sizes**, each tracked with its own barcode and stock count (e.g. a shirt in S/M/L). On the product form:

- Tap a size chip to add it, or **Add Size** to create a brand-new size name.
- Each added size gets its own row where you can type a barcode and (for a brand-new product) an opening stock quantity.
- On an already-saved product, tapping the barcode icon on a size row lets you set/change/clear that size's barcode; tapping **×** removes the size (its history is kept, it just stops appearing).
- A size's barcode is checked for duplicates the same way a product's own barcode is.

### 4.3 Receiving, removing, and adjusting stock

On a Product Detail screen (or a size's row within it), three actions open a bottom sheet with a big +/- stepper:

- **Receive Stock** — adds quantity (logged as a supplier delivery).
- **Remove Stock** — subtracts quantity; pick a reason from **Sale**, **Damaged**, **Expired**, **Internal Use**, or **Other**.
- **Adjust Stock** — sets the exact quantity to match a physical count, rather than adding/subtracting (logged as "Physical inventory count").

Each sheet lets you also pick which **Location** the change applies to, if you've set any up. The stepper's number field can be typed into directly, not just tapped with +/-.

After saving, a confirmation dialog appears with **Scan Another** (returns you to wherever you came from) or **View Product** (stays here).

---

## 5. Scanning & manual code entry

### 5.1 Scan tab (standalone lookup)

Tap **Scan** to open the camera. Point it at a barcode; on a successful read the app looks it up:

- If it matches something in your standalone catalog or a vendor list, you're taken to the matching Product Detail (or, if there are multiple related matches, a **Scan Result** list to choose from).
- If nothing matches, you land on a **Product Not Found** screen offering **Create Product** (pre-fills the scanned code as the barcode) or **Scan Again**.

**Hidden gesture — double-tap to type it in:** if a barcode won't scan (torn label, glare, damaged sticker), **double-tap anywhere on the camera preview**. This opens an **Enter Barcode** dialog where you can type the number printed under the barcode instead. A small hint — "Won't scan? Double-tap to type it" — is shown at the bottom of the camera screen as a reminder.

### 5.2 Scan to Count (inside a counting session)

Within an active count session, tapping **Scan to Count** opens a similar continuous-scan camera loop, but tuned for counting:

- Every successful scan immediately opens the count-entry sheet for that item (see §6.3), and the camera restarts automatically afterward — no need to back out and re-enter between items.
- If a scan matches more than one item, a **Multiple Items Found** picker appears so you choose the right one.
- If a scan matches nothing in the list, a red banner appears at the bottom: "Vendor SKU not found in this count sheet," along with the scanned code and an **Add as New Item** button that opens the Add Item form pre-filled with that code, then immediately pulls the new item into the running session so you can count it right away.
- **Same double-tap gesture applies here**: double-tap the camera preview to open an **Enter Vendor SKU** dialog for typing a code that won't scan. A reminder — "Barcode won't scan? Double-tap to type it" — sits at the top of this screen.

---

## 6. Stock Count workflow

Reached from **More → Stock Count**, or the Stock Count card on the Dashboard.

### 6.1 Stock Count home

- **Start Count** (floating button) — walks you through: pick a saved list (or import a new one, or create a blank one) → optionally pick a Location → begin (or resume) a counting session.
- **Saved Lists** — your existing Vendor Inventory lists; tap one to open it.
- **Recent Sessions** — every counting session you've started, showing Completed/In progress status. Each session has a **⋮** menu with **Delete Session** (removes the session and its counts only — any quantities already applied back to the list are unaffected, and the Activity Log is untouched).
- Top-right **⋮** menu: **Import Count Sheet**, **Add Item Manually** (pick which list first, if you have more than one), **Download Templates** (blank Excel templates for Count Sheet, Sales Report, or Delivery Report), and **Activity Log (All Lists)**.

### 6.2 Selecting a location before counting

Before a count starts, you're asked to pick a physical location — tap an existing one, tap **Add Location** to create one on the fly, or tap **Skip — goes to Unassigned**. This step never blocks you from counting; Skip is always a valid choice.

If a count is already in progress for that exact list+location combination, you're asked to **Resume** it or **Start New Cycle** (a genuine separate re-count) instead of silently duplicating or losing the old one.

### 6.3 Counting a session

Inside a session (`Count Session` screen):

- A progress bar and text show how many required items have been counted, plus counts of any auto-resolved zero-quantity items and any exceptions.
- Filter chips: **Pending**, **Exceptions**, **Completed**, **All**.
- Tap any item card to open its count-entry sheet directly (instead of scanning).
- **Scan to Count** (floating button) opens the camera loop described in §5.2.
- Items whose expected on-hand quantity is zero or less are automatically treated as "Zero — Not Required" and don't block completion — you don't have to count something that was never expected to have stock.
- If what you actually count doesn't match what was expected (including counting a nonzero amount against an item expected to be at zero), the item is flagged as an **Exception** rather than silently marked done — you're warned about this in the count-entry sheet itself ("This differs from the expected quantity — saving will flag it as an exception.").

Top-right **⋮** menu on a session:

- **Export Excel** / **Export CSV** — write your counted quantities back into a copy of the original imported file (only the COUNT column is touched; everything else in the file — formatting, other columns, header rows — is preserved exactly). If items are still pending, you're warned and can choose **Export Anyway** (their COUNT is left as it was in the source file). If any manually-added items (ones with no row in the original file) were counted, you're told how many were skipped from the export file — they're still recorded in the Activity Log.
- **Mark Complete** — marks the session finished (you can still export/review afterward), then immediately offers to **Apply Counts to List**.
- **Apply Counts to List** — writes your counted quantities back into the list's on-hand quantities, so future deliveries/sales/counts start from the corrected numbers. Pending items are left untouched. This is reachable at any time, not just right after marking complete, so declining it once is never a dead end.
- After applying counts, you're offered **Add Counted Items to Inventory** — a shortcut into the Copy-to-Inventory screen (§6.5), pre-selecting whichever items you actually counted.

### 6.4 List Detail screen (one Vendor Inventory list)

Opened by tapping a list from Inventory or Stock Count home. Shows every item in the list with its current quantity. Tapping an item opens a bottom-sheet menu of item-level actions: **Record Sale**, **Record Delivery**, **Remove Stock (Damaged / Expired / Other)**, **Transfer Between Locations**, **Edit Product** (name & price only), and **Delete Item** (removes it from the list; the Activity Log is unaffected).

If the list has counting history at more than one location, chips above the item list show each location's progress (e.g. "Warehouse 8/20") — tapping one re-enters that location's count.

The **⋮** menu on this screen holds everything else: **Add Item Manually**, **Record Sale/Delivery/Return/Transfer** (search-first, without an item pre-picked), **Import Sales/Delivery Report**, **Download Templates**, **Add to Inventory**, **View Activity**, and **Rename List**.

**Start Count From Here** (floating button) is disabled until the list has at least one item.

### 6.5 Add to Inventory (copying counted items into the standalone catalog)

A checklist of the list's items (all pre-checked by default, or just the ones you counted if reached from "Apply Counts"). **Select All / Deselect All** toggles everything at once. This only ever copies — the source list and its quantities are left completely unchanged; it creates brand-new standalone products. Any item whose SKU or barcode already matches an existing standalone product is skipped as a likely duplicate, and you're told exactly which ones and how many were skipped.

### 6.6 Adding items manually

The **Add Item Manually** form only strictly requires **Vendor SKU / Code** (whatever will be scanned or typed to find this item). Description, SKU, Class, Sub-Class, Starting Quantity, Price, and Comments are all optional.

---

## 7. Importing files

There are three different import flows in the app, each tuned to a different job:

### 7.1 Import Products (into the standalone Inventory catalog)

**Inventory tab → upload-file icon.** Choose an `.xlsx` or `.csv` file. Any of Product, SKU, Barcode, Quantity, Class, Price, or Location columns you have will be auto-detected; you confirm the mapping before anything imports (see §7.4). Once confirmed and clean, tap **Import to Inventory**. You're told how many products were added, and how many were skipped as likely duplicates (matching an existing SKU or barcode), with the duplicate items named.

### 7.2 Import Count Sheet / Vendor List

**Inventory tab → checklist icon**, or from Stock Count. This is the most format-flexible import in the app, built to read a vendor's own export as-is, without you having to reformat anything first.

**The exact template** (what **Download Excel Template** gives you) has one header row with:
- **SKU**
- **VENDOR SKU** — required; this is what gets scanned or typed during counting
- **COUNT** — where your counted quantities get written back on export
- Optional: DESCRIPTION, CLASS, SUB-CLASS, ON HAND, PRICE, COMMENTS, LOCATION

Rows above the header can carry `LOCATION:`, `NAME:`, `CYCLE:`, `NOTE:` labels in the first two columns to pre-fill the list's name/cycle/notes automatically.

**If a file doesn't match that template exactly**, the app automatically falls back to flexible column detection (the same system used for product import) and shows you a **Confirm Column Mapping** screen (§7.4) instead of rejecting the file. A `.csv` file always goes through this flexible step, since CSV has no fixed template of its own.

**Validation, before anything is saved:**
- Every row needs some identifier — the app tries Vendor SKU, then SKU, then Description, in that order, and uses whichever is present first.
- A row with none of those is reported as an error ("Missing SKU / Vendor SKU" for the exact template, or "No SKU, Barcode, or Product name on this row — cannot identify it." for a flexibly-mapped file) and nothing is imported until you fix it.
- If the same identifier repeats across rows, the app doesn't silently overwrite or merge them — it appends "(row N)" to make the later ones unique, so every row still gets imported and stays individually countable.
- Rows that look like a spreadsheet's own subtotal or "Total:"/"Value:" summary line (rather than an actual product) are automatically skipped rather than reported as broken rows.
- If a Location column is present, it's applied automatically per row; without one, everything imports into **Unassigned**.

**After a clean parse**, choose **New List** (name it) or **Update Existing** (pick which saved list to refresh), and optionally leave **Start counting immediately after saving** checked to jump straight into location-selection and a new session.

### 7.3 Import Sales/Delivery Report (applying bulk transactions to an existing list)

From a list's **⋮** menu → **Import Sales Report** / **Import Delivery Report**. This uses the app's own downloadable template (not a foreign vendor format) — download it from the same screen if you need a blank one. Each row needs a quantity and at least one identifier (Vendor SKU, SKU, Barcode, or Item Name — whichever the report has). Rows are matched against the list's existing items by Vendor SKU → SKU → Barcode → Name, in that order. If everything resolves cleanly, you see a preview of exactly what will change (with row numbers and any reference/invoice numbers) before tapping **Apply Sale**/**Apply Delivery**. If a file parses but matches nothing in the list, you're told so rather than silently applying zero changes. Any row-level problem is reported with its row number before anything is applied — nothing is guessed or partially applied.

### 7.4 Confirm Column Mapping (the shared fallback screen)

Whenever a file's headers don't exactly match a fixed template, this screen shows every field the app recognizes (SKU, Barcode, Product, Quantity, Location, Class, Sub-Class, Price, Comments) as a dropdown pre-filled with its best guess, next to every actual column header found in your file. You only need to fix whatever looks wrong; leaving a field as **— None —** simply excludes it from the import. **Quantity is always required**, plus at least one of SKU, Barcode, or Product — the screen tells you exactly which of those is still missing if the **Confirm & Continue** button is greyed out.

If you've previously saved a mapping as a template (checkbox at the bottom: **Save this mapping as a reusable template**), it appears as a quick-apply chip at the top of this screen next time, so a recurring vendor format only needs to be mapped once.

---

## 8. Exporting

- **Inventory tab → share icon**: pick **Excel** or **CSV**, then check which columns to include (Product, Size, Quantity, Location, Barcode, SKU, Vendor, Cost, Price). At least one column must be selected before **Export** is enabled. The resulting file is handed to your device's normal share sheet (email, Drive, Bluetooth, etc.) — the app doesn't send it anywhere itself.
- **A count session's ⋮ menu → Export Excel/CSV**: writes your counted quantities into a copy of the exact file you imported, as described in §6.3.
- **Activity Log → Export**: exports whatever rows are currently on screen (filtered or not) to Excel.
- **Report Builder** (below) has its own, more flexible export with custom columns and row selection.

---

## 9. Sales, Deliveries, Returns/Removals, and Transfers

These are the four ways stock quantity changes on a Vendor Inventory list item (beyond counting):

- **Record Sale** / **Record Delivery** — a stepper for quantity, an optional **Location**, and an optional **Reference** (invoice/order number). Recording a sale larger than what's on hand is blocked with an error rather than allowed to go negative silently.
- **Record Return / Removal** — quantity plus a reason chip (**Damaged**, **Expired**, **Internal Use**, **Other**) and optional Location.
- **Record Transfer** — pick a **From Location** and **To Location** (the From list shows each location's current on-hand quantity so you can see where stock actually is), then a quantity. The app defaults "From" to whichever location currently holds the most of that item. Source and destination must be different, and the quantity can't exceed what's on hand at the source.

Each of these is reachable two ways: tap an item directly (its own bottom-sheet menu), or use the list's **⋮ → Record …** menu item, which opens a search screen first so you can find the item by name, vendor SKU, or SKU before picking the action.

---

## 10. Locations

**More → Locations.** Add, rename, deactivate, or reactivate physical locations (e.g. "Warehouse," "Front Counter"). The built-in **Unassigned** location is permanent and can't be renamed or removed — it's where stock lands when no location was specified. Deactivating a location hides it from every location picker in the app but keeps its stock and history exactly as they were; reactivating brings it back at any time.

---

## 11. Backup & Restore

**More → Backup & Restore.**

- **Create Backup** saves your entire database — every product, list, count, history entry, and the original imported spreadsheet files — as one file, then hands it to your device's share sheet so you can save it wherever you like (cloud drive, email to yourself, etc.). A ZIP backup includes both the data and your saved count-sheet templates; older database-only backup files are still accepted for restore.
- **Restore Backup** picks a `.zip` or `.db` file. You're warned explicitly: restoring **replaces every product, list, count, history entry, and saved template currently on the device** — the backup is validated first, and only replaces your data if it checks out. This is the one truly destructive action in the whole app, so only restore a backup you're certain about.

Because this app has no cloud sync, a backup taken before uninstalling or switching phones is the only way to carry your data forward.

---

## 12. Inventory History & Activity Log

Two separate logs exist, covering different things:

- **Inventory History** (More → Inventory History, or the history icon on a Product Detail screen) — every stock transaction on standalone catalog products: type, date, previous/new quantity, and reason/reference if given. Tap any row for full detail.
- **Activity Log** (a Vendor list's ⋮ → View Activity, or Stock Count home's ⋮ → Activity Log (All Lists)) — every change to a Vendor Inventory list's items: added, delivered, sold, removed, deleted, adjusted, or counted (scanned or typed). Filterable by type, and exportable to Excel.

---

## 13. Reports & Report Templates

**More → Report Templates.** This is a general-purpose report builder separate from the simple Inventory-tab export.

- **Recently Used** and **All Templates** (filterable by type: Inventory, Delivery, Sales, Reconciliation, Count Sheet) — each saved template card offers **Edit**, **Duplicate**, and **Delete**.
- **+** (top-right) opens the **Report Builder** to create a new one.
- A separate **Saved Import Mappings** section at the bottom lists any column mappings you chose to save while confirming an import (§7.4) — each can be deleted individually.

### Report Builder

1. Name the report and choose its **Report Type** (Inventory, Delivery, Sales, Reconciliation, Count Sheet).
2. For Inventory/Count Sheet reports, choose **Location Handling**: **Combined** (all locations together), **Split by location** (one breakdown per location), or **Single location** (pick one).
3. Check which columns to include; a **Selected Columns** list below lets you drag to reorder them.
4. Toggle **Include Headers** and **Include Summary**.
5. Choose an **Export Format**: CSV, Excel, or PDF.
6. **Preview** generates a live table of the report's rows. Each row has its own checkbox (plus a "select all" checkbox in the header) so you can exclude specific rows before exporting — **Select all** / **Select none** shortcuts are provided.
7. **Export** requires a generated preview and at least one selected row.
8. **Save** stores the report as a reusable template — a name and at least one selected column are both required.

---

## 14. Settings & About (More tab)

- **Storage** — shows how many products are stored on this device.
- **Check for Updates** — shows the currently installed version; tapping it checks whether a newer build has been published. Because this app is distributed as a plain APK rather than through an app store, this is the only built-in way to learn a new version exists. If one is found, a dialog shows the version and release notes, states plainly that **your products, counts, and history stay on this device and installing the update keeps everything exactly as it is**, and offers **Download** (opens the file in your browser — open the downloaded file afterward to install it) or **Later**.
- **About** — a short reminder that this is a standalone app: no account, no server, no internet connection required.

---

## 15. Troubleshooting / FAQ

**"Could not read any columns from … — is this a valid file?"**
The app couldn't open the file at all as a spreadsheet. Confirm the file is really `.xlsx` or `.csv` and isn't corrupted or password-protected.

**"Could not find a header row containing SKU, VENDOR SKU, and COUNT columns."**
Shown only when importing a Count Sheet that doesn't match the exact downloadable template. This isn't fatal — the app automatically retries with flexible column detection and, if that finds anything usable, takes you to the Confirm Column Mapping screen instead of stopping here.

**"X issue(s) found in [file] — nothing has been imported."**
Something in the file couldn't be resolved automatically — most often a row missing every identifier (no Vendor SKU, SKU, Barcode, or Name), or an unreadable header row. Every issue lists its row number and a plain description. Nothing is ever partially imported: fix the source file and re-import, or choose **Choose a Different File**.

**"Missing SKU / Vendor SKU." / "No SKU, Barcode, or Product name on this row — cannot identify it."**
A specific row in your file has nothing the app can use to identify that item. Add a value to at least one identifying column for that row.

**A row got renamed with "(row N)" appended.**
Two or more rows in your file shared the exact same identifier (SKU/Vendor SKU/Barcode/Name). Rather than merge them into one item or drop the duplicate, the app keeps every row by making the later ones unique this way, so nothing silently disappears from your count.

**"A product with this barcode already exists." / "That barcode is already used by another product/size."**
You're trying to save a barcode already assigned elsewhere (on another product, or another size of a product). Barcodes must be unique across the whole catalog.

**"X item(s) added, Y skipped as likely duplicates (SKU or barcode already exists in Inventory): …"**
Shown after Import Products or Add to Inventory. Any incoming item whose SKU or barcode already matches an existing standalone product is skipped rather than creating a duplicate — the message names exactly which ones.

**"No matching rows" after importing a Sales/Delivery Report.**
The file parsed without errors, but none of its rows matched any item currently in the list (by Vendor SKU, SKU, Barcode, or Name). Double-check you picked the correct list, or that the report actually corresponds to it.

**Recording a sale/removal/transfer is blocked with a quantity error.**
The app won't let a Sale, Removal, or Transfer take an item's on-hand quantity below zero at the relevant location — you'll see an on-screen error naming the shortfall. Use **Adjust Stock** or a physical count instead if you need to correct on-hand numbers directly.

**An item shows as an "Exception" during a count.**
The physical count you entered doesn't match the system's expected on-hand quantity for that item (including counting anything above zero for an item that wasn't expected to have any stock at all). This is not an error — it's flagged so you can review it later; you can still save the count and move on.

**"Count already in progress" dialog.**
You tried to start a count for a list/location combination that already has an unfinished session. Choose **Resume** to continue where you left off, or **Start New Cycle** to begin a genuinely separate re-count alongside it.

**Deleting a session vs. deleting a list item vs. deactivating a location.**
These are all deliberately non-destructive to your broader history: deleting a count session only removes that session and its counted values (quantities already applied to the list, and the Activity Log, are untouched); deleting a list item removes it from that list only (Activity Log unaffected); deactivating a location just hides it from pickers (its stock and history are kept, and reactivating restores it fully).

**Restoring a backup did nothing visible, or the app looks unusually empty afterward.**
Restore is total and destructive: it fully replaces every product, list, count, and history entry with whatever was in the backup file. If a restore appears to have "lost" data, it's most likely because the wrong backup file was chosen. There is no way to recover pre-restore data unless you have another backup of it — always keep more than one backup file if this matters to you.

**Update check says "Update checking has not been set up for this build yet."**
This specific build of the app wasn't configured with a location to check for updates. This is a one-time setup detail; if you built or received the app another way, this message is expected and can be ignored.

**The camera won't recognize a barcode.**
Both main scanning screens — the Scan tab and Scan to Count (inside a count session) — support the same fallback: **double-tap the camera preview** to type the code by hand instead of scanning it. Look for the "Double-tap to type it" hint text on screen. (The small quick-scan camera used to fill in a barcode field on the product form is a simpler scan-only screen without this fallback — if a barcode won't scan there, back out and type the number directly into the Barcode field instead.)
