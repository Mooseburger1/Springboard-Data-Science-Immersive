# Capstone One Project Proposal

**Title:** Using Sentiment to Predict Cryptocurrency Price

**Problem:** $18,000!!! That was the price of one Bitcoin in late 2017, up from its inaugral price point of 0.003 cents in 2010. With those type of returns, it is hard for anyone to not suffer from FOMO (fear of missing out) on the "Next Bitcoin". But with the ambiguity of blockchain technology, decentralized nature of cryptocurrency, and over 1000 altcoins to choose from, how does one even begin to pick a coin. Even tougher, how does one pick a **Winner**? The technology surrounding most altcoins are still under development. Because of this, most investors are buying into coins for what they may become, not what they are today. So can we predict from daily sentiment, hype, and marketing, future gains or losses?

**Who might care?** A $100 dollar investment in Bitcoin back in 2010 would've netted $600 Million dollars at its highest price point. The possibility of those types of returns on other coins is enough to make everyone care! 

**Data:** Articles from Forbes.com, CNBC.com, Cointelegraph.com, Bitcoin.com, and Coindesk.com on a particular altcoin scraped from the web. Historical price data of said coin in conjuction with historical price data of bitcoin (BTC) and (ETH) since these are the most common coins needed to purchases altcoins

**Modeling approach:** As earlier stated, a lot of coins on the market today support technology currently in development, not a tangible platform. A project that appears to be and sounds like a future game changer would undoubtedly spike in price.Therefore a coins inherent value can be correlated to the news, marketing and hype surrounding it. Overly positive sentiment via news articles, twitter or reddit on a coin can have investors throwing money at it. Conversely, negative sentiment can make those same investors dump everything, tanking the price as a consequence. Therefore, an overall sentiment will be extracted of each article. This sentiment score in conjuction with historical prices of the coin of interest will be paired with historical prices of Bitcoin and Ethereum as features to be fed into multiple machine learning algorithms, both supervised and unsupervised. From there, the best performing model will be focused on and optimized for future price predictions.

**Possible limitations:** Due to its decentralized nature and 24/7 trading hours, predicting a specific price point might be too tall of a task. At least for a very accurate prediction. Because of this, it might be more feasible to predict future daily, weekly, or monthly price percentage change. Conversely, due to the mass entropy of the cryptocurrency realm, the possibility of accurately modelling it might be unfeasible. True randomness and disorder has no real model.

**Deliverables:** 
1.    Codes (notebooks) for:

	a.    data acquisition - 1.) A custom web scraper for extracting online articles 2.) Downloaded historical prices in CSV format
	
	b.    data cleaning - 1.) Cleanup/parsing of scraped web articles. 2.) Extracted overall Sentiment of articles via custom token dictionary.
	
	c.    EDA - Exploratory data analysis
	
	d.    machine learning model development
	
2.    Report on the capstone project
3.    Presentation on the capstone project
