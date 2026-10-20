# Artist and Track Characteristics Analysis

**Project:** The Anatomy of a Hit: Decoding Audio Features of Global Chart-Toppers  
**Section:** Member 4 — Artists and Track Characteristics Analysis  
**Dataset:** [Spotify Tracks Dataset on Kaggle](https://www.kaggle.com/datasets/yashdev01/spotify-tracks-dataset)  
**Notebook:** [`04_artist_analysis.ipynb`](../notebooks/04_artist_analysis.ipynb)

> **Documentation workflow:** This is the starter report for the initial documentation commit. After running the notebook in Google Colab, download the generated `artist_analysis.md` and replace this starter file with that generated report before final submission. Do not submit placeholders as final findings.

## 1. Objective

This section examines which artists are most frequently credited in the dataset, how track duration is distributed, and how track counts compare with average popularity among frequently appearing artists. It also documents relevant data-quality issues. This is exploratory data analysis; no machine-learning model is used.

## 2. Research questions

1. Which artists have the most distinct credited tracks in the dataset?
2. How is track duration distributed?
3. How do artist track counts and average popularity compare among frequently appearing artists?
4. How should multiple-artist tracks be counted?
5. What missing, invalid, or duplicate values may influence the analysis?

## 3. Dataset and variables

The analysis uses the Spotify Tracks Dataset provided through Kaggle. The notebook checks the actual CSV columns before proceeding. The main fields are:

| Column | Purpose |
|---|---|
| `artists` | Artist or artist-credit field; may contain multiple artists |
| `duration_ms` | Track length in milliseconds, converted to minutes for reporting |
| `track_id` | Used to prevent repeated artist/track credits from inflating counts when available |
| `track_name` | Helps identify tracks in previews |
| `popularity` | Used for artist-level descriptive comparisons when available |

## 4. Methodology

1. Load the CSV or a ZIP archive containing a CSV in Google Colab.
2. Standardize column labels and remove typical exported index columns.
3. Remove exact duplicate rows and convert relevant numeric fields.
4. Exclude missing or non-positive durations from duration summaries.
5. Parse list-like artist fields; credit each named artist for a collaboration.
6. Calculate distinct credited track counts for each artist. When a usable `track_id` exists, count an artist/track-ID pair once.
7. Calculate duration statistics and create a top-artist chart, duration histogram, duration box plot, and an artist track-count versus average-popularity scatter plot when popularity data is available.
8. Generate the final report from the actual notebook results.

## 5. Visualizations

The notebook creates:

- **Top 10 artists by credited track count:** a horizontal bar chart.
- **Track duration distribution:** a histogram displaying durations up to 15 minutes for readability.
- **Track duration box plot:** a second view of the central distribution up to 15 minutes.
- **Artist track count vs. average popularity:** a scatter plot for the 15 most frequently credited artists, when `popularity` is available.

Long positive durations are retained in the numerical summary; the 15-minute limit is only a display choice for the two duration plots.

## 6. Findings

**To be completed from real data:** Run `notebooks/04_artist_analysis.ipynb`. Its final reporting cell generates a results-based Markdown report with the calculated data-quality checks, duration summary, top-artist table, and key findings. Replace this starter document with that generated report before the final pull request is merged.

## 7. Limitations

- Results describe the provided dataset and its collection snapshot, not every song on Spotify or the full global music industry.
- Popularity is a platform-specific score and can change over time; it is not a direct measure of artistic quality.
- Artist parsing depends on the representation used in the source CSV. Plain ambiguous fields are not split on every comma because some artist names contain commas.
- Repeated track IDs are reported for transparency, not automatically treated as errors.
- Descriptive differences and associations do not prove causation.

## 8. Tools

Python, Pandas, NumPy, Matplotlib, Google Colab, Git and GitHub.

## 9. References

- [Spotify Tracks Dataset — Kaggle](https://www.kaggle.com/datasets/yashdev01/spotify-tracks-dataset)
- [Project GitHub repository](https://github.com/RevathiLogs/The-Anatomy-of-a-Hit)
