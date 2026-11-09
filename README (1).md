# Diet and Weight Loss Analysis

## Project Overview
This project analyzes weight loss over a six-week period using Python. It explores whether weight loss differs across age groups, height groups, starting-weight categories, and diet types. The analysis uses descriptive visualizations and statistical hypothesis testing, including one-way and two-way ANOVA.

## Objectives
- Calculate each participant's weight loss over six weeks.
- Group participants by age, height, and starting weight.
- Visualize weight-loss distributions using density plots, histograms, and box plots.
- Use one-way ANOVA to compare average weight loss across age and starting-weight groups.
- Use two-way ANOVA to examine the effects of height and gender, and starting-weight category and diet type.
- Use interaction plots to visualize possible interactions between factors.

## Dataset
The notebook expects an Excel file named **`Diet_R (2).xlsx`** in the same folder as the notebook.

The notebook uses these dataset columns:
- `gender`
- `Age`
- `Height`
- `pre.weight` — weight before the diet
- `weight6weeks` — weight after six weeks
- `Diet` — diet group/type

Make sure the Excel file contains these columns and that the filename matches exactly. The notebook converts `gender` to numeric values and removes rows where gender cannot be converted.

## Tools and Libraries
- Python
- Jupyter Notebook
- pandas — data loading and manipulation
- matplotlib — plotting
- seaborn — statistical visualizations
- SciPy — one-way ANOVA
- statsmodels — two-way ANOVA and statistical models

## Analysis Workflow

### 1. Import libraries and load data
The notebook imports the required Python libraries, reads the Excel dataset, converts the `gender` column to numeric, and removes rows with invalid gender values.

### 2. Calculate weight loss
A new column is calculated:

```python
weightloss = pre.weight - weight6weeks
```

A positive value indicates weight loss; a negative value indicates weight gain.

### 3. Age-group analysis
Participants are divided into three quantile-based groups: **Young**, **Middle**, and **Senior**. The notebook:
- Plots the weight-loss distributions for the three age groups.
- Applies one-way ANOVA to compare their mean weight loss.
- Displays a box plot for comparison.

### 4. Height and gender analysis
Height is divided into **Short**, **Average**, and **Tall** groups using quantiles. A two-way ANOVA evaluates:
- The effect of height group.
- The effect of gender.
- The interaction between height group and gender.

A grouped box plot and an interaction plot are also generated.

### 5. Starting-weight and diet analysis
The notebook reloads and prepares the data, then divides participants into **Light**, **Moderate**, and **Heavy** starting-weight categories using quantiles. It:
- Plots weight-loss distributions for the three categories.
- Uses one-way ANOVA to compare the categories.
- Uses two-way ANOVA to study starting-weight category, diet type, and their interaction.
- Generates a grouped box plot and an interaction plot.

## Statistical Results Recorded in the Notebook
The saved notebook outputs contain these ANOVA results:

| Test | F-statistic | p-value |
|---|---:|---:|
| One-way ANOVA: Age group | 0.1879 | 0.8291 |
| One-way ANOVA: Starting-weight category | 0.2350 | 0.7911 |

For the two-way ANOVA models:

- **Height group and gender:** height group p = 0.4283, gender p = 0.5703, and interaction p = 0.7992.
- **Starting-weight category and diet:** starting-weight category p = 0.8075, diet p = 0.0082, and interaction p = 0.5400.

Using the common 0.05 significance level, the recorded output shows a statistically significant diet effect in the starting-weight-category-and-diet model. The other listed effects are not statistically significant at that level. These are statistical associations in this dataset and should not be interpreted as proof of causation.

## How to Run
1. Download or clone this project folder.
2. Place `Diet_R (2).xlsx` in the same directory as the notebook.
3. Install the required libraries:

   ```bash
   pip install pandas matplotlib seaborn scipy statsmodels openpyxl jupyter
   ```

4. Start Jupyter Notebook:

   ```bash
   jupyter notebook
   ```

5. Open `da_exp5_2.ipynb`.
6. Run the notebook cells from top to bottom.

## Notes
- The notebook uses `pd.qcut()` to create three groups based on the data distribution. Group boundaries depend on the dataset.
- The notebook contains a `seaborn.distplot()` call, which is deprecated in newer Seaborn versions. It can be replaced with `seaborn.histplot(..., stat="density", kde=True)` if needed.
- The notebook's saved outputs are based on the data available when it was last run. Re-running with a different dataset or modified data may produce different results.
- The Excel dataset is required to reproduce the analysis; it was not included with the notebook.

## Conclusion
This project applies exploratory data analysis and ANOVA techniques to study six-week weight loss across demographic and diet-related groups. The visualizations help compare distributions, while ANOVA tests assess whether observed group differences are statistically significant.
