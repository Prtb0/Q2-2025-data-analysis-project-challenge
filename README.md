# Project Title: Crime, Socio-Economic Factors, and Policing in Chicago Neighborhoods

## 1. Project Overview

### **Premise**

The City of Chicago publishes a wealth of **open data** on crime incidents, demographic information, and policing activity. This project aims to **quantify** how crime rates vary among different Chicago neighborhoods, examine **socio-economic** factors (e.g., median income, unemployment rate, education levels), and explore whether **changes in policing strategies**—like additional patrols or targeted interventions—correlate with shifts in crime patterns over time.

**Key Research Questions**:
1. How do crime rates differ among Chicago neighborhoods, and how have they trended over the past several years?  
2. Do socio-economic indicators (income, educational attainment, unemployment, etc.) correlate with higher or lower rates of specific crime types?  
3. Have any notable **policing changes** or programs (e.g., targeted patrols, community policing initiatives) impacted crime statistics in certain neighborhoods?

---

## 2. Data Requirements & Sources

1. **Chicago Crime Data**  
   - **Source**: [Chicago Data Portal – Crimes dataset](https://data.cityofchicago.org/Public-Safety/Crimes-2001-to-Present/ijzp-q8t2).  
   - **Fields**: Date/time of incident, location (block, ward, police district), primary crime type (theft, assault, drug offenses, etc.), arrest made or not, etc.  
   - **Timespan**: At least the last 3–5 years (or more, if you have capacity).

2. **Neighborhood Boundaries / Demographics**  
   - **Source**: [Chicago Data Portal – Community Areas](https://data.cityofchicago.org/Facilities-Geographic-Boundaries/Boundaries-Community-Areas-current-/cauq-8yn6).  
   - **Description**: GeoJSON or shapefiles that delineate official community areas, often used to map or aggregate socio-economic metrics.

3. **Socio-Economic Indicators**  
   - **Source**: [Chicago Data Portal – Census/ACS-based Indicators](https://data.cityofchicago.org/browse?sortBy=most_accessed&pageSize=20&category=Community+%26+Economic+Development).  
   - **Examples**: Median household income, unemployment rate, education level (bachelor’s degree or higher), poverty level, etc.  
   - **Frequency**: Usually annual or multi-year averages (American Community Survey).

4. **Policing Strategy / Activity Data (if available)**  
   - **Source**: This can be trickier; check for data on police beats, number of officers, or specific programs in neighborhoods.  
   - **Possible references**: 
     - [CPD district-level data or staffing levels](https://home.chicagopolice.org/statistics-data/).  
     - Public announcements or official dashboards describing community policing initiatives, shot-spotter deployments, etc.

**Note**: If official data on policing strategies is not granular, you can use **proxies** like the number of police stops recorded in each district or the presence of specialized task forces in certain neighborhoods.

---

## 3. Suggested Analysis Outline

### A. Data Ingestion & Cleaning

1. **Obtain Chicago Crime Data**  
   - Download or use an API to fetch the “Crimes” dataset for your chosen timeframe.  
   - Clean the dataset (handle missing values, remove duplicates, parse dates properly).

2. **Standardize Neighborhood Information**  
   - Use GIS joins or crosswalks to **map each crime record** to a community area or ward.  
   - This is crucial for aligning crime incidents with socio-economic indicators.

3. **Incorporate Socio-Economic Indicators**  
   - Retrieve data on median income, unemployment rates, etc.  
   - Ensure consistent formatting (e.g., each row represents a neighborhood, year).

4. **Merge Policing Strategy/Activity Data** (optional, if available)  
   - Align policing changes or initiatives (like start/end dates, specific neighborhoods covered).  
   - Create flags or numeric measures representing presence/absence or level of policing efforts.

### B. Exploratory Data Analysis (EDA)

1. **Time-Series Exploration**  
   - Plot monthly or yearly crime incidents citywide and by major crime type.  
   - Identify spikes or trends that align with city events or policing announcements.

2. **Crime by Neighborhood**  
   - Compare total crime counts, crime rates (per 1,000 residents), or serious crime (violent vs. property) across neighborhoods.  
   - Visualize with maps or bar charts to highlight significant variations.

3. **Socio-Economic Correlations**  
   - Check if neighborhoods with lower median income or higher unemployment see elevated rates of certain crimes.  
   - Use scatter plots or correlation matrices to reveal possible relationships.

### C. Deeper Analysis / Modeling

1. **Regression or Classification**  
   - If you want to **predict** crime rates or see which indicators matter most, build a regression model with neighborhood-level data (crime rate as the dependent variable, socio-economic indicators + policing data as predictors).  
   - Alternatively, do a classification approach (e.g., high-crime vs. low-crime neighborhoods) using logistic regression or a tree-based algorithm.

2. **Difference-in-Differences (Optional Advanced)**  
   - If you can identify neighborhoods where a **new policing strategy** took place (treatment group) vs. similar neighborhoods without it (control group), try a difference-in-differences approach.  
   - Evaluate changes in crime before and after the strategy for both groups, isolating the policy’s potential impact.

### D. Visualization & Reporting

1. **Mapping**  
   - Create a **choropleth map** showing the distribution of certain crimes or total incidents across community areas.  
   - Overlay socio-economic layers (e.g., shading by median income).  
   - Tools: QGIS, ArcGIS, Python’s `geopandas`, or a JavaScript library if building a web-based interface.

2. **Interactive Dashboards**  
   - Use Tableau, Power BI, or a Python dashboard framework (Plotly Dash, Streamlit) to let users explore crime stats by crime type, timeframe, or socio-economic factor.

3. **Final Presentation**  
   - Summarize the extent to which socio-economic variables correlate with neighborhood crime.  
   - Document if there is any noticeable effect from policing changes.  
   - Provide caution on potential confounding factors (population shifts, unreported crime, etc.).

---

## 4. Potential Challenges & Considerations

- **Data Accuracy & Granularity**: Crime data might have geocoding errors, or policing data might only be available at a broader district level.  
- **Differences in Neighborhood Boundaries**: Chicago community areas vs. wards vs. ZIP codes can differ. Ensure consistent boundary usage.  
- **Population Adjustments**: Always consider using crime **rates** (per 1,000 or 100,000 residents) to account for population differences among neighborhoods.  
- **Ethical & Social Context**: Avoid oversimplifying complex social issues. Frame results as indicative rather than conclusive proof of cause-and-effect.

---

## 5. Final Deliverables

1. **Cleaned & Documented Datasets**  
   - A master dataset with columns for date, crime type, neighborhood identifier, relevant socio-economic metrics, policing initiatives (if used).

2. **Exploratory Analysis**  
   - Notebooks or reports with descriptive stats, correlation analysis, time-series plots, and initial mapping.

3. **Model / Advanced Analysis**  
   - (Optional) Regression or difference-in-differences results that quantify relationships or measure the impact of policing strategies.

4. **Visual Output**  
   - A set of charts/maps or an interactive dashboard demonstrating key insights across neighborhoods and time.

5. **Project Write-Up or Presentation**  
   - Summarize methodology (data sources, cleaning steps), findings, limitations, and potential policy implications.

---

## Conclusion

By investigating **crime rates** across **Chicago neighborhoods** in relation to **socio-economic indicators** and **policing strategies**, you’ll apply real-world data wrangling, spatial analysis, and statistical reasoning. This project can be as light-touch (simple descriptive maps and correlations) or deep (advanced causal inference with difference-in-differences) as you’re comfortable with. Either way, you gain **practical experience** in analyzing a high-value public dataset with direct social relevance. Good luck with your analysis!