
# World Cup Player Performance Analysis

Analyzes World Cup player performance using PCA (Principal Component Analysis) to rank players by position, with interactive Power BI dashboards for visualization.

## Overview

This project ranks players within their position (GK, DEF, MID, FWD) by combining 12 performance metrics into a single composite score. Includes correlation analysis to show which stats move together, and a two-page Power BI dashboard for exploration.

## Files

- **`World_Cup_Analysis.ipynb`** — Python analysis (pandas, scikit-learn, matplotlib)
- **`Dashboard_World_Cup.pbix`** — Power BI dashboard (Teams & Players pages)
- **`player_stats.csv`** — Player statistics (12 metrics)
- **`teams.csv`** — Team metadata

---

## How It Works

**1. Data Prep**

- Load player stats and team data, fill missing values with 0
- Merge datasets on team_id

**2. Position Segmentation**

- Split players into four groups (GK, DEF, MID, FWD)
- Goalkeepers have different "good stats" than midfielders, so analysis is stratified

**3. Correlation Analysis**

- Generate heatmaps for each position showing which metrics move together
- Example: defenders with more tackles tend to have more yellow cards

**4. Principal Component Analysis (PCA)**

- Normalize 12 performance metrics (StandardScaler)
- Extract 1 principal component (PC1) that captures maximum variance
- PC1 becomes a composite "overall performance" score for each player
- High PC1 = top performer; Low PC1 = weaker performer

**5. Ranking**

- Rank players within each team by PC1 score
- Create labels (GK1, DEF1, DEF2, etc.) to identify top players per team

**6. API Integration**

- Generate Sofascore photo URLs using player IDs (for dashboard display)

---

## Dashboard (Power BI)

**Teams Page**

- Team-level summary with map and aggregated statistics

**Players Page**

- Player distribution by position (donut chart)
- PC1 score scatter plot (filterable by position)
- Player details table with performance metrics
- Player photos via Sofascore API

---

## Known Issues

**Player Photos**
Some photos in the Power BI dashboard may not match players due to player ID mismatches between the source data and Sofascore API. The concept is sound, but the data integration needs refinement. The analytics and statistics are accurate—photos are decorative only.

---

## Setup & Run

**Prerequisites**

```bash
pip install pandas scikit-learn seaborn matplotlib jupyter
```

**Run Notebook**

```bash
jupyter notebook World_Cup_Analysis.ipynb
```

**Open Dashboard**

- Open `Dashboard_World_Cup.pbix` in Power BI Desktop (data is embedded, no external connection needed)
