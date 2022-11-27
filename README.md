# Investment-Portfolio-Builder
This is the final group project by Robin, Jessica, and Eric for the course CFM101 at the University of Waterloo

This project aims to create the riskiest portfolio consisted of only US securities given a csv file with any stock tickers.

In terms of coding concepts, this project incorporated:
1. Functions
2. Objected Oriented Programming
4. Threading
5. Usage of Python libraries (yfinance, Numpy, Pandas, etc.)
6. input cleaning/filtering

## The rules for the contest are as follows:
Choose one of two goals: you can either target the riskiest portfolio or the safest.  There will be 2 prize winning championship teams, and 2 prize-winning runner-up teams.  For teams targeting the riskiest: We will take the value of the portfolio on December 02, 2022 and subtract the starting value of $500,000.  We will then take the absolute value of that result, “the ending value”.  The team with the highest ending value will win.  For teams targeting the safest: We will take the value of the portfolio on December 02, 2022 and subtract the starting value of $500,000, “the ending value”.   The team with ending value closest to zero will win.
1. Dynamically create a portfolio, where you will not know which stocks you are choosing from beforehand 
2. The code will read in a .csv file containing a finite number of stock tickers. The title of the file will be “Tickers.csv” and will reside in the same directory as the code.
3. Ignore any tickers that do not reference a valid stock denominated in USD.
4. Only include stocks in your portfolio that have an average monthly volume of at least 200,000 shares, as calculated based on the time interval of January 01, 2022 to October 31, 2022.  A month is defined as a calendar month.  Drop any month that does not have at least 20 trading days. 
5. Portfolio must consist of a minimum of 12, maximum of 25 stocks for your portfolio. Each stock must make up a minimum of (100/(2n))% of the portfolio when weighted by value as of closing prices on November 25, 2022.  In addition, no individual stock may make up more than 25% of the portfolio when weighted by value.
6. Teams have $500,000 USD to spend on their portfolio, you MUST SPEND IT ALL. To do so, you can purchase fractional shares. 
7. no need to consider transaction fees
8. Output 2 dataframes and 1 csv file for the contest: Portfolio_Final, Stocks_Final and a csv version of Stocks_Final

## Our Strategy:

We chose to invert the risk-reducing/diversification principles we have learned and use them to create our portfolio. To be the riskiest portfolio, it must have the highest standard deviation possible: maximizing its potential growth or loss. The riskiest option would be a portfolio of a single, highly variable stock. However, the assignment required that we hold a minimum of 12 stocks, and that no stock could make up more than 25% of the portfolio. Thus, the structure of our portfolio was made  to maintain and support the risky nature of that single risky stock. 

To accomplish this, we ranked all stocks based on the highest standard deviations. Due to the maximum investing limit per stock, our portfolio primarily consists of three “main” securities. Otherwise, we would have put the least money possible in the rest of the portfolio while the rest goes into the main. However, to ensure the highest risk, given we had already put 25% of the investment into the main stock, we decided to increase the investment to the next stock that had the closest correlation. Once we had invested the maximum amount into that, we would move to the next one, ensuring that the least amount is invested in stocks with lower correlation to the main stock. For the other 9 stocks were chosen from the lower correlations from the top 12, and by the assignment restrictions, they were weighted according to the minimum requirements.  

Therefore, creating an uneven weighting of the first 3 stocks (25%, 25%, 12.5%) while all the other stocks had the bare minimum of just over 4% (100/2n%) in each. 

Our portfolio uses standard deviation, rather than expected return, as the primary metric for compatibility with the goal of the portfolio. This is because the final value of the portfolio will be calculated from the final values of the stocks. A highly volatile stock may have limited average returns, because it has extremely positive and negative percentage returns over time. Given only the final value of the stock will be considered, so it is more important that the stock be highly volatile, and end on an extreme value on the final calculation date, than have high expected return.  

The other 9 stocks were also chosen for their high correlation with the main stocks and given the smallest weighting possible. We did this to minimize diversification, and thus reduce the risk-reducing effects of holding multiple stocks. This met the assignment requirements, while preserving the risky nature of that one stock with the highest standard deviation. 
