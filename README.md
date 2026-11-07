# Data Analyst Internship — Task 1
## Data Cleaning and Preprocessing

**Dataset:** Medical Appointment No Shows (Kaggle)  
**Tools:** Python 3, Pandas

### Objective
Prepare the Medical Appointment No Shows dataset for analysis by checking duplicates, missing values, inconsistent text, date formats, and invalid age values.

### Dataset source
Original Kaggle dataset: https://www.kaggle.com/datasets/joniarroba/noshowappointments

The original file is named `KaggleV2-May-2016.csv`. Download it from Kaggle and place it in:
`data/raw/KaggleV2-May-2016.csv`

> The raw CSV is not bundled in this starter package. The dataset is hosted by Kaggle; download it from the source above before running the cleaning program.

### Project structure
```text
Medical_Appointment_Task1/
├── data/
│   ├── raw/                 # Put original Kaggle CSV here
│   └── cleaned/             # Generated cleaned CSV and summary
├── notebooks/
│   └── Task1_Data_Cleaning.ipynb
├── src/
│   └── clean_data.py
├── requirements.txt
├── Task_1_Summary.pdf
└── README.md
```

### How to run
1. Install Python 3.
2. Open a terminal in this project folder.
3. Install dependencies:
   `pip install -r requirements.txt`
4. Download the Kaggle CSV and save it to `data/raw/KaggleV2-May-2016.csv`.
5. Run:
   `python src/clean_data.py`

The program creates:
- `data/cleaned/medical_appointments_cleaned.csv`
- `data/cleaned/cleaning_summary.txt`

### Cleaning steps
- Standardize column names to lowercase with underscores.
- Correct known spelling inconsistencies: `hipertension` → `hypertension`; `handcap` → `handicap`.
- Preserve patient and appointment identifiers as strings.
- Remove exact duplicate rows.
- Standardize gender, neighbourhood, and no-show text.
- Parse scheduled and appointment dates as UTC datetimes.
- Convert numeric fields to numeric types.
- Fill missing age values with the median and missing gender with the mode, only when such values exist.
- Remove impossible ages outside 0–120; age 0 is retained because it can represent infants.
- Calculate `wait_days` and remove records where the appointment date precedes the scheduling date.
- Preserve the handicap field's original numeric categories rather than forcing it to 0/1.

### Important interpretation
In this dataset, `No-show = Yes` means the patient did not attend; `No-show = No` means the patient attended.

### Validation
The script prints and saves a cleaning log with row counts, duplicate counts, invalid values, and remaining missing-cell count. Use the generated log for the final numeric results; do not assume counts before running the script.

### Author
Prepared as a learning submission for Data Analyst Internship — Task 1.
