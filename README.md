# Spotify Tracks Dataset Analysis & Visualization

## Overview
This repository contains a comprehensive exploratory data analysis (EDA) of a Spotify dataset containing over 89,000 track entries across 113 unique genres. The project performs data cleaning, track deduplication, duration unit conversion, genre-level metric aggregation, and visualization of key audio metrics such as danceability, energy, and popularity.

---

## Key Features & Workflow

1. **Data Cleaning & Preprocessing**:
   - Dropped redundant index columns (`Unnamed: 0`).
   - Removed missing values (`dropna`) and deduplicated records using unique track identifier attributes.
   - Converted duration from milliseconds (`duration_ms`) to seconds (`duration_sec`).

2. **Genre Representation**:
   - Aggregated total unique genres (113 total).
   - Filtered top-represented genres (averaging ~1,000 tracks each).

3. **Audio Features Analysis**:
   - Compared distribution of `danceability` and `energy` across genres using boxplots.
   - Evaluated genre popularity rankings and track duration profiles.

---

## Dependencies
- Python 3.8+
- pandas
- numpy
- matplotlib
- seaborn

---

## Installation & Usage

1. **Clone the repository**:
   ```bash
   git clone [https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git](https://github.com/YOUR_USERNAME/YOUR_REPOSITORY.git)
   cd YOUR_REPOSITORY
   ```

2. **Install requirements**:
   ```bash
   pip install pandas numpy matplotlib seaborn
   ```

3. **Run the script**:
   ```bash
   python main.py
   ```
