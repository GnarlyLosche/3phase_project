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

![Correlation Matrix](http://lmsotfy.com/so.png](https://drive.google.com/file/d/1_o5ziRZBE88hkAR1bytcgu66dxMN9Yqr/view?usp=sharing)
