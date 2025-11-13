# Fuzzy_Logic
This Python script uses fuzzy logic (via rapidfuzz) to match company names from a main list with similar names across multiple reference lists (different columns in an Excel sheet). It is especially designed for Indian company names, where small naming variations like “Ltd”, “Private”, or “Technologies” make direct string matching unreliable.
🚀 Overview

This project uses fuzzy logic and RapidFuzz to compare and map organization names between multiple Excel sheets.
It’s built with real-world data challenges in mind — especially for Indian company datasets where corporate names often include extra suffixes, abbreviations, or variations.

Example:

“TATA AIG GENERAL INSURANCE CO LTD” → correctly matched with → “TATA AIG INSURANCE LIMITED”

🧩 Key Features

🔤 Text Cleaning & Normalization — removes punctuation, unwanted characters, and stopwords.

🧱 Custom Stopword Filtering — ignores business suffixes like LTD, PRIVATE, TECHNOLOGIES, etc.

🧮 Hybrid Fuzzy Matching Algorithm — combines multiple RapidFuzz ratios for more stable similarity scoring.

🧠 Smart Business Logic — penalizes group-level duplicates (e.g., “TATA MOTORS” vs. “TATA STEEL”).

📊 Multi-Source Comparison — matches one main dataset against multiple reference columns.

🧾 Detailed Match Classification — outputs confidence levels: Exact, High, Medium, or Low.

💾 Excel Output — results exported to an easy-to-read .xlsx file.

🧠 How It Works
1️⃣ Input

An Excel file with columns such as:

Main Names → Primary dataset

Parent company Sheet 2 Radhika

Automation File

SMS Names2

Zoho

2️⃣ Cleaning

Each name is standardized:

Uppercase conversion

Stopword and symbol removal

Trim spaces and invalid text (N/A, NULL, etc.)

3️⃣ Scoring

A hybrid fuzzy score is calculated using:

score = (
    0.5 * fuzz.token_set_ratio(query, choice)
  + 0.3 * fuzz.partial_ratio(query, choice)
  + 0.2 * fuzz.token_sort_ratio(query, choice)
)


Then adjusted for:

Common prefixes (e.g., TATA, HDFC, BAJAJ)

Word overlap (Jaccard similarity)

Containment and subset logic

4️⃣ Output

Final matches and scores are saved
