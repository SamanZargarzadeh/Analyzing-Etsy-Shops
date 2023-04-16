# Analyzing Etsy Shops

Scraping data from various Etsy shops and organizing it into a clean database. Analyzing the data using Python and R, and creating linear and regression models revealed the key factors for shops' success. Applying feature engineering techniques improved the accuracy of the models.

•	Skills: Web Scraping, Python, R, Linear and Logistic Regression, Feature engineering 


## Data

a.	Summary
In order to examine profitable Etsy merchants and find trends that may assist individual sellers in growing their sales, we first performed a thorough examination of Etsy's history, taking into account its business strategy, characteristics, and competitive edge. Data on Etsy’s active sellers, their sales, and countries these sellers are located were obtained. To expand on the data and find insightful information, we made use of a number of analytical techniques such as histograms, bar plots, and heat maps to illustrate the data and make it easier to interpret. To further examine the data, we performed an Ordinary Least Square regression and logistic regression with sales as a dependent variable. In addition to these techniques, we also ran sentiment analysis and created a WordCloud from the web scraped data on Etsy sellers’ bio and announcements. We believe that our analysis can be useful to business owners either looking to launch their businesses or improve their sales and achieve success on Etsy's e-commerce platform.
b.	Description
Below, Fig. 3, is a description of the original data we obtained from Kaggle.  The data contains Etsy seller information from 2005, when Etsy was founded, to 2019 July. There are 7 columns and 65,531 rows in the data. The data's 7 columns are as follows:

Fig. 2


