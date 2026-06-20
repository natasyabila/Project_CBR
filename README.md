# Case-Based Reasoning for Indonesian Court Decisions

## Project Overview

This project implements a simple Case-Based Reasoning (CBR) system using Indonesian court decision documents obtained from the Supreme Court Directory (Direktori Putusan Mahkamah Agung RI).

The project consists of three main stages:

1. Data Cleaning
2. Case Representation
3. Case Retrieval

The objective is to retrieve previous legal cases that are most similar to a new case query.

---

## Project Structure

```text
CBR_Project/
│
├── data/
│   ├── raw/
│   ├── raw_pdf/
│   └── processed/
│
├── logs/
│
├── notebooks/
│   ├── 01_data_cleaning.ipynb
│   ├── 02_case_representation.ipynb
│   └── 03_case_retrieval.ipynb
│
├── requirements.txt
│
└── README.md
```

---

## Dataset

Domain selected:

Drug-related criminal cases (Narcotics Law).

Source:

Direktori Putusan Mahkamah Agung Republik Indonesia

A minimum of 30 court decision documents were collected in PDF format.

---

## Installation

### Clone or Download Project

Place the project folder in your local machine or Google Drive.

### Install Dependencies

```bash
pip install -r requirements.txt
```

---

## Stage 1 – Data Cleaning

Input:

```text
data/raw_pdf/*.pdf
```

Process:

* Extract text from PDF using PyMuPDF (fitz)
* Remove watermark and header/footer
* Normalize spaces
* Convert text to lowercase
* Validate document completeness

Output:

```text
data/raw/*.txt
logs/cleaning.log
```

Run:

```bash
01_data_cleaning.ipynb
```

---

## Stage 2 – Case Representation

Input:

```text
data/raw/*.txt
```

Process:

* Extract case number
* Extract legal articles (pasal)
* Generate case summary
* Count total words
* Store full text

Output:

```text
data/processed/cases.csv
data/processed/cases.json
```

Generated Attributes:

| Attribute       | Description               |
| --------------- | ------------------------- |
| case_id         | Unique case identifier    |
| no_perkara      | Court case number         |
| pasal           | Related legal article     |
| ringkasan_fakta | Summary of case facts     |
| jumlah_kata     | Total number of words     |
| text_full       | Complete cleaned document |

Run:

```bash
02_case_representation.ipynb
```

---

## Stage 3 – Case Retrieval

Input:

```text
data/processed/cases.csv
```

Process:

* TF-IDF Vectorization
* Cosine Similarity Calculation
* Retrieve most similar legal cases

Output:

List of similar court decisions ranked by similarity score.

Run:

```bash
03_case_retrieval.ipynb
```

---

## Example Workflow

```text
PDF Documents
      ↓
Data Cleaning
      ↓
TXT Documents
      ↓
Case Representation
      ↓
cases.csv
      ↓
TF-IDF
      ↓
Cosine Similarity
      ↓
Case Retrieval
```

---

## Author

Natasya Salsabila (2023-019) dan Senyiur Putri Hallinda (2023-021)

Informatics Engineering

Case-Based Reasoning Project
