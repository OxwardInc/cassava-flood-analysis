# Cassava Flood Analysis: Farm Productivity and Income

An analysis of how flooding affects cassava farmers' yields, revenue and incomes, comparing flood-affected farms with flood-free farms. The analysis was carried out as data-analysis support for a final-year research project at the University of Port Harcourt, Nigeria.

## Research question

Do cassava farms hit by flooding perform worse than flood-free farms on yield, revenue and net farm income?

## Key findings

Flood-affected farms performed worse on every measure, but the differences are statistically significant only on a per-hectare basis.

| Measure | Flood-affected (mean) | Flood-free (mean) | Difference | p-value |
|---|---|---|---|---|
| Yield (kg/ha) | 7,877 | 14,574 | about 46% lower | < 0.001 |
| Total revenue per hectare (₦) | 1,550,316 | 2,692,024 | about 42% lower | < 0.001 |
| Net farm income per hectare (₦) | 659,261 | 1,444,358 | about 54% lower | < 0.001 |
| Total revenue per farm (₦) | 503,731 | 651,337 | about 23% lower | 0.071 |
| Net farm income per farm (₦) | 231,820 | 349,232 | about 34% lower | 0.072 |

In short, flooding is associated with much lower output and income for each hectare farmed. Per farm, the gap is large but not statistically significant at the 5% level, partly because farm sizes differ.

## Data

The data comes from a farm survey of cassava farmers, coded in a spreadsheet and exported as CSV files in the `data/` folder:

- `Cassava_Flood_Data_Coded - Sheet1.csv`: main survey (farm size, harvest, price, labour, inputs, transport, land rent, flood exposure)
- `Cassava_Flood_Data_Coded - Equipment used.csv`: tools owned, depreciation and other costs
- `Cassava_Flood_Data_Coded - Coping and adaptation strategies.csv` and `Cassava_Flood_Data_Coded - Effectiveness of flood-management interventions.csv`: loaded in the notebook but not analysed here

Sample size: [n flood-affected farms, n flood-free farms]. Location and survey period: [add].

## Method

1. **Cleaning:** standardised column names, converted values to numeric, and treated missing numeric values as zero.
2. **Groups:** farms were split into flood-free (1) and flood-affected (2) using the survey's flood exposure code.
3. **Land area:** farm size was converted from plots to hectares (15 plots = 1 hectare), falling back to the recorded hectares where plots were missing.
4. **Production and revenue:** yield (kg/ha), total revenue (harvest × price per kg) and revenue per hectare.
5. **Costs:** total variable cost (hired and family labour, inputs, transport, extra flood costs, other costs) and total fixed cost (land rent plus annual equipment depreciation, multiplied by the number of tools).
6. **Profit measures:** gross margin and net farm income (revenue minus total cost), per farm and per hectare.
7. **Testing:** Welch's t-tests comparing the two groups, which do not assume equal variances.

## Limitations

- The tests show association, not proof that flooding alone caused the gaps. Other factors, such as soil, location or farming practice, may also differ between the groups.
- Missing cost values were set to zero, which may understate costs for some farms.
- Family labour is included as a cost, so net farm income is lower than it would be if only cash costs were counted.
- Means can be pulled by a few unusually large or small farms. Medians or a non-parametric test would be a useful check.

## Tools

Python, pandas, NumPy, SciPy, Jupyter Notebook

## How to run

```bash
pip install pandas numpy scipy jupyter
jupyter notebook project_analysis.ipynb
```

Run the notebook from the repository root so the `data/` folder is found.

## Author

Divine Ogbonda | [LinkedIn](https://www.linkedin.com/in/divine-ogbonda-625014179/) | [GitHub](https://github.com/OxwardInc)
