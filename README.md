# 🇮🇪 Ireland Visa Decision Checker — Abuja

A Streamlit web app that lets applicants instantly look up their Irish visa decision by application number, using live weekly PDF reports published by the Irish Embassy in Abuja, Nigeria.

---

## What it does

- Scrapes the [Ireland Embassy Abuja](https://www.ireland.ie/en/nigeria/abuja/services/visas/weekly-decision-reports/) page for all weekly decision PDF reports
- Downloads and parses each PDF automatically, combining them into one searchable dataset
- Displays total, approved, and refused counts across all weekly reports
- Lets users search by application number in any format (`79001082`, `IRL79001082`, `irl79001082`)
- Input validation: exactly 8 digits, optional IRL prefix only, no special characters
- If no result is found, shows the nearest application numbers (before and after) with decisions and difference
- Provides a full CSV download of all combined decisions
- Data refreshes every hour via Streamlit cache

---

## Running locally

**Prerequisites:** Python 3.11+

```bash
# 1. Navigate to the project folder
cd "abuja irish visa"

# 2. Install dependencies
pip install -r requirements.txt

# 3. Run the app
streamlit run app.py
```

The app will open at `http://localhost:8501`.

---

## Project structure

```
abuja irish visa/
├── app.py            # Main Streamlit application
├── requirements.txt  # Python dependencies
├── render.yaml       # Render deployment config
└── README.md         # This file
```

---

## Dependencies

| Package | Purpose |
|---|---|
| `streamlit` | Web app framework |
| `requests` | HTTP requests to embassy website |
| `beautifulsoup4` | Parse HTML to find PDF links |
| `pandas` | Data processing |
| `pdfplumber` | Extract tables from PDF decision reports |

---

## Deploying

### Render
1. Push this repo to GitHub
2. Go to [render.com](https://render.com) → **New → Web Service**
3. Connect your GitHub repo — Render auto-detects `render.yaml`
4. Click **Deploy**

### Hugging Face Spaces
1. Create a new Space with **Streamlit** SDK
2. Upload `app.py` and `requirements.txt`
3. The Space builds and launches automatically

---

## Data source

All visa decision data is published by the Irish Embassy Abuja at:  
https://www.ireland.ie/en/nigeria/abuja/services/visas/weekly-decision-reports/
