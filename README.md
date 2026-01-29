# Baseball Analytics: Bat Speed vs Sprint Speed Analysis

## DSGA 1007 Final Project

### Project Overview

This project investigates the relationship between **bat speed** (rotational athleticism) and **sprint speed** (linear athleticism) in Major League Baseball players using data from the 2023-2025 seasons. The analysis explores whether faster runners generate higher bat speeds and how this relationship varies across different player demographics.

### Research Questions

1. **Primary Question**: Is there a significant correlation between a player's sprint speed and their bat speed?
2. **Age Analysis**: Does the relationship between athleticism metrics change as players age?
3. **Position Analysis**: Do different defensive positions show varying correlations between bat and sprint speed?

### Dataset

The project combines two primary datasets:

- **Bat Tracking Data** (2023-2025): Contains metrics including average bat speed, swing rates, contact rates, and performance statistics
- **Sprint Speed Data** (2023-2025): Includes player sprint speeds, competitive runs, and bolts (runs ≥30 ft/s)

**Final Merged Dataset**: 1,775 player-season observations across 27 variables

#### Key Variables
- `avg_bat_speed`: Average bat speed in mph
- `sprint_speed`: Sprint speed in ft/sec
- `age`: Player age
- `position`: Defensive position
- `swings_competitive`: Number of competitive swings
- `competitive_runs`: Number of competitive runs

### Methodology

#### 1. Data Preprocessing
- Merged bat tracking and sprint speed datasets on player name, ID, and year
- Removed missing values for key metrics
- Applied filtering criteria to ensure data quality (200+ competitive swings, 100+ competitive runs)

#### 2. Statistical Analysis

**Linear Regression**
- Base model on full dataset
- Filtered model on reliable data points
- Position-specific regression models

**Hypothesis Testing**
- Two-sample t-tests comparing fast vs. slow runner groups
- 50/50 median split analysis
- 75/25 percentile split analysis

**Advanced Modeling**
- Ordinary Least Squares (OLS) regression with interaction terms
- Age-stratified correlation analysis
- Age-binned slope calculations

#### 3. Visualizations
- Distribution histograms with normal curve fits
- Scatter plots with regression lines
- Overlapping histograms for group comparisons
- Aging curves for both metrics
- Position-specific scatter plots with regression lines

### Key Findings

#### Overall Correlation
- **Weak positive correlation** exists between sprint speed and bat speed in the full dataset
- **Slope (full data)**: 0.12 mph bat speed per 1 ft/sec sprint speed increase
- **Slope (filtered data)**: 0.05 mph bat speed per 1 ft/sec sprint speed increase

The correlation becomes weaker when filtering for players with reliable sample sizes, suggesting the initial relationship may be influenced by sample size bias.

#### T-Test Results

**50/50 Split (Median)**
- T-statistic: 1.3895
- P-value: 0.1649
- **Conclusion**: No statistically significant difference in bat speed between fast and slow runners

**75/25 Split**
- T-statistic: 1.1310
- P-value: 0.2582
- **Conclusion**: No statistically significant difference even at extreme splits

#### Age Analysis

**OLS Regression with Age Interaction**
- R-squared: 0.015
- Interaction term p-value: 0.820
- **Conclusion**: The relationship between bat speed and sprint speed does NOT significantly change with age

**Age-Binned Correlation Trends**
```
Age Group    Slope
18-24        -0.05
24-27         0.02
27-30         0.04
30-35         0.19
35-45         0.20
```

While older players show slightly higher correlations, the overall effect remains weak and likely influenced by smaller sample sizes in older age groups.

**Aging Curves**
- Both bat speed and sprint speed decline with age
- Sprint speed shows a steeper decline
- Bat speed remains relatively stable until later career years

#### Position Analysis

**Correlation by Position** (ranked by absolute correlation strength)

| Position | Slope | Correlation | Sample Size |
|----------|-------|-------------|-------------|
| C        | 0.46  | 0.25        | 251         |
| SS       | 0.53  | 0.23        | 175         |
| 1B       | 0.45  | 0.19        | 168         |
| 3B       | 0.17  | 0.07        | 224         |
| RF       | -0.16 | -0.06       | 201         |
| DH       | 0.12  | 0.05        | 136         |
| 2B       | 0.05  | 0.03        | 216         |
| LF       | 0.07  | 0.03        | 198         |
| CF       | 0.03  | 0.01        | 199         |

**Key Insights**:
- Catchers and shortstops show the strongest positive correlations
- Outfielders (CF, LF, RF) show minimal to negative correlations
- Middle infielders generally show higher correlations than corner positions

### Conclusions

1. **Weak Overall Relationship**: There is minimal correlation between linear (sprint speed) and rotational (bat speed) athleticism in MLB players

2. **Age is Not a Moderating Factor**: The relationship between the two metrics does not significantly change as players age, contradicting the initial hypothesis

3. **Position Matters**: Defensive position appears to influence the relationship more than age, with catchers and shortstops showing the strongest correlations

4. **Independent Skills**: Bat speed and sprint speed appear to be largely independent athletic abilities, suggesting that training and development in one area may not necessarily translate to the other

### Technical Requirements

#### Dependencies
```python
pandas
matplotlib
numpy
scikit-learn
scipy
statsmodels
seaborn
```

#### Installation
```bash
pip install pandas matplotlib numpy scikit-learn scipy statsmodels seaborn
```

### File Structure
```
DSGA_1007_final_project/
├── DSGA1007_final.ipynb          # Main analysis notebook
├── bat_tracking_2025.csv         # 2025 bat tracking data
├── bat_tracking_2024.csv         # 2024 bat tracking data
├── bat_tracking_2023.csv         # 2023 bat tracking data
├── sprint_speed_2025.csv         # 2025 sprint speed data
├── sprint_speed_2024.csv         # 2024 sprint speed data
├── sprint_speed_2023.csv         # 2023 sprint speed data
├── merged_bat_sprint_data.csv    # Combined dataset (generated)
└── README.md                     # This file
```

### Usage

1. Clone the repository
2. Ensure all CSV files are in the same directory as the notebook
3. Install required dependencies
4. Run the Jupyter notebook cells sequentially

```bash
jupyter notebook DSGA1007_final.ipynb
```

### Future Work

- Incorporate additional performance metrics (exit velocity, launch angle)
- Analyze specific swing types (hard swings vs. contact swings)
- Investigate the relationship with offensive outcomes (batting average, OPS)
- Examine the impact of player biomechanics and training regimens
- Expand the dataset to include more historical seasons

### Data Sources

Baseball Savant (Statcast data)
- Bat tracking metrics
- Sprint speed measurements

### Course Information

**Course**: DSGA 1007 - Programming for Data Science  
**Institution**: New York University  
**Term**: Fall 2025

### License

This project is for educational purposes as part of the DSGA 1007 course requirements.

---

*Note: This analysis uses publicly available baseball statistics and is intended for academic research purposes only.*
