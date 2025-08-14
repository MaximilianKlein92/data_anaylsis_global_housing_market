# European Housing Prices analysis

**European Housing Prices analysis** is a comprehensive data analysis tool designed to streamline data exploration, analysis, and visualisation. The tool supports multiple data formats and provides an intuitive interface for both novice and expert data scientists.

# ![CI logo](https://codeinstitute.s3.amazonaws.com/fullstack/ci_logo_small.png)

## Dataset Content

### Columns:

Country –
Name of the country (e.g., Germany, France, Italy, Spain, Netherlands, Sweden, Switzerland, UK).

Year –
Calendar year of observation (integer), covering roughly 2015–2024.

House Price Index –
Index value for average house prices in that country for the given year.
Usually base year = 2015 (value = 100), so changes reflect relative growth or decline.

Mortgage Rate (%) –
Average annual mortgage interest rate in percent for that country and year.

(Optional, derived in analysis) Prev Year Rate –
Mortgage rate shifted by one year, used for lagged correlation analysis.

### Content description:

Time series data for multiple countries in Europe.

Each row represents one country–year combination.

Values are numerical and continuous for House Price Index and Mortgage Rate (%).

Allows analysis of:

Trends in housing prices per country over time.

Relationship between interest rates and housing prices.

Cross-country correlations in housing markets.

### Time coverage:

Data spans ~10 years (2015–2024), including periods of major economic events:

COVID-19 pandemic (2020–2021)

Inflation and interest rate hikes (~2022–2023)

Various geopolitical and economic events (Brexit, Ukraine war, etc.)

## Business Requirements

I want to identify measurable factors that influence housing market affordability and use them to decide whether it’s better to buy now or wait.

## Hypothesis and how to validate?

#### 1. Hypothesis: It is better to buy a house in Crisis/Corona Times.

Meaning:
During crises (e.g., COVID-19), house prices might drop, making buying more affordable.

How to test it:

- Plotteing HPI over time for each country with major crisis events shaded.
- Lookeing for visible dips or slower growth during crisis periods.

#### 2️. Hypothesis: The European housing market is independent from the global market.

Meaning:
Housing price movements in one country are mostly unrelated to others.

How to test it:

- Calculating pairwise correlations between countries’ HPIs.
- Useing a clustered heatmap to visualize relationships.

3️. Hypothesis: When interest rates go down, house prices go up.

Meaning:
Lower borrowing costs stimulate demand, increasing prices.

How to test it:

- Calculating lagged correlation between Mortgage Rate and HPI (1-year lag).
- Creating scatter plots and dual-axis time series to visualize relationships.

## Project Plan, Methodology & Rationale

### 1. High-Level Steps Taken

1. **Define Business Requirements & Hypotheses**

   - **Hypothesis 1**: It is better to buy a house in crisis periods (e.g., COVID-19).
   - **Hypothesis 2**: The European housing market is independent from the global market.
   - **Hypothesis 3**: When interest rates go down, house prices go up.

2. **Data Exploration**

   - Reviewed dataset structure: annual data (2015–2024) for multiple countries, including House Price Index (HPI), Mortgage Rate, and other macroeconomic indicators.

3. **Data Preparation**

   - Cleaned and validated data types.
   - Created derived features (e.g., `Prev Year Rate` for lag analysis).
   - Pivoted data to wide format for correlation analysis.

4. **Analysis & Visualisation**

   - Matched each business requirement to appropriate statistical and visualisation techniques.
   - Produced plots using **seaborn** and **plotly** for interactivity.

5. **Interpretation**
   - Analysed plots to evaluate each hypothesis.
   - Recorded observations and linked them back to the business requirements.

---

### 2. Data Management

- **Collection**: Dataset supplied in structured CSV format, no missing values.
- **Processing**:
  - Standardised numeric formats.
  - Sorted by `Country` and `Year` to ensure chronological integrity.
  - Created lag variables and reshaped data for specific analyses.
- **Analysis**: Conducted using Python (`pandas`, `plotly`, `seaborn`), enabling reproducibility.
- **Interpretation**: Observations were made directly from visual patterns and correlation metrics.

---

### 3. Rationale: Mapping Business Requirements to Data Visualisations

#### Requirement 1: Identify whether it is better to buy a house during crisis periods

**Visualisations**:

- Time-series line plots of HPI per country with shaded crisis periods (COVID-19, Ukraine war, inflation surge).

**Rationale**:  
Time-series plots allow visual comparison of price movements before, during, and after crises, making it easy to spot potential dips or slower growth phases.

---

#### Requirement 2: Determine if European housing markets are independent from each other

**Visualisations**:

- Correlation heatmap of HPI between countries.
- Pairplot (scatter matrix) with regression lines and correlation coefficients.

**Rationale**:  
Heatmaps provide an overview of inter-market relationships at a glance, while pairplots reveal patterns and anomalies in specific country pairs.

