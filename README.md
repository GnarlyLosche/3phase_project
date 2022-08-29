# 3phase_project
My ML Project Repo for Phase 3

# Project Thesis:

BlackRock is an American multinational investment management corporation based in New York City. Since their founding in 1988, they have become the world's largest asset manager, with US$10 trillion in assets under management as of January 2022.

In 2020, Blackrock’s CEO stunned the business world with his annual letter to investors. He announced his, and the firm's concern about the impact climate change has on companies' long-term prospects.

Since then, Blackrock has started shifting its investment approach to account for climate risk in its investment decisions.

However, it can be very difficult to compare companies across industries, so many fledgling rating agencies have popped up to create a standard approach to quantify a company’s level of responsibility across environmental, social (diversity, equity, inclusion), and governance (responsible leadership/decision-making) concerns. This is known as the ESG efforts/policies of a company.

# Problem:
BlackRock doesn’t want to have to hire one of these standards companies to rate a company every time before they invest, and they don’t have the in-house expertise to build their own ESG metrics or what to evaluate upon. 

# Business Context:
Presenting to Executive Sustainability Staff/CIO on Sustainability recommendations.

# Business Context:
As a member of the big 3, blackrock is one of the largest shareholders in 40% of all publicly listed firms in the United States. As such, they care deeply about the ESG scores for their public holdings, and want to focus on those investments first. They want to know if their existing positions are sound, and if there is a way to scout new public companies to invest in.

# Initial EDA and Data Review:
After initially joining MSCI’s ESG rating data and information on the 2021 Fortune 1000 companies from two separate kaggle Datasets, I Combined the dataframes leaving me with 1089 records for the largest public companies and their ESG scores.

I found that not many features, even after initial engineering, had a strong linear relationship with my target variable of ESG Rating/it's numeric score of ESG Score shown by the correlation matrix below.

![corr_matrix](https://user-images.githubusercontent.com/106346824/187224720-091d68c5-8a63-4224-9d66-6ee4d9e874f6.png)

However, there is a clear relationship once you start to include the numeric variable - as shown below. 

![final_esg_overall](https://user-images.githubusercontent.com/106346824/187224891-cd86cc0d-0d2f-460b-9933-8cf4c4e41707.png)

![final_founder_esg](https://user-images.githubusercontent.com/106346824/187224917-5bc85daa-f253-4d29-b1b3-2cfdfa9afaab.png)


Corporations that still have an initial founder both tend to have a higher valuation, and have better performance on ESG Ratings. This could potentially be due to a stronger sense of ownership/accountability with founders vs hired CEOs. Using the publicly available financial data, and the readily available data on the founder, I had a set of features that appeared to provide a good indicator of ESG Score.

# Modeling

The MSCI rating system breaks down companies into 3 categories, Laggard, Average, and Leader, that can then be broken down further into 6 individual rating levels, shown below. From my initial review, I focused on classifying the 3 high level categories instead of all six in order to provide a strong model based on available data.

![Screen Shot 2022-08-25 at 11 04 02 AM](https://user-images.githubusercontent.com/106346824/187225699-fe7a79e2-f1b3-4a01-aebd-e0f3d684741f.png)

MSCI ESG Ratings evaluate upon 4 important areas:
 1. What are the most significant ESG risks and opportunities?
 2. How exposed is the company to risk?
 3. How does it manage risk? 
 4.How does it compare to its peers?


I built 6 different classification models that took in the below features to then classify a company based on its:
 1.'revenue'
 2.'profit'
 3.'num_of_employees'
 4. 'sector'
 5. 'subsector'
 6. 'state'
 7. 'newcomer'
 8. 'ceo_founder'
 9. 'ceo_woman'
 10. 'profitable'
 11. 'market_cap'

Ultimately my models were able to provide the below scores prior to parameter tuning:

Dummy Results:
 accuracy - 0.5506493506493506 
 precision - 0.5512701932214128 
 recall - 0.5506493506493506 
 F1 Score - 0.550943945958487 

Decision Tree Results:
 accuracy - 0.6441558441558441 
 precision - 0.6130334928229665 
 recall - 0.6441558441558441 
 F1 Score - 0.6242471409758287 

KNN Results:
 accuracy - 0.6987012987012987 
 precision - 0.6108540870893813 
 recall - 0.6987012987012987 
 F1 Score - 0.6336692825361651 
        
Random Forest Results:
 accuracy - 0.6987012987012987 
 precision - 0.6013952989159601 
 recall - 0.6987012987012987 
 F1 Score - 0.6171624601813281 

Gradient Boosting Data Results:
 accuracy - 0.6805194805194805 
 precision - 0.5893080783408092 
 recall - 0.6805194805194805 
 F1 Score - 0.6071327362146494 

XGBoost Results:
 accuracy - 0.6519480519480519 
 precision - 0.5803324277037311 
 recall - 0.6519480519480519 
 F1 Score - 0.6043034651299114 
        
AdaBoost Results:
 accuracy - 0.6675324675324675 
 precision - 0.5653480045410881 
 recall - 0.6675324675324675 
 F1 Score - 0.6013489736070381 

Ultimately, using XGBoost and parameter tuning via gridsearch, my precision and accuracy landed at 76%.

# Second order considerations (modeling)
While I ultimately built a strong model to understand total ESG Score, I did want to better understand how well I wass able to classify a model individually upon E, S, and G concerns since my project was focused specifically on environmental concerns. I built new target variable columns that binary classified whether a company was above or below the median E, S and G score for the dataset, and then ran the model pipeline for each of them.

My best model was a random forest classifier, that had 72% accuracy at correctly classifying whether a company would be above or below the median score - using both the high level ESG XGBoost model, and the Environmental random forest, I can provide an overall performance predictor, and specific environmental classifier with strong accuracy.

# Conclusion
To Conclude, different models work better depending on the given target - E, S, or G. Additionally these models will work better or worse depending on the complexity of the target, and access to extra ESG Data is valuable and improves classification performance, and as is the goal of blackrock, these existing metrics are effective at classifying Environmental performance, in addition to overall performance.

As a few recommendations, consider partnering with a rating company like MSCI, and in regards to your investment strategy, focus on financials first, and then on the qualities present in the leadership team. 

If we keep working together, I would love to gather additional data, compare this models capabilities on another rating agencies standard, and better understand how ESG investing impacts returns.
