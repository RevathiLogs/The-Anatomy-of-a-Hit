# Track Popularity and Explicit Content Analysis

## 1. Objectives
1. How is track popularity distributed?
2. How do explicit and non-explicit tracks compare in count and average popularity?
3. How does track popularity vary with duration?
4. How does popularity vary with energy and danceability?

## 2. Dataset and Variables
I have used the Spotify Tracks Dataset for this analysis, focusing specifically on the following key columns:
- **`popularity`**: This is the target numeric score ranging from 0 to 100 that represents the overall popularity of a track.
- **`explicit`**: This is a boolean flag (`True`/`False`) indicating whether a track contains explicit content.
- **`duration_ms`**: This is the track length measured in milliseconds, which was converted to minutes (`duration_min`) for easier interpretation of the visualization.
- **`energy`**: This is a perceptual measure of intensity and activity (0.0 to 1.0).
- **`danceability`**: This is a metric describing how suitable a track is for dancing(0.0 to 1.0).

## 3. Data Preparation & Cleaning
- **Explicit Encoding**: The `explicit` column uses boolean values (`True`/`False`), so it required no formatting changes.
- **Missing Values**: Only 1 track name and 1 artist were missing out of 114,000 rows. Since the core analysis targets numeric scores (popularity and audio features), these rows were retained to preserve valuable data.
- **Duplicates**:I identified 27,268 duplicate rows in the selected columns and removed them to reduce repeated records in the analysis.

## 4. Exploratory Data Analysis & Visualizations
1. **Track Popularity Distribution**: I created a purple Seaborn histogram (`bins=50`, `kde=True`) to analyze the spread of popularity scores across the cleaned dataset.
2. **Explicit vs. Non-Explicit Comparison**: I created side by side subplots comparing total track counts (`sns.countplot`) and average popularity scores (`sns.barplot`) between explicit and non-explicit tracks.
3. **Track Popularity vs. Duration**: I converted duration to minutes and used a transparent scatter plot (alpha=0.1) with an x-axis limit of 10 minutes to minimize overplotting across a large dataset.
4. **Popularity vs. Energy & Danceability**: I rounded features to 1 decimal place (0.1 intervals) and plotted dual line plots (`sns.lineplot`) to track average popularity trends across energy and danceability levels.

## 5. Findings & Observations

### A. Track Popularity Distribution
- **The Zero Popularity Spike**: There is a massive spike of approximately 7,000 tracks with a popularity score of exactly 0, indicating that there are a large volume of completely undiscovered or negligible streaming tracks.
- **Two Distinct Peaks**: Excluding the zero scores, the distribution reveals two main peaks: a sharp peak around a score of 20–25, and a broader one around 40–45.
- **The Rarity of True Hits**: The right tail drops off steeply after 60. Tracks achieving a popularity score above 80 are extremely rare.

### B. Explicit vs. Non-Explicit Tracks
- **Volume Imbalance**: The vast majority of tracks on Spotify are non-explicit (`False`), with explicit tracks (`True`) making up a smaller fraction.
- **Popularity Advantage**: Despite being fewer in number, explicit tracks maintain a higher average popularity score than non-explicit tracks, suggesting higher average listener engagement.

### C. Track Popularity vs. Duration
- **The 3-Minute Sweet Spot**: Most tracks are concentrated between approximately 2 and 4.5 minutes. The scatter plot also shows that highly popular tracks occur within this range.
- **Longer Tracks Lose Traction**: Tracks longer than 5 minutes appear less concentrated at very high popularity scores.
### D. Popularity vs. Energy & Danceability
- **The Energy Sweet Spot**: Average popularity peaks in the mid-to-high energy range (0.5 to 0.7). Popularity drops for the most intense tracks (0.9 to 1.0), showing maximum energy does not guarantee a hit.
- **The Danceability Arc**: Follows a similar curve, rising steadily to a peak between 0.5 and 0.7 before falling off at extreme danceability levels (1.0).
- **Moderation is Best**: Listeners clearly favor tracks in the middle-upper ranges over absolute extremes.

## 6. Limitations
- **Dataset Scope**: These findings only apply to this specific Spotify dataset and might not represent all music everywhere.
- **Correlation vs. Causation**: These trends show patterns in the data, but they don't prove that these factors directly cause a song to become a hit.

## 7. Conclusion
This analysis successfully mapped out popularity distributions, explicit content dynamics, and optimal track durations, creating a strong foundation for the team's project.