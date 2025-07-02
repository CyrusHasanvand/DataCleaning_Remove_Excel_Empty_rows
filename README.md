# 🧹 Excel Cleaner for Memrise Vocabulary Lists

This simple Python script helps you **clean up Excel files** containing vocabulary words exported from Memrise (or entered manually), especially if there are **empty rows** between the entries.

✅ Built using the `pandas` library (already included with Anaconda).

---

## 📁 Input

A file named `MemWords.xlsx` in the same directory as the script.  
The Excel file should contain at least two columns:

| Word      | Meaning         |
|-----------|-----------------|
| apple     | a red fruit     |
| _(empty)_ | _(empty)_       |
| banana    | a yellow fruit  |

---

## 🚀 What It Does

- Loads your Excel file.
- Removes all **fully empty rows** (rows where all columns are blank).
- Resets the index (row numbers).
- Saves the cleaned data to `MemWords_Cleaned.xlsx`.

---

## 🧠 How It Works

```python
import pandas as pd

# Load original Excel file
df = pd.read_excel("MemWords.xlsx")

# Remove fully empty rows
df_cleaned = df.dropna(how='all')

# Reset the row index
df_cleaned.reset_index(drop=True, inplace=True)

# Save to a new Excel file
df_cleaned.to_excel("MemWords_Cleaned.xlsx", index=False)

print("Done! Cleaned file saved as MemWords_Cleaned.xlsx")
