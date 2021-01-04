# Time is Money

As said by probably somebody's dad.
> Time is money.


This is a fairly common saying, so the I decided to explore it a little further and give it a bit more quantitative meaning. 

Wages are defined by amount of money per hour. Unfortunately, money has slightly different values depending on where you are located in the US. A wage of $25/hour in San Francisco, CA is not worth the same amount as a wage of $25/hour in Dallas, TX. However, 60 seconds in San Francisco, CA is 1 minute, and this holds true for Dallas, TX as well. So the goal for this project was to try to convert the value of a dollar into minutes. In other words, see how many minutes of someones time is worth a dollar.

With the basic idea in mind, I began to determine what sort of data was needed to try and perform this conversion. My thought process was to look at the county-level data of the US and use this data for my calcuations. After some investigative efforts, it became apparent to me that there was a large number factors that go into defining the worth of a dollar, specifically: finding the data, checking the accuracy of the data, and deciding how specific or broad I wanted the analysis to be. In the end, I decided on taking the per capita income of each county in the US and determining the cost of living as a sum of housing costs, federal and state taxes, medical costs, and food costs. Cost of living was based on a single individual and taxes were calculated for someone filing as single, taking no deductions. Also, Alaska and Hawaii were excluded from this project because some of the data sources did not include them.

I tried to only use data from government sites as these seemed to be the most reputable and complete.

Sources for the data:
- per capita income by county - [bea](https://www.bea.gov/data/income-saving/personal-income-county-metro-and-other-areas)
- meal cost by county - [feeding america](http://map.feedingamerica.org/)
- housing cost by county - [huduser](https://www.huduser.gov/portal/datasets/fmr.html#2020_data)
- medical cost by county - [cms](https://www.cms.gov/Research-Statistics-Data-and-Systems/Statistics-Trends-and-Reports/Medicare-Geographic-Variation/GV_PUF)

Calculations performed for cost of living data:
- federal and state taxes were calculated using the 2020 tax brackets
- food cost was calculated by assuming 3 meals a day for 365 days

`food_cost = meal_cost * 3 * 365`

- housing cost was calculated by averaging 1 and 2 bedroom prices and assuming a 12 month lease

`housing_cost = average(one_bedroom + two_bedroom) * 12`

The calculation performed for the conversion:
- covnvert annual per capita income to hourly assuming 40 hour work weeks

`hourly_income = per_capita_income / 2080`

- hours it takes to make cost of living based on per capita income

`hours = cost_of_living / hourly_income`

- convert hours to minutes

`minutes = hours * 60`

- generate the dollar to time converted value

`dollar_time_value = minutes / cost_of_living`


This was a simple project out of curiosity and fun and although the data is real, there are so many unconsidered factors in my analysis that I would not consider the results accurate by any means. That being said, there were some interesting trends depicted by the results and the dollar to minutes values seemed to be consistent with being higher for more poverty stricken counties. Overall it was an interesting project and plugging the data into Tableau yielded some nice visuals to explore the results.
