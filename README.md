# D365 Sales Demo Data Generator (GitHub Pages)

This repo hosts a **single‑page app** that packages a complete **Dynamics 365 Sales demo dataset** for quick import. It is intentionally streamlined to require only **two inputs** (Demo Type and Users) so you can generate a ZIP of CSVs in seconds and start demoing immediately.

---

## 🧩 What this demo deploys (full contents)

The exported ZIP contains a cohesive data pack representing **Contoso Coffee** (or your custom brand) with realistic sales activity over time. Files are CSVs designed for import into Dataverse/Dynamics 365 Sales. By default, the app reads the sample data from the repo’s `data/` folder and outputs the same structure in the ZIP, plus a generated `businessunit.csv`.

**Included datasets:**

- **businessunit.csv** *(generated)* – Minimal business unit record.  
  - Uses **Contoso Coffee** by default or the **Customer name** you enter when “Custom” is selected.
- **User.csv** – Demo users (sellers, system users).  
  - Can be replaced by your uploaded `users.csv` when “Custom users” is selected. Header validation is applied.
- **Territory.csv** – Sales territories to support assignment and segmentation.
- **Campaign.csv** – Marketing campaigns that act as sources for opportunities/leads.
- **Product.csv** – Product catalog (espresso machines, coffee, accessories, subscriptions) used by opportunities.
- **Account.csv** – Customer accounts (B2B) with varied industries and sizes.
- **Contact.csv** – Contacts tied to accounts (B2B personas) used in emails/appointments.
- **Opportunity.csv** – Opportunities across multiple sellers and time ranges, mixing open/won/lost states.  
  - Represents realistic pipeline and sales cycles with products and estimated revenue.
- **Emails.csv** – Email activities aligned to opportunity stage (fewer early, more for late-stage deals).
- **Appointments.csv** – Meetings/calls aligned to advancing opportunities (discovery, demo, technical review, close).

> The sample data emphasizes **realistic sales engagement** over multiple months/years with varied outcomes, product mixes, and activity volume—useful for showcasing Sales research/insights agents, pipeline analytics, and seller productivity scenarios.

---

## ✨ How the app works (two inputs only)

1) **Demo Type**: `Contoso Coffee` or `Custom`  
   - If `Custom`, enter a **Customer name**. The app generates `businessunit.csv` using that name; all other business config comes from the sample CSVs.

2) **Demo Users**: `Contoso Coffee` or `Custom`  
   - If `Custom`, upload a `users.csv` **with the same headers as the sample**. The app validates headers and replaces `User.csv` in the output package. All other datasets stay as defined by the sample files.

That’s it—no other configuration is required. Click **Prepare Demo Package**, then **Download CSV ZIP**.

---

## 📁 Repo layout

```
/ (repo root)
├─ index.html          # the single‑page app (loads data from /data/)
├─ README.md
└─ data/
   ├─ Territory.csv
   ├─ Appointments.csv
   ├─ Contact.csv
   ├─ Goal.csv
   ├─ Campaign.csv
   ├─ User.csv
   ├─ Product.csv
   ├─ Opportunity.csv
   ├─ Account.csv
   └─ Emails.csv
```

> **Paths matter.** Keep filenames **exact** (case‑sensitive). The app expects all CSVs under `data/`. The ZIP removes the `data/` prefix so the output files have clean names for import.

---

## 🚀 Publish on GitHub Pages

1. Commit `index.html` at repo root and all CSVs under `data/`.
2. In GitHub: **Settings → Pages**  
   - **Source**: *Deploy from a branch*  
   - **Branch**: `main` and **/(root)** folder
3. Open the Pages URL when it’s ready (e.g., `https://<user>.github.io/<repo>/`).

---

## ✅ Smoke test

1. Visit your Pages URL.  
2. Click **Prepare Demo Package** — you’ll see logs for each `data/*.csv`.  
3. Click **Download CSV ZIP** — confirm the ZIP downloads.  
4. Try both flows:  
   - **Contoso / Contoso** (no upload)  
   - **Custom / Custom** (enter Customer name + upload your `users.csv` with matching headers)

---

## 🔒 Import guidance (typical order)

While your environment and dependencies may vary, this order is commonly successful:

1. `businessunit.csv` *(generated)*  
2. `User.csv`  
3. `Territory.csv`  
4. `Campaign.csv`  
5. `Product.csv`  
6. `Account.csv`  
7. `Contact.csv`  
8. `Opportunity.csv`  
9. `Emails.csv`  
10. `Appointments.csv`

> Adjust as needed for your Dataverse solution dependencies, lookups, or customizations.

---

## 🔧 Notes & Troubleshooting

- **PapaParse/JSZip CDNs**: The page uses multi‑CDN fallbacks. If all CDNs are blocked, host `papaparse.min.js` and `jszip.min.js` locally and update the loader to local paths.  
- **Header validation for users**: If your uploaded `users.csv` is missing columns found in the sample `User.csv`, the app will log the missing headers.  
- **Cache**: Use a hard refresh (Ctrl/Cmd+Shift+R) if your browser caches CSVs.  
- **ASCII‑only**: Keep text ASCII if your import tooling is sensitive to encodings.  
- **Non‑routable emails**: Consider using non‑routable or sandbox domains for contacts to avoid accidental emails.

---

## 📜 License

MIT (or your preferred license).