---

#### Requirement 3: Understand the relationship between interest rates and housing prices

**Visualisations**:

- Scatter plots with regression lines of lagged Mortgage Rate vs. HPI.
- Dual-axis time series plots showing both HPI and Mortgage Rates over time.

**Rationale**:  
Scatter plots quantify and visualise correlation, while dual-axis plots show temporal alignment or lag effects between rates and price changes.

---

### 4. Choice of Methodologies

- **Correlation Analysis**: To quantify the strength and direction of relationships between variables.
- **Time-Series Visualisation**: To detect trends, anomalies, and impacts of events.
- **Lag Analysis**: To capture delayed effects (e.g., interest rate changes influencing next year’s prices).
- **Clustered Heatmap**: To uncover grouping or similarity patterns in housing markets.
- **Interactive Plots**: To enable deeper exploration of relationships and event impacts.

## Analysis Techniques Used

### Methods

- **Correlation Analysis**: Checked relationships between HPI across countries and between lagged Mortgage Rates and HPI.
- **Time-Series Analysis**: Tracked trends and crisis impacts.
- **Lag Analysis**: Used `Prev Year Rate` to assess delayed effects of interest rates.
- **Visualisations**: Heatmaps, scatter plots with regression, dual-axis time series, and interactive Plotly charts.

### Structure

- Hypothesis-driven: Each plot or metric targeted one of the three hypotheses.
- Started with EDA to validate and prepare the data before applying targeted analyses.

### Limitations & Alternatives

- Annual data limited event granularity; more frequent data would improve insight.
- Could add other factors (e.g., unemployment, construction costs) for deeper affordability analysis.

### Use of Generative AI

- Helped with hypothesis generation, plot design, and code optimisation.
- Provided quick interpretation of results and improved workflow efficiency.

## Ethical considerations

- Were there any data privacy, bias or fairness issues with the data?
- How did you overcome any legal or societal issues?

## Unfixed Bugs

### Known Issues

- **Unfinished Feature Engineering**: Planned to create additional engineered features but lacked a clear understanding of some columns’ meanings. Deferred this as it was not essential for testing the hypotheses.
- **Matplotlib Subplot Issue**: Initially could not get multi-metric subplots for one country to render correctly (only white space appeared). Resolved later with AI assistance, but some plot commands were forgotten and had to be relearned.

### Framework/Technology Shortcomings

- None critical. Most issues stemmed from syntax or plotting logic rather than library limitations.

### Knowledge Gaps & Resolution

- Relied on ChatGPT and GitHub Copilot to bridge gaps in plotting syntax and configuration.
- Knew the intended outcome for each visualisation and iterated through multiple versions until satisfied.

### Feedback & Iteration

- Did not actively seek peer or instructor feedback during the process due to feeling overwhelmed; improvements came through self-directed iteration.

## Development Roadmap

### Challenges & Strategies

- Faced difficulties understanding the meaning of certain columns, which delayed planned feature engineering.
- Initially struggled with creating complex subplots in Matplotlib; overcame this by using ChatGPT and GitHub Copilot to recall and apply the correct syntax.
- Often got distracted during work sessions, but a fixed deadline helped me refocus and push forward — similar to how I worked during my Master’s thesis, where most progress happened under high time pressure.

### Next Steps & Skills to Learn

- Deepen understanding of feature engineering techniques and dataset column interpretation.
- Improve confidence and speed in using Matplotlib, Plotly, and Seaborn without relying heavily on AI assistance.
- Explore more advanced time-series analysis methods for future housing market studies.

## Main Data Analysis Libraries

- **Pandas** – Used for data loading, cleaning, and transformation.  
  _Example_: Filtered country-specific data and created lagged interest rate columns using `shift()`.

- **NumPy** – Provided numerical operations and supported Pandas calculations.  
  _Example_: Handled missing values and performed array-based computations for correlation analysis.

- **Seaborn** – Created statistical visualisations for exploring relationships between variables.  
  _Example_: Generated correlation heatmaps and regression plots to test independence between housing markets.

- **Matplotlib** – Used for custom plotting and subplot creation when Seaborn’s defaults were not sufficient.  
  _Example_: Designed multi-panel figures showing different housing metrics for a single country.

- **Plotly** – Added interactive visualisations for deeper exploration.  
  _Example_: Built dual-axis time series plots to compare house prices and mortgage rates, and interactive scatter plots with hover tooltips.

## Credits

### Content & Code Assistance

- **ChatGPT** – Provided guidance, troubleshooting, and code suggestions for data cleaning, visualisation, and analysis.
- **GitHub Copilot** – Assisted with code completion, syntax recall, and alternative implementations.

No external repositories, tutorials, or media sources were used beyond these AI tools.

## Acknowledgements

I would like to thank my mother, who listened to my ideas and asked insightful questions that helped me better formulate my hypotheses.
