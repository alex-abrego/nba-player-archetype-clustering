# NBA Player Clustering Analysis
An unsupervised machine learning project that groups NBA players into archetype clusters by their distinct play styles using 2025-26 advanced box score metrics and tracking data.

## Project Status
Currently in development

## Project Objective
To discover if unsupervised machine learning can identify modern NBA playing-style archetypes without using traditional position labels. 

Further goals would be:

- To apply these clusters to player valuation and determine which players excel the most in these roles.
- To discover which players have the most statistically similar playing styles.
- Which combination of player archetypes have winning teams from recent history used in their successful campaigns.

## Modeling Philosophy
The project intentionally separates playing style from player quality.

Variables describing behavior, role, and shot selection are used to construct
player archetypes. Efficiency and impact metrics are withheld from clustering
and later used to evaluate players relative to others within the same archetype.

This helps prevent the clustering algorithm from simply separating stars,
role players, and low-impact players rather than discovering different styles
of play.

## Data
Data is collected from NBA.com using the `nba_api` Python package.

The analysis currently uses data from the 2025-26 NBA regular season.

Data sources include:

- Traditional player statistics
- Advanced statistics
- Player tracking data including:
- Passing
- Drives
- Catch-and-shoot attempts
- Pull-up shooting
- Touches
- Paint and post touches
- Rebounding tracking
- Hustle statistics
- Defensive activity
- Shot-location data

Players must have at least 250 total regular-season minutes to be included.

## Methodology

### 1. Data Collection
NBA data is collected using league-wide `nba_api` endpoints and cached
locally to reduce repeated API requests.

### 2. Data Wrangling and Feature Engineering
Raw totals are converted into playing-style measures such as:

- Drives per 100 possessions
- Potential assists per 100 possessions
- Catch-and-shoot attempts per 100 possessions
- Pull-up attempts per 100 possessions
- Paint touches per 100 possessions
- Screen assists per 100 possessions
- Deflections per 100 possessions
- Shot-location attempt shares

This is to account for differences in playing time and pace of play variations.

Efficiency metrics are generally excluded from the clustering model so that clusters represent playing style rather than player quality.

### 3. EDA and Feature Selection
Candidate variables are evaluated using:

- Missing-value analysis
- Distribution analysis
- Outlier inspection
- Correlation analysis
- Basketball stylistic interpretation

Highly redundant variables are removed when they provide similar information to avoid multiplying the weight of specific traits in the clustering model's distance calculation.

## Planned Workflow
1. Collect NBA data (Completed)
2. Clean dataset and feature engineering (Completed)
3. Perform exploratory data analysis (Completed)
4. Preprocess and dimensionality reduction (In-Progress)
5. K-means and Gaussian Mixture Model clustering (In-Progress)
6. Interpreting and naming archetype clusters
