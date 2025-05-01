**Global Disease‐Burden Time-Series Forecast & Anomaly Detection**  

This project builds a **fully pandas-driven**, end-to-end pipeline that transforms raw, multi-country disease-burden data into clear, actionable insights. By ingesting annual death counts for 30 years and 34 disease categories, it reshapes the data into a tidy “long” format, then applies ARIMA(1,1,1) models to each country–disease time series. Whenever observed mortality for a given year falls outside the model’s 95% prediction interval, that year is flagged as an **anomaly**—potentially signaling an outbreak, reporting error, or other epidemiological event.

Key components include:  
- **Data Wrangling with pandas**: standardized column names, handled missing values, and melted the wide dataset into a one-record-per-country/year/disease structure.  
- **Automated Time-Series Modeling**: looped through every valid series (per country and disease), fit ARIMA models via `statsmodels`, and merged forecasts and confidence bands back into the DataFrame.  
- **Anomaly Detection & Reporting**: compared actual vs. forecasted deaths to identify outliers, aggregated all anomalies into a single DataFrame, and exported the results to an Excel report.  
- **Visualization**: generated polished Matplotlib charts showing actual counts, forecasts, confidence intervals, and red markers for anomalous years—perfect for stakeholder presentations.

By focusing squarely on pandas for data ingestion, transformation, and analysis, this project not only highlights advanced data-wrangling techniques but also demonstrates how to scale time-series modeling across hundreds of series with minimal custom code. The deliverables—a comprehensive anomaly report and intuitive visualizations—make it an ideal showcase for any data-scientist or analyst portfolio.

```markdown
# Global Disease-Burden Time-Series Forecast & Anomaly Detection

## Table of Contents
- [Project Overview](#project-overview)
- [Features](#features)
- [Dataset](#dataset)
- [Technologies & Libraries](#technologies--libraries)
- [Installation](#installation)
- [Usage](#usage)
- [File Structure](#file-structure)
- [Contributing](#contributing)
- [Future Enhancements](#future-enhancements)
- [License](#license)
- [Contact](#contact)

## Project Overview
This project builds a **pandas-centric**, end-to-end pipeline that:
1. Ingests and cleans a multi-country, multi-year disease-burden CSV.
2. Reshapes data to long format (one row per country–year–disease).
3. Fits ARIMA(1,1,1) models to each country–disease time series.
4. Flags statistically significant anomalies (years where observed deaths fall outside the 95% forecast interval).
5. Generates visualizations and exports an Excel report of all detected anomalies.

This serves as both a **public-health surveillance tool** and a **portfolio showcase** of advanced pandas, time-series modeling, and automation skills.

## Features
- **Data Cleaning & Reshaping**  
  - Standardize column names, handle missing values, sort by country/year
  - Melt wide format into long format for analysis
- **Time-Series Modeling**  
  - Automated ARIMA(1,1,1) fitting per country/disease
  - In-sample forecasting with 95% confidence intervals
- **Anomaly Detection**  
  - Flags years where actual deaths deviate from forecast bounds
  - Aggregates all anomalies into a single DataFrame
- **Visualization & Reporting**  
  - Matplotlib plots showing actual vs. forecast vs. confidence bands
  - Red markers for anomalies
  - Excel export (`anomalies_detected.xlsx`) ready for stakeholder review
- **Batch Processing**  
  - Loop over all valid series, with progress bars via `tqdm`
- **Google Colab-Ready**  
  - Simple file upload/download
  - Minimal setup in a hosted notebook environment

## Dataset
- **Source**: WHO Global Health Estimates (annual deaths by cause, circa 1990–2019)
- **Dimensions**: ~200 countries/territories × 34 disease categories × ~30 years
- **Format**: CSV with columns  
  `Country/Territory`, `Code`, `Year`, `<Disease_1>`, `<Disease_2>`, …, `<Disease_34>`

## Technologies & Libraries
- **Python 3.8+**
- **Google Colab**
- **pandas** — data manipulation  
- **numpy** — numerical operations  
- **statsmodels** — ARIMA modeling  
- **matplotlib** — plotting  
- **tqdm** — progress bars  
- **openpyxl** — Excel export  
- **google-colab** utilities — file upload/download  

## Installation

1. **Clone the repository**  
   ```bash
   git clone https://github.com/your-username/disease-burden-anomaly-detection.git
   cd disease-burden-anomaly-detection
   ```

2. **Open in Google Colab**  
   - Upload `Global_Disease_Burden_Anomaly_Notebook.ipynb` to Colab.
   - Or use:  
     ```
     https://colab.research.google.com/github/your-username/disease-burden-anomaly-detection/blob/main/Global_Disease_Burden_Anomaly_Notebook.ipynb
     ```

3. **Install Python dependencies** (if running locally)
   ```bash
   pip install pandas numpy statsmodels matplotlib tqdm openpyxl
   ```

## Usage

1. **Upload Dataset**  
   In the Colab notebook, run:
   ```python
   from google.colab import files
   uploaded = files.upload()  # select your CSV
   df = pd.read_csv('your_dataset.csv')
   ```

2. **Follow the Notebook Steps**  
   - Data cleaning & reshaping  
   - Model fitting & anomaly detection  
   - Visualization of a selected country/disease  
   - Batch looping to collect all anomalies  
   - Export results to Excel  

3. **Download Results**  
   ```python
   from google.colab import files
   files.download('anomalies_detected.xlsx')
   ```


- **data/** — place your CSV here (if running locally)
- **Global_Disease_Burden_Anomaly_Notebook.ipynb** — main Colab notebook
- **requirements.txt** — list of `pip` dependencies
- **README.md** — this file

## Contributing
Contributions are welcome! To propose changes:
1. Fork this repo.
2. Create a new branch: `git checkout -b feature/YourFeature`.
3. Commit your changes: `git commit -m 'Add some feature'`.
4. Push to the branch: `git push origin feature/YourFeature`.
5. Open a Pull Request.

Please follow the existing style and include clear descriptions of additions or fixes.

## Future Enhancements
- Integrate population data to compute per-capita rates.
- Allow dynamic ARIMA order selection or support exponential smoothing.
- Add interactive parameter tuning via **ipywidgets** or **Streamlit**.
- Deploy as a standalone web app using **Voila** or **Streamlit Cloud**.
- Incorporate geospatial mapping of anomalies on a world map.

## Contact
— **Muhammad Shabbar**  
— Email: shabbaraza26@gmail.com  
```
