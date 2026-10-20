# Artist and Track Characteristics Analysis

**Project:** The Anatomy of a Hit: Decoding Audio Features of Global Chart-Toppers
**Section:** Member 4 — Artists and Track Characteristics Analysis
**Dataset source:** [Spotify Tracks Dataset on Kaggle](https://www.kaggle.com/datasets/yashdev01/spotify-tracks-dataset)
**Analyzed file:** `spotify-tracks-dataset (1).csv`

## 1. Objective

This section investigates artist frequency, track-duration patterns, and artist-level differences in track counts and popularity. It also documents basic data-quality issues. The analysis is descriptive and does not use machine learning.

## 2. Research questions

1. Which artists have the most distinct credited tracks in the dataset?
2. What is the distribution of track duration?
3. How do track counts and average popularity compare among the most frequently credited artists?
4. How are multiple-artist tracks handled?
5. What duplicate or invalid values should be considered when interpreting the results?

## 3. Data preparation and counting rules

- Standardized column labels and removed typical exported index columns where present.
- Removed exact duplicate rows; repeated `track_id` values were reported rather than automatically deleting records.
- Converted `duration_ms` to numeric and calculated minutes by dividing by 60,000.
- Excluded missing or non-positive durations from duration statistics and plots, but retained long positive durations in the numerical summary.
- Parsed list-like artist credits when possible. Each named artist receives a credit for a multi-artist track. The same artist/track-ID pair is counted once when a usable `track_id` exists.
- Calculated artist-level popularity summaries only if the dataset includes a usable `popularity` column.

## 4. Data-quality checks

| Check | Count |
| --- | --- |
| Rows in uploaded dataset | 114,000 |
| Rows after exact-duplicate removal | 113,550 |
| Exact duplicate rows removed | 450 |
| Rows with missing/non-positive duration | 1 |
| Rows with at least one parsed artist | 113,549 |
| Rows with multiple parsed artists | 29,894 |
| Rows with no usable artist name | 1 |
| Unique non-missing track IDs | 89,741 |
| Repeated track-ID rows after exact-duplicate removal | 23,809 |

The file contains **89,741 unique non-missing track IDs** and **23,809 repeated track-ID row(s)** after exact duplicates were removed. Artist frequency deduplicates the same artist/track-ID pair.

## 5. Track-duration summary

| Measure | Value (minutes unless noted) |
| --- | --- |
| Valid track records | 113,549.00 |
| Mean duration (minutes) | 3.80 |
| Median duration (minutes) | 3.55 |
| Standard deviation (minutes) | 1.77 |
| Minimum duration (minutes) | 0.14 |
| 25th percentile (minutes) | 2.90 |
| 75th percentile (minutes) | 4.36 |
| Maximum duration (minutes) | 87.29 |

The duration histogram and box plot display records up to 15 minutes for readability. All valid positive duration values remain included in the duration summary above. There are **151** valid-duration record(s) longer than 15 minutes (0.13%). These values were not silently removed.

## 6. Top artists

| artist_key | Artist | Distinct credited tracks | Mean popularity | Median popularity | Mean duration (min) |
| --- | --- | --- | --- | --- | --- |
| — | George Jones | 332 | 16.07 | 13.0 | 2.77 |
| — | Pritam | 323 | 53.52 | 53.0 | 4.51 |
| — | Wolfgang Amadeus Mozart | 305 | 10.42 | 7.0 | 2.3 |
| — | Arijit Singh | 259 | 58.17 | 60.0 | 4.5 |
| — | Hank Williams | 243 | 17.1 | 13.0 | 2.51 |
| — | my little airport | 171 | 33.22 | 32.0 | 2.5 |
| — | Glee Cast | 170 | 39.86 | 44.0 | 3.55 |
| — | Hillsong Worship | 167 | 44.5 | 44.0 | 5.47 |
| — | Yuvan Shankar Raja | 167 | 51.2 | 50.0 | 4.36 |
| — | BTS | 165 | 68.08 | 67.0 | 3.73 |

## 7. Key findings

- The artist with the highest credited track count in this dataset is **George Jones**, with **332 distinct credited track(s)** under the counting method used here.
- The mean track duration is **3.80 minutes** and the median track duration is **3.55 minutes** among records with valid positive durations.
- The mean popularity across valid-duration records with a numeric popularity value is **33.32** (based on 113,549 records).
- **29,894** record(s) contain more than one parsed artist name. These collaborations were credited to each parsed artist rather than treated as a single unnamed combined artist.

Interpretation should refer to the generated charts: the artist-frequency chart compares distinct track credits, the duration histogram and box plot show the distribution within the 0–15 minute display window, and the scatter plot (when available) compares artist track counts with average popularity.

## 8. Limitations

- Findings describe the uploaded dataset and its collection snapshot, not every track on Spotify or the entire global music industry.
- Popularity is a platform-specific score and may change over time; it is not a direct measure of artistic quality.
- Artist parsing depends on how names are encoded in the CSV. Plain ambiguous fields are not split on every comma to avoid incorrectly splitting names that contain commas.
- Repeated track IDs are flagged for transparency. Their presence does not, by itself, prove that the entire record is erroneous.
- Relationships in these descriptive charts do not establish causation.

## 9. Conclusion

This analysis describes which artists receive the most credited track entries in the dataset and summarizes the dataset's track-duration patterns. It compares artist-level track counts with average popularity when that field is available, while making collaboration-counting and data-quality decisions explicit. The numerical results above are calculated directly from the uploaded file and should be interpreted within the dataset's limitations.

## 10. Tools and reproducibility

- Python, Pandas, NumPy and Matplotlib
- Google Colab notebook: `notebooks/04_artist_analysis.ipynb`
- Dataset source: [Kaggle — Spotify Tracks Dataset](https://www.kaggle.com/datasets/yashdev01/spotify-tracks-dataset)
