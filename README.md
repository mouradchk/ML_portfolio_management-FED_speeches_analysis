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
