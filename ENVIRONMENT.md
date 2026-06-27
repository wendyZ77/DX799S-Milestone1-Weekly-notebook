# Python Environment

This project uses a dedicated virtual environment for Milestone One notebooks.

## Setup (already done)

```bash
cd /Users/moly-work/Documents/DX799s-O1
python3.12 -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python -m ipykernel install --user --name=modc-dx799s --display-name="ModC DX799s (Python 3.12)"
```

## Select kernel in Cursor / VS Code

1. Open any `ModC-week*.ipynb` notebook.
2. Click **Select Kernel** (top-right).
3. Choose **ModC DX799s (Python 3.12)**.

Do **not** use the system **Python 3.14.3** interpreter — many data-science packages are not yet stable on 3.14.

## Verify

```bash
source .venv/bin/activate
python -c "import pandas, sklearn, statsmodels, mlxtend, ipykernel; print('OK')"
```
