# TCS Consignment Auto-Filler

> **Automates filling `Delivery Date` and `Received By` columns in your TCS Excel reports — in seconds.**

---

## 🚀 What It Does

If you manage TCS courier deliveries and maintain an Excel report, you know the pain of manually:
1. Copying each consignment number
2. Opening `tcsexpress.com/track/...` in the browser
3. Reading and typing back the delivery date and receiver name

**TCS Consignment Auto-Filler eliminates this entirely.** Just point it to your Excel file, pick the sheet, and hit **Start**. It fetches live tracking data directly from TCS and fills in the columns for you — automatically.

---

## 📋 Requirements

- Windows 10 or 11
- An Excel file (`.xlsx`) with a `Consg#` column containing valid TCS tracking numbers
- An active internet connection

> ✅ No Python installation required. The `.exe` is fully self-contained.

---

## 📥 Download

Download the latest release from the [Releases](../../releases) page:

```
tcs_auto_filler.exe
```

---

## 🖥️ How to Use

1. **Double-click** `tcs_auto_filler.exe` to launch the application.

2. **Select your Excel file** using the Browse button.

3. **Choose the sheet** you want to process (e.g., `July`) from the dropdown — it auto-populates from your file.

4. **Configure options:**
   - ✅ *Skip rows that already have Delivery Date filled* — avoids re-fetching data that's already there (recommended).
   - ✅ *Create a backup file before saving* — saves a timestamped copy of your file before any changes are written.

5. Click **Start Processing** and watch the progress in the live log window.

6. Once complete, open your Excel file — the `Delivery Date`, `Received By`, and `Status` columns will be filled in.

---

## 📊 Excel File Format

Your Excel sheet should contain the following columns (the tool auto-detects them by name):

| Column | Description |
|---|---|
| `Consg#` | TCS tracking / consignment number (e.g., `4171606318`) |
| `Delivery Date` | Will be auto-filled by this tool |
| `Received By` | Will be auto-filled by this tool |
| `Status` | Will be set to `DELIVERED`, `PENDING`, etc. |

> Rows where `Consg#` is `By Hand`, `0`, or blank are automatically skipped.

---

## ⚙️ Options Explained

| Option | Default | Description |
|---|---|---|
| Skip filled rows | ✅ On | Skips rows where `Delivery Date` is already populated |
| Backup before save | ✅ On | Creates a `_backup_<timestamp>.xlsx` copy before writing |

---

## 🔍 How It Works

The application communicates directly with TCS Express's backend tracking API — the same API used by [tcsexpress.com](https://www.tcsexpress.com). No browser automation or scraping is involved, making it fast, lightweight, and reliable.

For each valid tracking number it:
1. Sends a POST request to the TCS API bridge
2. Reads the delivery status, date/time, and receiver name
3. Writes the values back into the correct cells in your Excel sheet

---

## ❓ FAQ

**Q: Will this work with any TCS Excel report format?**  
A: Yes, as long as the sheet has a column named `Consg#` with valid TCS tracking numbers.

**Q: What if a consignment hasn't been delivered yet?**  
A: The tool will leave those cells blank or write the current status (e.g., `PENDING`).

**Q: Is my data sent anywhere?**  
A: No. The app only contacts the official TCS tracking endpoint (`tcsexpress.com`) to retrieve tracking info. No data is sent to any third party.

**Q: The app shows "No rows to process" — why?**  
A: This usually means all rows already have `Delivery Date` filled in and the *Skip filled rows* option is enabled. Uncheck that option to re-fetch all rows.

---

## 👤 Author

**ArsalanRiaz**  
© 2026 ArsalanRiaz. All rights reserved.

---

## ⚠️ Disclaimer

This tool interfaces with the publicly accessible TCS tracking endpoint for personal productivity use. It is not affiliated with or endorsed by TCS (TCS Express Logistics).
