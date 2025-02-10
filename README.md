# Machine Learning for Portfolio Management and Trading project

### Notebook structure :

1.	Introduction : Outlines the project’s context, objective and contributions.
2.	Data : Details the sources, preprocessing steps, and exploration of the datasets.
3.	Methodology : Describes the building of indicators and machine learning models, as well as experimental setup employed.
4.	Results and analysis : Presents the empirical findings, visualizations, and interpretations of the data.
5.	Discussion : Analyzes the implications, limitations, and potential future directions of the study.
6.	Conclusion : Summarizes the key takeaways and the overall significance of the research.

## 1 - Introduction
The aim of our project is to use data from speeches by FED officials, scraped from the site, to determine a signal about economic conditions. After using NLP techniques to construct this signal, we deploy a RandomForest model to predict the log-returns of Treasury bills over a 10-year horizon. Features include our indicator, as well as other macro indicators useful for prediction. We then develop a simple trading strategy, which consists of going long if our model predicts a rise, and going short if it does not.

## 2 - Data
### Scrapping the data
In this section, we provide the code to obtain speech data for all FED officials since 2006. We have scraped the data from the following link : https://www.federalreserve.gov/newsevents/speeches.htm. As a first step (first cell), we've provided the code that scrapes the first page, to show you how well it works. Execution time is approximately 1 minute 30 seconds. However, scrapping all the speeches since 2006, i.e. all 58 pages on the site, takes over an hour. It's the code in the second cell that makes this possible. We therefore do not recommend that you run this cell. To make things easier, we've extracted the file we put on our GitHub repo (https://github.com/cominho/Machine-Learning-for-Portfolio-Management-and-Trading/blob/main/fomc_speeches.xlsx), and import it directly via the repo URL (so no need for external files to the notebook). As a result, you can start the project directly from the third cell of the notebook (sub-section "Data cleaning and formatting").

### 3 - Methodology
### Macro data : identification of relevant variables from the three bonds at different maturities
**Feature construction for Treasury yields**

This section of the code focuses on creating a structured dataset to analyze and model the behavior of the US Treasury yield curve. We combine data for yields for 3 months, 5-year, 10-year and 30-year maturities were brought together into a single DataFrame.

**Building main indicators**  
   - **Daily returns** : These provide a measure of the percentage change in yields from one day to the next, helping to track market movement at each maturity.  
   - **Spreads** : Differences between yields of various maturities, such as the 5-year minus the 3-month, are commonly used to assess market sentiment, predict economic cycles, or identify potential curve inversions.  
   - **Rolling statistics** : By calculating rolling averages and standard deviations over a set window (20 days in this case), we capture both the recent trend and the short-term volatility of yields.

**Principal Component Analysis (PCA)**  
Then, we apply PCA to reduce the dimensionality of the dataset and extract key factors driving the yield curve's shape. The first three principal components often align with the curve's main characteristics :  
- The **first component** reflects the overall level of the curve  
- The **second component** relates to its slope
- The **third component** represents its curvature.

This method simplifies the analysis by summarizing the yield curve into a few interpretable factors, often linked to macroeconomic influences but we have to be carreful to the forward looking biais this transformation brings.
