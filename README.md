# GSTIN Checker

A Streamlit tool that validates a list of GSTINs in bulk and enriches them with taxpayer details, using the gstincheck.co.in API. Upload an Excel of GSTINs, enter your API key, download an enriched Excel.

## Features

- **Bulk validation** - reads GSTINs from an uploaded Excel file (column A, header `GSTIN` in A1).
- **Your own API key** - the key is entered in the app at runtime (password field), never hard-coded or stored.
- **Rich output** - for each GSTIN, fetches:
  - Status (active/cancelled etc.)
  - Legal Name and Trade Name
  - Constitution of business
  - Centre and State jurisdiction
  - Principal place of business
  - Registration date and cancellation date
  - Nature of business activities
  - State code and last-updated date
- **Styled Excel export** - downloads the enriched results as a formatted `.xlsx` (openpyxl styling).
- Graceful per-row handling of invalid GSTINs, API errors, and network failures - one bad row does not stop the run.

## Requirements

```bash
pip install -r requirements.txt
```

Dependencies: `streamlit`, `pandas`, `requests`, `openpyxl`.

You also need an API key from [gstincheck.co.in](https://sheet.gstincheck.co.in).

## Run

```bash
streamlit run GSTCheck.py
```

1. Enter your GSTIN Check API key.
2. Upload the Excel file with GSTINs in column A.
3. Review the results table and download the enriched Excel.

## Notes

- The app calls `http://sheet.gstincheck.co.in/check/<api_key>/<gstin>` once per GSTIN; a paid/exhausted key will return API errors per row.
- Version 2.0 (sidebar credits: AuditFlow Team).
- Private project.
