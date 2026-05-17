# Dataset Characteristics

**[Notebook](exploratory_data_analysis.ipynb)**

## Dataset Information

### Dataset Source
- **Dataset Link:** https://www.kaggle.com/datasets/yamaerenay/spotify-dataset-19212020-600k-tracks?select=tracks.csv
- **Dataset Owner/Contact:** Public Kaggle dataset by user `yamaerenay`

### Dataset Characteristics
- **Number of Observations:** 202 tracks
- **Number of Features:** 21 features

### Target Variable/Label
- **Label Name:** `label`
- **Label Type:** Classification (binary)
- **Label Description:** Song mood class used to predict whether a track is perceived as happy or sad.
- **Label Values:** `happy`, `sad`
- **Label Distribution:** `happy`: 103 tracks (~51.0%), `sad`: 99 tracks (~49.0%)

### Feature Description
- **Track metadata:** `id`, `name`, `artists`, `id_artists`, `release_date` identify tracks and artists and provide release year context.
- **Popularity and duration:** `popularity` (Spotify popularity score) and `duration_ms` (track length in milliseconds).
- **Content flags:** `explicit` indicates whether a track is marked explicit.
- **Core audio features:** `danceability`, `energy`, `valence`, `acousticness`, `speechiness`, `instrumentalness`, `liveness`, `tempo`, `loudness` capture musical characteristics from Spotify.
- **Music theory fields:** `key`, `mode`, `time_signature` describe tonal and rhythmic structure.
- **Target column:** `label` is the supervised mood class.

## Exploratory Data Analysis

The exploratory data analysis is conducted in the [exploratory_data_analysis.ipynb](exploratory_data_analysis.ipynb) notebook, which includes:

- Data loading and initial inspection
- Statistical summaries and distributions
- Missing value analysis
- Feature correlation analysis
- Data visualization and insights
- Data quality assessment

### Key Findings
- No missing values were found in any column (`df.isnull().sum()` returns 0 for all 21 columns).
- After dropping missing values, the dataset size remained 202, confirming complete records.
- The class distribution is close to balanced (`happy`: 103, `sad`: 99), reducing class imbalance risk.
- Popularity statistics are similar between classes (mean popularity: `happy` 72.63 vs `sad` 71.82), suggesting limited popularity-driven label bias.
- Repeated artists exist (e.g., Billie Eilish appears 7 times), which may introduce artist-representation bias.
- Correlation analysis was performed across key audio features (`danceability`, `energy`, `valence`, `acousticness`, `tempo`, `loudness`, `speechiness`, `instrumentalness`, `liveness`) to support feature selection and modeling.
