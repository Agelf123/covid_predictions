Predicting Covid Hotspots

By: 

Aryeh Gelfand(https://git.generalassemb.ly/aryehgelfand)
Jordan Weiss(https://git.generalassemb.ly/weisja4/)
Brandon Greenspan(https://git.generalassemb.ly/bgreenspan)

The Problem:

Our client wants to try to predict COVID-19 hotspots based on demographics and has asked us to build a predictive model that could predict if a county is a COVID-19 hotspot. Since we are cautious about trying to predict an ongoing problem with many changes in real-time data, we informed that if our models don't meet a .95 accuracy score or better that they should only use the model for interpretive purposes and not predictive purposes. While the client understands the low likelihood of building a predictive model under this criteria, they gave us the budget to proceed anyway.
We defined a "COVID-19 hotspot" as a county in the contiguous US that has a rate of infected residents per capita that is higher than one standard deviation for the mean. This actually presents an interesting situation where we already know that our baseline model will have an accuracy rate of .7625. Due to this, we will only consider our model interpretable if we can beat the baseline accuracy.
We are viewing this as a classification problem and will look to run Logistic Regression, KNN, Support Vector Machine, Decision Tree Classifier, Bagging Classifier,Random Forest, and AdaBoost models in order to see if it's possible to predict COVID-19 hotspots based on county demographic data.
To reiterate, our goal for the model to be considered predictive is a .95 accuracy score or better, and our goal for the model to be considered interpretable is a .7626 accuracy score or better. This is to ensure that we are held to high standards when it comes to predicting an ongoing pandemic, but also ensures that we can interpret the findings if we are performing better than average.


Executive Summary

Since our difficult goal is to predict COIVD-19 hotspots with 95% accuracy, we needed verifiable data that can give proper demographics for every county in the contiguous United States.  The first step was to collect expansive data from the Census Bureau, the Health Department, and covidtracking.com.  While we gathered a lot of good data, it also meant that the data required a lot of cleaning because we had over 900 columns worth of data for every single county in the US as well as territories (please see separate cleaning notebooks for cleaning code).  Since this an ongoing issue with new data coming in every minute, our cdata collection cutoff was May 8th.  Some of these categories included health resources like hospital beds, doctors, nurses, etc, all divided by county because we want to understand if certain factors could factor into a predictive model.
Since the model called for a threshold that determined a "hotspot" or "not a hotspot," we recognized that this was a classification problem from the start.  Our determined threshold was that anything greater than one standard deviation above the mean in terms of COVID-19 cases per capita would be classified as a "hotspot."  This interestingly gave us a baseline score right away of .7625 (which would be the accuracy if the model guessed that every single county was not a hotspot).
In addition to the baseline, we utilized a logistic regression twice (the first time to inform us on how to eliminate irrelevant features).  Afterwards we ran seven other classification models to see if we can meet our threshold of 95% or better for predictive purposes.  If that threshold is not reached, then we will look to interpret the model only if it can still score better than the baseline in terms of accuracy.
If we are able to interpret our model, we will look at the confusion matrix in order to investigate the predictive strength and weaknesses of the model.  Afterwards, we would look to evaluate coefficients to see if any key demographic data could help indicate COVID-19 hotspots.
Regardless of any findings, we do continue to urge that readers continue to follow CDC and WHO guidelines to help limit the spread of COVID-19.  This is expecially important if our model does not meet the predictive threshold (which is very likely) because that would show that COVID-19 can strike in any county, regardless of demographics.
Lastly, we did make an interractive Bokeh map in order to display our findings and track growth rates for COVID-19.

Conclusions and Recommendations

Our chosen Logistic Regression model scored 0.8121 on accuracy, which means that while it failed to meet our goal of .95 in order to fulfill its usage as a predictive model.  However, the model did surpass the accuracy score of .7625 that allows us to interpret coefficients and further investigate potential COVID-19 hotspots.
We do want to stress that on areas of actual COVID-19 hotspots, the model did not do a good job at predicting COVID-19 hotspots.  Our clients should not make any actionable decisions based on the model other than further research into some of the possible correlated features, like the high ratio of men to women over 18 being more prevalent in COVID-19 hotspots.
The path of the pandemic continues to evolve and it is likely that we will continue to see growth in new and unexpected ways. The general consensus is that there are no definitive ways to determine where the next hotspot will be, so all Americans (and indeed all people) should take the necessary precautions to mitigate the spread of COVID-19. As the virus continues, we should regularly re-evaluate that data and continue to search for patterns and insight to learn more about this deadly menace. 

Data Dictionary

https://docs.google.com/spreadsheets/d/1UeFfRlj8biufcOLuonWuuJXy9O6BT_SceWJ06Flj4Ik/edit#gid=0

References

- http://data.gov/
- https://www.bls.gov/developers/api_python.htm#python2
- https://covidtracking.com/api
- http://census.gov/
- http://docs.bokeh.org/en/0.11.0/docs/gallery/choropleth.
- https://towardsdatascience.com/walkthrough-mapping-basics-with-bokeh-and-geopandas-in-python-43f40aa5b7e9
- https://docs.bokeh.org/en/latest/docs/user_guide/plotting.html
- https://communityimpact.com/nashville/southwest-nashville/coronavirus/2020/05/01/large-spike-in-coronavirus-cases-traced-to-prison-in-trousdale-county/
- https://ncdp.columbia.edu/library/mapsmapping-projects/us-natural-hazards-index/
