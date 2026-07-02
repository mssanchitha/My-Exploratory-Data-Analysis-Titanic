# Titanic — Exploratory Data Analysis (EDA)

An end-to-end EDA on the Titanic dataset covering data cleaning, feature engineering, visualization, and hypothesis testing.

## Project Objectives
- Ask meaningful questions about the dataset
- Explore data structure (variables, data types)
- Clean data & handle missing values
- Engineer new features
- Identify trends, patterns, anomalies
- Test hypotheses using statistical tests
- Detect and address data issues

## Dataset
- **Source:** Titanic passenger data (1912)
- **Rows:** 891 | **Columns:** 12
- **Target variable:** `Survived` (0 = died, 1 = survived)

## Tech Stack
Python 3 · pandas · numpy · matplotlib · seaborn · scipy

## Data Cleaning
- `Age` missing values → filled with median
- `Embarked` missing values → filled with mode
- `Cabin` (77% missing) → converted into `HasCabin` binary flag

## Feature Engineering
| Feature | Description |
|---|---|
| `FamilySize` | SibSp + Parch + 1 |
| `IsAlone` | 1 if traveling alone |
| `Title` | Extracted from Name (Mr, Mrs, Miss, Master, Rare) |
| `AgeGroup` | Child, Teen, Adult, MiddleAge, Senior |
| `FareGroup` | Low, Mid, High, VeryHigh (quartiles) |
| `HasCabin` | 1 if cabin info was available |

## Hypothesis Tests
| Test | Variables | Result |
|---|---|---|
| T-test | Gender vs Survival | Significant (p < 0.001) |
| Chi-square | Class vs Survival | Significant (p < 0.001) |
| ANOVA | Fare across Classes | Significant (p < 0.001) |
| Chi-square | Embarked vs Survival | Significant (p < 0.01) |

## Key Findings
1. **Gender** — Females: ~74% survival vs Males: ~19%.
2. **Class** — 1st class ~63% survival vs 3rd class ~24%.
3. **Family size** — Groups of 2–4 survived most; solo travelers and 5+ least.
4. **Title** — "Mrs" & "Miss" highest; "Mr" lowest.
5. **Fare** — Higher fare → higher survival (correlated with class).
6. **Embarkation** — Cherbourg (C) passengers had the highest survival rate.

## Data Issues Detected & Handled
- Missing `Age`, `Embarked` → imputed
- Missing `Cabin` (77%) → transformed into flag
- No duplicates
- A few fare outliers (>$300) retained (valid high-class fares)

## Files
- `eda.py` — full analysis script
- `titanic.csv` — dataset
- `chart1..chart8.png` — visualizations
- `README.md` — this report
- `.gitignore` — excludes venv & cache

## How to Run
```bash
pip install pandas numpy matplotlib seaborn scipy
python eda.py