# PDF Duty Calculator

A Flask-based web application that processes **CUSDEC (C.pdf)** and **Working Sheet (W.pdf)** PDF files to generate a consolidated Excel report containing customs duty calculations, tax rates, and working sheet information.

![Screenshot](Screenshot%202026-07-14%20105648.

---

## Features

- Upload two PDF files:
  - **C.pdf** (CUSDEC)
  - **W.pdf** (Working Sheet)
- Supports multiple companies:
  - Zellco
  - EGT
  - DFL
- Automatically extracts:
  - HS Codes
  - Customs Duty
  - CID
  - PAL
  - SSL
  - VAT
  - EIC
- Calculates Duty Amount (Ex. VAT)
- Merges tax information with Working Sheet data
- Generates Excel reports
- Automatic cleanup of uploaded files
- Simple web interface built with Flask

---

# Project Structure

```
project/
│
├── app.py                 # Flask Web Application
│
├── calculators/
│   ├── zellco.py          # Zellco calculator
│   ├── egt.py             # EGT calculator
│   └── dfl.py             # DFL calculator
│
├── templates/
│   └── index.html
│
├── uploads/
│
├── outputs/
│
├── requirements.txt
│
└── README.md
```

---

# Technologies Used

- Python 3.10+
- Flask
- Pandas
- pdfplumber
- OpenPyXL
- PyPDF2
- Werkzeug

---

# Installation

Clone the repository.

```bash
git clone https://github.com/yourusername/pdf-duty-calculator.git

cd pdf-duty-calculator
```

Install dependencies.

```bash
pip install -r requirements.txt
```

If a requirements file is unavailable:

```bash
pip install flask pandas pdfplumber openpyxl PyPDF2 werkzeug
```

---

# Running the Application

```bash
python app.py
```

The application will automatically open:

```
http://127.0.0.1:5000
```

---

# How It Works

## Step 1

Select the company.

Supported companies:

- Zellco
- EGT
- DFL

---

## Step 2

Upload

- **C.pdf**
- **W.pdf**

---

## Step 3

Click **Process**.

The application will

- Validate uploaded files
- Save temporary PDFs
- Execute the selected calculator
- Generate an Excel report
- Download the result automatically
- Remove temporary files

---

# Processing Workflow

```
User
 │
 │ Upload PDFs
 ▼
Flask App
 │
 ├── Validation
 ├── Save PDFs
 ├── Select Company
 │
 ▼
Calculator
(Zellco / EGT / DFL)
 │
 ├── Parse C.pdf
 ├── Parse W.pdf
 ├── Extract HS Codes
 ├── Calculate Duties
 ├── Merge Data
 ▼
Excel Report
 │
 ▼
Download
```

---

# Output Excel

Depending on the selected calculator, the workbook may contain:

- Merged_Working_Sheet_Tax
- Working_Sheet_Only
- Tax_Data_Only
- FOB_Summary_by_HS
- Summary
- Extracted_Text

---

# Extracted Information

From **CUSDEC (C.pdf)**

- HS Code
- Item Number
- Tax Base
- Tax Rate
- Tax Amount
- CID
- PAL
- SSL
- VAT
- EIC

From **Working Sheet (W.pdf)**

- HS Code
- Description
- Packages
- Quantity
- UOM
- Gross Weight
- Net Weight
- FOB
- Freight
- Insurance
- Other Charges
- CIF
- Total EXW

---

# Calculations

The application calculates:

- Duty Amount (Excluding VAT)

```
Duty Amount = Tax Base × Tax Rate / 100
```

It also merges duty information with Working Sheet data using the HS Code.

---

# Supported Companies

## Zellco

- Complete CUSDEC parser
- Complete Working Sheet parser
- Detailed Excel export
- Multiple worksheets

---

## EGT

- Complete tax extraction
- Working Sheet parsing
- Duty calculations
- Summary worksheets

---

## DFL

- Tax extraction
- Basic Working Sheet integration
- Excel export

---

# Validation

The application validates:

- Both PDFs are uploaded
- PDF file format
- Valid company selection
- Output generation
- File existence

---

# Dependencies

```
Flask
pandas
pdfplumber
openpyxl
PyPDF2
Werkzeug
```

---

# Future Improvements

- Additional company calculators
- OCR support for scanned PDFs
- User authentication
- Database integration
- Batch PDF processing
- Progress indicators
- Docker deployment
- REST API
- Logging
- Error reporting dashboard

---

# License

This project is intended for internal business use.

---

# Author

Developed for automated customs duty and Working Sheet processing using Python and Flask.
