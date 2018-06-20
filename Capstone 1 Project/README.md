# Facilitation of Cryptocurrency Price Prediction by Sentiment Analysis
View the project proposal [Here](https://github.com/Mooseburger1/Springboard-Data-Science-Immersive/blob/master/Capstone%201%20Project/Proposal.md)


## Project Review Order
1. Web Scraper for News Articles [Here](https://github.com/Mooseburger1/Springboard-Data-Science-Immersive/blob/master/Capstone%201%20Project/Web%20Scraper/Web%2BScraper.ipynb)
2. Sentiment Analysis Performed on News Articles [Here](https://github.com/Mooseburger1/Springboard-Data-Science-Immersive/blob/master/Capstone%201%20Project/Data%20Wrangling/Sentiment_Analysis.ipynb)
3. Exploratory Data Analysis Performed [Here](https://github.com/Mooseburger1/Springboard-Data-Science-Immersive/blob/master/Capstone%201%20Project/EDA/EDA.ipynb)
4. Deep Neural Network Predictive Model Trained [Here](https://github.com/Mooseburger1/Springboard-Data-Science-Immersive/blob/master/Capstone%201%20Project/Machine%20Learning/Deep%20Learning%20Models.ipynb)


This project had a lot of steps involved, each of which probably could’ve been there own project. Each step is listed above with a link to the corresponding notebook. The notebooks come with detailed explanation and thought process. Every step took time in order to determine the best way to attack the problem.  The first of which was building an efficient API to scrape the articles needed to perform sentiment analysis. Parsing every individual article while copying and pasting would’ve taken days, maybe even weeks. 
The second part consisted of building a custom sentiment analysis algorithm due to poor performance of existing libraries. Because the cryptoworld is a very niche and specialized area, it has its own terms and language space that corresponds to it. This space unfortunately is outside the realm of everyday speech which in turn resulted in the initial poor performance of existing sentiment libraries. The custom algorithm itself in all reality could become its own stand alone entity, being improved and updated regularly. A positive and negative words dictionary was created from randomly chosen articles to facilitate custom sentiment analysis.
The third part consisted of data exploration, correlation analysis, and feature engineering. From the foundational data obtained from historical prices and created from sentiment analysis, even more data and metrics  were extrapolated.
Lastly, Deep Learning was utilized for predictive modeling implementation.
