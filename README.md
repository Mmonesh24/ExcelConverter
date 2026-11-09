# 📊 ExcelConverter — Options Chain Formatter & Analyzer

A high-performance, **100% client-side web application** that converts raw NSE Options Bhavcopy or Options Chain Excel (`.xlsx`, `.xls`) and CSV (`.csv`) files into the exact formatted **Sheet2** analysis structure matching `sent.xlsx`.

> 🚀 **Live Demo on GitHub Pages**: [https://mmonesh24.github.io/ExcelConverter/](https://mmonesh24.github.io/ExcelConverter/)

---

## ✨ Key Features

- **🌐 100% Client-Side & Secure**:
  - Runs entirely inside your browser using SheetJS.
  - Zero backend required. Your financial data never leaves your computer.
- **🔍 Smart Datatype & Filter Detection**:
  - **Date Columns (Timezone-Safe & Resilient)**:
    - ⚡ **Quick-Select Expiry Pills**: One-click pills displaying available expiry dates with row counts (e.g. `09/11/2026 (209 rows)`).
    - **Flexible Date Inputs**: Enter dates via the standard calendar picker or type directly (e.g. `9-11-2026` or `09/11/2026`).
    - **Date Range / Start / End**: Filter between any date range.
  - **Strike Price (`STR_PRICE`) Dedicated Filter**:
    - **Mid Value + Nearest Strikes**: Enter a Mid/Spot strike (e.g. `22330`) and a Range Count (e.g. `20`) to select the **20 nearest lower strikes** and **20 nearest higher strikes** around the mid value.
    - **Min/Max Bounds**: Optional custom numerical bounds.
  - **Text & Numbers**: Live multi-select search checklist, contains search, and numerical min/max.
- **📑 Custom Export Column Selection**:
  - Choose exactly which columns are exported to the final Excel `DATA` sheet and CSV.
  - Ensures essential option columns (`Identifier`, `STR_PRICE`, `OPT_TYPE`, `OPEN`, `HIGH`, `LOW`, `CLOSE`) are always validated.
- **📈 Formatted Sheet2 Output (Matches `sent.xlsx` Exactly)**:
  - **Live Excel Formulas**: Preserves formulas for `AVG`, `PREMIUM`, `VLOOKUP`, and radiating strike math (`ROUND(DATA!V4/DATA!Y5,0)*DATA!Y5`).
  - **ATM Yellow Highlight**: Highlights the reference At-The-Money (ATM) strike row in solid soft yellow (`#FEF3C7`) in both the browser preview and the exported `.xlsx`.
  - Radiates strikes outward symmetrically above and below ATM.

---

## 🚀 How to Deploy on GitHub Pages (Instant 1-Click Setup)

Since this repository contains the standalone frontend (`index.html` at the root), you can host it for free on GitHub Pages in under 1 minute:

1. Go to your repository on GitHub: [https://github.com/Mmonesh24/ExcelConverter](https://github.com/Mmonesh24/ExcelConverter)
2. Click on the **Settings** tab (gear icon at the top right).
3. In the left sidebar, click on **Pages** (under the "Code and automation" section).
4. Under **Build and deployment**:
   - **Source**: Select `Deploy from a branch`.
   - **Branch**: Select `main` (or `master`) and set the folder to `/ (root)`.
5. Click **Save**.
6. Wait ~30 seconds for GitHub to build the page.
7. Your app is now live at:
   👉 **`https://mmonesh24.github.io/ExcelConverter/`**

---

## 🖥️ Local Usage

Simply double-click `index.html` to open it in any modern browser (Chrome, Edge, Firefox, Safari, Brave). No web server, Node.js, or Python installation is required!

---

## 📋 Sheet2 Output Structure

| Column | Header | Description & Formula |
|:---:|:---:|---|
| **B** | *(none)* | `=CONCATENATE(G{row},"CE")` (e.g. `23300CE`) |
| **D** | `PREMIUM` | `=V{row}` (Call Premium) |
| **E** | `AVG` | `=(F{row}+H{row})/2` (Call Avg) |
| **F** | `CLOSE` | CE Close Price |
| **G** | `STRIKE` | **ATM**: `=ROUND(DATA!V4/DATA!Y5,0)*DATA!Y5`<br>**Above ATM**: `=G{row+1}-DATA!$Y$5`<br>**Below ATM**: `=G{row-1}+DATA!$Y$5` |
| **H** | `CLOSE` | PE Close Price |
| **I** | `AVG` | `=(F{row}+H{row})/2` (Put Avg) |
| **J** | `PREMIUM` | `=Z{row}` (Put Premium) |
| **R** | *(none)* | `=CONCATENATE(G{row},"PE")` (e.g. `23300PE`) |
| **T** | `call low` | CE Low Price |
| **U** | `put hig` | PE High Price |
| **V** | *(none)* | `=(T{row}+U{row})/2` |
| **X** | `put low` | PE Low Price |
| **Y** | `call hig` | CE High Price |
| **Z** | *(none)* | `=(X{row}+Y{row})/2` |

---

## 📄 License

MIT License. Free for personal and commercial use.
