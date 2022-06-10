# Kickstarting with Excel

## Overview of Project
The client, Louise, is an up-and-coming playwright who is looking to crowdfund her play *Fever*. Her current fundraising goal is $12,000.
### Purpose
I will be using Kickstarter campaign data to determine how different theater campaigns fared in relation to their launch dates and funding goals. I will then apply these insights to the client's campaign so that they may mirror successful Kickstarter campaigns in the same category.

## Analysis and Challenges
### Analysis of Outcomes Based on Launch Date
I first created a pivot table from the Kickstarter data that would organize theater campaign outcomes based on the launch date. The table is filtered by parent category (theater) and years, groups campaign launch dates by month, and counts the campaign outcome (successful, failed, or canceled) for each month. I then created a line chart from the pivot table to visualize the relationship between outcomes and launch month.
![Theater_Outcomes_vs_Launch](https://github.com/mschimmy/kickstarter-analysis/blob/Resources/Theater_Outcomes_vs_Launch.png?raw=true)
In our dataset, there are 1,369 theater campaigns and 839 of them were successful, giving a 61% success rate. When we compare the outcomes of theater campaigns based on launch month, we can see that more campaigns were launched between May and July than in other months, with most campaigns being launched in May. May also has the highest number of successful campaigns with a success rate of 67%. December has the least number of successful campaigns with a success rate of 49%.

### Analysis of Outcomes Based on Goals
I created a table using the COUNTIFS() function to calculate the number of successful, failed, and canceled theater campaigns by funding goal range. Using this information, I then calculated the percentage of successful, failed, and canceled projects for each funding goal range, and created a line chart to visualize the relationship between the goal-amount ranges and the percentage of successful, failed, or canceled projects. 
![Outcomes_vs_Goals](https://github.com/mschimmy/kickstarter-analysis/blob/Resources/Outcomes_vs_Goals.png?raw=true)
Generally, failed Kickstarter campaigns have higher fundraising goals than successful Kickstarter campaigns, with the likelihood of having a successful campaign tapering off at the $15,000 to $19,999 fundraising goal (50% chance of success). The exceptions to this trend are campaigns with a fundraising goal of $35,000 to $39,999. But it is important to note that the number of campaigns in this range is much lower than the number of campaigns with a fundraising goal of less than $20,000 (9:985). Theater campaigns with a fundraising goal of less than $1,000 or $1,000 to $4,999 were the most successful with a success rate of 76% and 73% respectively. The least successful campaigns were those with a fundraising goal of $45,000 to $49,999.

### Challenges and Difficulties Encountered
I encountered some challenges when populating the table used to compare campaign outcomes based on goals. I did not know how to format the different ranges of campaign goals. Initially, for cell B3 I had `=COUNTIFS(Kickstarter!F:F,”successful”,Kickstarter!D:D,”1000<4999”)` and Excel returned an error. I decided to break up the funding goal ranges in my formula and added a third criteria to filter by the subcategory “plays”, `=COUNTIFS(Kickstarter!D:D,”>=1000”,Kickstarter!D:D,”<=4999”,Kickstarter!F:F”successful”,Kickstarter!R:R,”plays”)`. I then had an issue with the pulled columns changing as I applied the formula to other cells. To solve this I locked the columns in the formula and filtered the data for the appropriate goal range and outcome: `=COUNTIFS(Kickstarter!$D:$D,”>=1000”,Kickstarter!$D:$D,”<=4999”,Kickstarter!$F:$F”successful”,Kickstarter!R:R,”plays”)`. 

## Results
- What are two conclusions you can draw about the Outcomes based on Launch Date?
  - Louise has the highest chance of having a successful campaign if she launches in May.
  - Louise has the lowest chance of having a successful campaign if she launches in December. This could possibly be due to the number of holidays that occur during the end of the year, backers may be less likely to donate to Kickstarter campaigns as they are saving their money to spend on holiday activities.

- What can you conclude about the Outcomes based on Goals?
  - With their current budget of $12,000, Louise has a 54% chance of having a successful campaign. If they were to decrease their fundraising goal to less than $5,000 their chances of having a successful campaign would increase to 73-76%, approximately 20%.

- What are some limitations of this dataset?
  - A limitation of this dataset is that it does not give context to the methods used to crowdfund the campaign. Different campaigns will have different methods of fundraising and this information could be relevant to the success or failure of the campaign. For example, campaigns that use advertising to raise money for their campaign may have more success than campaigns that do not, this could be a useful insight for Louise’s campaign.
  - This dataset does not include data on individual donations to a campaign. This information could be useful and provide insight into the donation habits and trends of backers.

- What are some other possible tables and/or graphs that we could create?
  - We could create a box plot to illustrate the variance of our dataset and if there are any outliers. If there are we could remove these outliers and further analyze our data and see the new story it’s telling. One area where there might be an outlier that is skewing the data is the funding goal, there is one theatre campaign with a fundraising goal of $200,000. By removing this data point we can get a better understanding of the distribution of successful campaigns by funding goal.
  - We could also look at the distribution of successful campaigns by their launch date and whether those dates were in the beginning of the month (day 1 to day 10), the middle of the month (day 11 to day 20), or the end of the month (day 21 to day 31). This could provide insight into when in May Louise should start her fundraising campaign.