![image](https://user-images.githubusercontent.com/88157400/232275325-e2033854-1bfb-4d26-b55b-3b92bce7f2ac.png)



Fig. 3


<img width="471" alt="image" src="https://user-images.githubusercontent.com/88157400/232275289-654f224a-f7c4-46fb-8d8c-af2546cc4df6.png">




It is important to note that the mean number of sales is 579 items, mean review number is 141, and mean average review score is 3.5.
	As the data on Kaggle had limitations such as categories of selling items and information on each shop page, we turned to web scraping the current Etsy website. Below are the descriptions of the 17 variables in the web scraped data (Fig. 4) There are 17 columns and 5,992 rows in the data.


Fig. 4


![image](https://user-images.githubusercontent.com/88157400/232275545-c6b67ab1-d8c7-493d-b273-da38bb2b5d92.png)






The important findings are that the mean lifetime sales amount is 10,948 per seller, on average a seller has 4,120 admirers, 42.3% of the current Etsy sellers have the star seller badge, and on average a seller lists 9 categories of items on its page. Moreover, only 57.4% of the Etsy sellers ship on time, the average rating score is 4.74, and 50% of the sellers on the Etsy website has sold at least an item.
c.	Cleaning
First, we began our analysis by cleaning the initial dataset obtained from the Kaggle website in order to guarantee the precision and dependability of our analysis. We located and removed outliers and duplicates. We then replaced null values with mean values, depending on the condition. For example, if the number of sales was zero, we replaced the null values in the number of reviews and average review score with zero. If the number of sales was missing but there were reviews, we replaced the null values with the mean value of the number of sales. We carried out several data cleaning operations using Python modules like Pandas and NumPy. Additionally, we found that there are many typos and special characters used in city names, so we removed city names and preserved country names for the column “Location”, utilizing the “re” module. 
For web scraped data, we performed numerous steps to clean the data, which was essential as the Etsy web pages contained a lot of noise and inconsistencies. First, we removed HTML tags using the BeautifulSoup library. Then we removed special characters with the “re” module again. Finally, we removed duplicates, outliers and unnecessary information from the data in order to make sure the data is clean and consistent before performing further data analysis.


## Analysis
We first grouped the Kaggle data by seller location, counted the occurrences of each location and sorted the values in descending order. The top 10 countries with the highest number of Etsy shops are depicted in Fig. 6 as a bar plot. As you can see, most of the Etsy shops are based in the United States, followed by England, Canada and Australia, which are all English-speaking countries.


Fig. 6

<img width="263" alt="image" src="https://user-images.githubusercontent.com/88157400/232275935-d1ab505d-a56b-44a3-bce2-4c2fecd967e2.png">

We then created a bar plot to demonstrate which countries the Etsy shops with the highest average sales are located in (Fig. 7). The plot shows that the average sales is the highest in sellers based in China, followed by Ethiopia and Hong Kong. This result indicates that although most of the Etsy shops are based in the United States, they do not make a lot of sales on average. On the other hand, there are not that many Etsy sellers in China, but they make up the largest share of Etsy's merchandise sales.


Fig. 7

<img width="262" alt="image" src="https://user-images.githubusercontent.com/88157400/232275994-1c26a430-65f9-4fff-bfc4-e689137363e0.png">

 
The bar plot in Fig. 8 gives a visual depiction of how many business owners have joined the Etsy community by year. Since the data obtained from Kaggle only has Etsy seller data from Etsy’s creation in 2005 to July of 2019, the 2019 value is incomplete and can be disregarded. The bar plot proves the fact that the number of Etsy sellers is steadily increasing since the e-commerce platform’s establishment in 2005, and this upward trend will continue as the e-commerce industry keeps expanding as a result of the COVID-19 pandemic and Etsy makes it easy for beginner business owners to launch their products and sell online.


Fig. 8

<img width="240" alt="image" src="https://user-images.githubusercontent.com/88157400/232276040-b32acd13-1eab-4836-bdbc-c0bdb207afab.png">

Based on the year that each Etsy shop entered the platform, the bar plot in Fig. 9 illustrates the average sales of those shops. The plot shows that the average sales was the highest in 2007 and has been decreasing since then, indicating that the longer the seller run their businesses on Etsy, the more sales they generate on average. As more business owners join the Etsy community, this may be good news for them as their sales will continue to grow in the long-term.


Fig. 9

<img width="259" alt="image" src="https://user-images.githubusercontent.com/88157400/232276091-20e99e00-21f1-4a05-88ed-51d4451e8aaf.png">


We then created a new column “sold” to identify which seller has sold an item on Etsy, giving 1 if they have sold at least one item and 0 otherwise. The frequency of this binary variable is depicted in Fig. 10. The plot makes it clear that most of the sellers have sold at least one item while there are still many sellers that have yet to sell an item on Etsy.


Fig. 10

<img width="221" alt="image" src="https://user-images.githubusercontent.com/88157400/232276126-39e9e813-a00a-4383-ba42-82e8acc01c1d.png">

 
Fig. 11 presents histograms of Etsy seller data scraped from the current website. The left histogram shows most sellers have average review scores > 4.5, while few have scores < 0.5. The right histogram, logarithmic to show data better, displays most sellers have < 100,000 sales, but some have > 200,000 sales.

  
Fig. 11

<img width="495" alt="image" src="https://user-images.githubusercontent.com/88157400/232276197-58ea983c-3d4b-46af-9a19-fec3e2381297.png">


Before running regression analysis, we performed feature selection to eliminate irrelevant or redundant features that may hurt the accuracy of the models and to improve the model performance, utilizing the ExtraTreesClassifier module in python. The result is visualized in the bar plot shown in Fig. 12 below.


Fig. 12

<img width="270" alt="image" src="https://user-images.githubusercontent.com/88157400/232276251-e7f0cef7-81e8-4cac-90a0-d6d047e76024.png">

The heat map of the correlation matrix is shown in Fig. 13. As the multicollinearity of independent variables negatively affects the accuracy of the regression models, we removed the variables Reply and Shipping as they are highly correlated to the Badge (85% and 68% respectively). Thus, we performed a logistic regression using the 6 independent variables, Admirer, Total Items, Category, Review, Year, and Badge, with Sales as the binary dependent variable.


Fig. 13

<img width="360" alt="image" src="https://user-images.githubusercontent.com/88157400/232276295-e714b45f-6e9f-416f-90f5-4acd9d593c68.png">


Logistic regression results (Fig. 14) show that all independent variables except Review are significant (p-values < 0.001). Fig. 15 reveals that having a star seller badge increases odds of being successful (median/higher sales) by 29.9%, while average review rating of 4.8+ increases odds by 10.7%. Adding a category decreases odds by 6.8%. Admirer, Total Items and Year have odds ratio of 1, indicating little association with Sales.


Fig. 14

<img width="370" alt="image" src="https://user-images.githubusercontent.com/88157400/232276330-b8fb415e-f5cd-4339-9782-247abf49dca0.png">


Fig. 15

![image](https://user-images.githubusercontent.com/88157400/232276399-2f2ccd7c-ce97-40fa-b6be-6276242ab461.png)


Fig. 16 shows the Ordinary Least Squares regression results, predicting Etsy seller sales using independent variables Admirer, Review, Total Items, Year and Badge. R-squared value is 0.515, indicating 51.5% of Sales variation is explained by independent variables. Statistically significant variables with p-values below 0.1 are Admirer, Total Items, Year and Badge. One more admire leads to approximately two more sales, having one more item in the shop leads to approximately 14 more sales; and having a badge of star seller, leads to 1256 more sales. Joining Etsy five years later decrease the number of sales by one unit. Review and constant are not significant but we can talk about their direction and interpret that having a average review rating more than 4.8, the sales number will goes up about 1176 amount

Sales = - 838 + 1.9 Admirer + 1176.6 Review + 13.5 Total Items - 0.8 Year + 1255.6 Badge


Fig. 16

<img width="322" alt="image" src="https://user-images.githubusercontent.com/88157400/232276442-0e375f56-245e-4469-9232-74c12ef0e447.png">


Both of the logistic regression and OLS regression agree that having a certified star seller badge increases the odds and amount of Sales.
Sentiment analysis was performed on Etsy seller announcements to see if positive sentiment correlates with higher sales. Term Frequency-Inverse Document Frequency (TF-IDF) statistic was used to measure word importance in announcements, assuming those with median/higher sales have positive sentiment. The resulting confusion matrix (Fig. 17) showed only 65% accuracy, indicating that sentiment in announcements has little influence on purchasing decisions, and words used are neutral.


Fig. 17

<img width="235" alt="image" src="https://user-images.githubusercontent.com/88157400/232276448-68445e5b-7f1b-438d-ba39-dad8f709af07.png">


Accuracy = 65%
We then created a word cloud to visualize the top 40 words that show up the most in Etsy sellers’ announcements, using the NLTK library. The size of each word is proportional to its frequency, so the bigger the size of the word is, the more frequent that specific word is used. It illustrates that the most frequently used word is Thank, followed by design and Welcome, indicating that most Etsy sellers express gratitude to viewers for visiting their pages in their announcements. Additionally, they often highlight their unique designs to attract more visitors and purchases.


Fig. 18

<img width="215" alt="image" src="https://user-images.githubusercontent.com/88157400/232276456-13afe510-65f7-41ea-afef-16c02811eb62.png">

 
## Conclusion and Recommendation
Based on the analysis and visualizations presented in this project, several key findings have been identified for business owners aiming to launch their online shop, improve their sales and create a successful shop on Etsy’s e-commerce platform.
First, the number of stores joining the Etsy marketplace has been steadily increasing since its launch in 2005, indicating a growing interest in the platform among sellers. However, the average lifetime sales peaked in sellers that joined Etsy in 2007, indicating that Etsy sellers have been able to grow their sales over time. This suggests that persistence and dedication pays off in the long run. Second, the distribution of review ratings and sales for Etsy shops is highly skewed, with a majority of shops having lower sales and higher review scores. This information can be useful for sellers to tailor their marketing tactics to boost sales. Third, our analyses involved running one OLS and one logistic regression model. The result suggests that earning a star seller badge is worth it because it directly relates to higher sales. It is also recommended that Etsy sellers have an average review rating of 4.8 or higher and sell more items on their shop pages to gain median or higher sales. Lastly, although no big difference was found between sellers with large and small sales volumes, we recommend that sellers express gratitude to viewers for visiting their shop on Etsy by writing “Thank you” or “Welcome” on their announcements, as it seems like a common practice on Etsy. Additionally, they can highlight their selling points such as a unique design on their announcements. 
