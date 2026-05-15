City of Los Angeles Job Bulletins — Dataset Documentation
---

## 1. Dataset Overview

This project works with the **City of Los Angeles Job Bulletins** dataset, originally published on Kaggle by the City of LA. The dataset consists of 683 plain-text job bulletins published by the Los Angeles Personnel Department. Each bulletin describes a single job classification, including its duties, minimum qualifications (education, experience, required courses, and licenses), salary range, and application process.

The bulletins cover a wide range of public sector roles, from administrative clerks and accountants to engineers, police officers, and zoo curators, giving a broad cross-section of City of LA employment requirements.

---

## 2. Submitted Reference Files

Two reference CSV files are included with this submission. These files serve as schema and lookup references rather than the primary analysis dataset (see Section 3 for where the primary data will come from).

### `job_titles_clean.csv`

| Property | Value |
|---|---|
| Rows | 668 |
| Columns | 1 (`JOB_CLASS_TITLE`) |
| Description | The official list of recognized City of LA job class titles |

This file is the authoritative list of all job classifications covered by the bulletin corpus. It is used to validate job titles extracted from bulletins and to confirm complete coverage. Titles are in uppercase (e.g., `ACCOUNTANT`, `CIVIL ENGINEERING ASSOCIATE`). One title,`311 DIRECTOR`, has a numeric prefix reflecting the City's 311 service line. This is kept as-is.

**Cleaning applied:**
- Added column header `JOB_CLASS_TITLE` (original file had none)
- Stripped leading/trailing whitespace from all values
- Removed any duplicate entries
- Renamed from `job_titles .csv` (trailing space in filename) to `job_titles_clean.csv`

---

### `data_dictionary_clean.csv`

| Property | Value |
|---|---|
| Rows | 21 |
| Columns | 7 |
| Description | Schema definition for the structured output to be extracted from job bulletins |

This file defines every field that will be populated when parsing the job bulletins into structured tabular data. Each row describes one output field.

**Columns:**

| Column | Description |
|---|---|
| `Field Name` | The name of the output field (e.g., `JOB_CLASS_TITLE`, `EDUCATION_YEARS`) |
| `Annotation Letter` | The letter used to annotate this element in the bulletin annotation guide |
| `Description` | Plain-English description of what the field captures |
| `Data Type` | `String`, `Integer`, or `Float` |
| `Allowable Values` | Enumerated valid values where applicable |
| `Accepts Null Values?` | `yes` or `no`, whether the field is required for every row |
| `Additional Notes` | Extra parsing and formatting guidance |

**Cleaning applied:**
- Collapsed embedded newlines inside `Description`, `Allowable Values`, and `Additional Notes` cells to single spaces (the original CSV used RFC-compliant quoted multiline cells which can confuse some tools)
- Fixed typo in `JOB_CLASS_TITLE` description: "matching **in in** supplied" -> "matching in supplied"
- Stripped leading/trailing whitespace from all cells
- Normalized `Accepts Null Values?` to lowercase `yes`/`no`

---

## 3. Primary Data: How It Will Be Collected

The actual analysis dataset does not yet exist as a spreadsheet. It will be constructed by **programmatically parsing the 683 job bulletin `.txt` files** included in the dataset.

### Approach

Each bulletin is a plain-text file structured around consistent section headings:

```
DUTIES
REQUIREMENTS/MINIMUM QUALIFICATIONS
PROCESS NOTES
WHERE TO APPLY
APPLICATION DEADLINE
SELECTION PROCESS
```

We will use **Python with regex-based text extraction** to parse each file and populate the 21 fields defined in `data_dictionary_clean.csv`. This is conceptually equivalent to web scraping. The difference is that the "pages" are local text files rather than live URLs.