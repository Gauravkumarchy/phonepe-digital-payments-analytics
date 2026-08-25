# PhonePe Digital Payments Analytics

Simple, clear README to get this repository running and explain the expected structure.

## Project overview

This repository contains code to analyze PhonePe digital payments data exported as an Excel (.xlsx) file. The included script(s) are small, easy-to-follow examples that load the raw Excel file, produce a few summary outputs, and save a processed CSV.

## Before you run anything

At the top of `analysis/run_analysis.py` set the path to your raw .xlsx file by replacing the placeholder value of `RAW_XLSX_PATH` with the full path (absolute or relative) to your file. Example:

```python
RAW_XLSX_PATH = "/path/to/your/raw_data.xlsx"
```

This single change is required so the analysis scripts can find and load your Excel file.

## Quick start

1. Install Python 3.8+ and create a virtual environment (recommended):

```bash
python -m venv venv
source venv/bin/activate  # macOS/Linux
venv\Scripts\activate     # Windows
```

2. Install dependencies:

```bash
pip install -r requirements.txt
```

3. Edit `analysis/run_analysis.py` and set `RAW_XLSX_PATH` as instructed above.

4. Run the analysis:

```bash
python analysis/run_analysis.py
```

The script will print basic summaries to the console and write a processed CSV to `data/processed.csv`.

## Project structure

- README.md                  - This file
- requirements.txt           - Minimal Python dependencies
- analysis/run_analysis.py   - Example analysis script (set XLSX path at top)
- data/                      - Script will create this folder and save processed outputs here

## Notes

- The example script is intentionally small and intended as a starting point. Replace or extend it with more specific analysis steps for your data.
- If your Excel file has multiple sheets, `run_analysis.py` will load the first sheet by default. Modify the script to load a specific sheet if needed.

If you want, I can also adapt the script to accept the path as a command-line argument or via a small config file — tell me which you prefer and I will update the repo accordingly.
