# A_NUMBERS_GAME
Miami Herald Project: A Numbers Game
Email us with questions or comments about our data and methodology. 
Sarah Blaskey, sblaskey@miamiherald.com 
Nicholas Nehamas, nnehamas@miamiherald.com 

‘A NUMBERS GAME’ METHODOLOGY 
Miami Herald analysis of Florida COVID-19 data
DATA SOURCES

The Herald used “Case Line” data published daily by the Florida Department of Health. The Case Line data were used to create the first chart, which visualizes cases by “Event Date,” the day a person who tested positive began to show symptoms. Case Line data were also used to perform an analysis on new cases by day. The analysis was performed on “Case Date,” the date that DOH received the positive test results.

The Herald analysis also used three non-public data sets on individuals tested, individuals who tested positive, and total tests administered. These data, which contain information through May 13, were exclusively obtained by the Herald and were used to do an independent analysis of positivity shown in the second chart. 

The state’s public summary documents were used to perform an analysis on positivity ant testing after May 13. These same methodologies for looking at trends were applied.

BASIC ANALYSIS

The Centers for Disease Control and Prevention’s non-binding guidelines say that a region should see a two-week period of decline in either positivity rate or new cases before reopening. When positivity is used as the basis for reopening, the guidelines state that there must be even or increasing testing over the same period, and a consecutive increase of positivity over two-three consecutive days within that 14-day period could disqualify the region from reopening. When new cases are used as a basis for reopening, the guidelines state that increases in new cases over a consecutive five days within that 14-day period could disqualify the region from reopening based on that criteria. 

The CDC uses three-day averages and cubic smoothing to determine trends and states that the methodology should be applied locally, at a county level or smaller.

The Herald analysis was based conceptually on the CDC guidelines, but uses three-day rolling averages and linear regression lines to look at trends within a two-week period. For the purposes of this story, the Herald’s analysis was applied to broad regions (not county by county) and therefore should not be considered an exact replica of a CDC analysis. Furthermore, the Herald analysis does not account for the correlation coefficient. Accuracy of the trend will differ for each two-week period.

The analysis of new cases was performed using a three-day rolling average of new cases by case date. The three-day average is the mean of new cases on a single day, and new cases from the two previous days. Three-day averages were used to smooth these data, which otherwise tend to spike and dip. The Herald applied a trend line to 14-day chunks of data and used the slope of that line to analyze whether the trend in new cases was positive or negative over that period of time. (A positive slope indicates a general increase in new cases over that two-week period.) 

Positivity rate was independently calculated by the Herald by taking the number of individuals who tested positive for the first time on a given day, over the total individuals who tested positive or negative for the first time on that same day. The Herald graphed three-day rolling averages of positivity, calculated by taking the mean of the positivity rate of a single day and the two previous days. The Herald then applied a trend line to 14-day chunks of data and used the slope of that line to analyze whether the trend in positivity rate was up or down. (A positive slope indicates a general increase in positivity over that two-week period.) 


ANALYSIS SPECIFICS
NEW CASES 
DATA SOURCE
Case Line data published by DOH on June 10, 2020.

DEFINITIONS
	
“NEW CASES” 
The rolling three-day mean of new cases, on date of report.
Three-day mean is calculated by taking new cases on that day, plus new cases the previous day, plus new cases the day before that and dividing by three. 
These data are through June 6.
Spike
Consecutive increase in new cases (three-day) average within five day period
“SPIKE” is defined as
 New Cases > New Cases the previous day 
AND New Cases the previous day  > New Cases the day before that 
AND New Cases the day before that > New Cases the day before that 
AND New Cases the day before that > New Cases the day before that 
AND New Cases the day before that > New Cases the day before that 
14-day period
Day 14 of a fourteen-day period is the date
Day one of a fourteen-day period is 13 days prior to the date

REOPENING CRITERIA & ANALYSIS
Meets_criteria1
A 14-day period where new cases on day 14 are lower than new cases on day 1

Meets_criteria2
the overall trajectory of new cases is “downward” 

Meets_criteria3
14-day period does not include a spike

 Can_reopen
“Y” means that 
Meets_criteria1 = “Y” 
AND Meets_criteria2 = “Y” 
AND Meets_criteria3 = “Y”



POSITIVITY RATE
DATA SOURCE
DOH: Internal DOH data (good through May 13) on all individuals tested, both positive and negative.
TEST DATA: internal testing data on all positive individuals. Includes dates of first negative results and first positive. (Good through May 16)


DEFINITIONS
	
“Individuals” are unique Case.IDs, which refer to the same person in both DOH and TEST DATA.
Positivity Rate
Defined as all positive individuals divided by total individuals tested positive and negative on a given day. (Inconclusives are filtered out)
Positives are unique individuals defined Dx.status = “Confirmed” in DOH.
Date of positive test is the Date.became.case in DOH, which is the date the positive test result was received by DOH.
Negatives are unique individuals where Dx.status = “Not a Case” in DOH OR defined Dx.status = “Confirmed” where earliest.lab.event.date.not.positive for that individual in TEST DATA is earlier than Date.became.case.
There is no overlap between these two subsets of data. Meaning a single person is counted negative only once, on the date the negative test result is received by DOH
A person who was first entered into the system as negative, and then later tested positive would be counted twice. Once as a negative on earliest.lab.event.date.not.positive date in TEST DATA, and again as a positive on Date.became.case DOH.
Testing
Total_tests 
The total positive and negative individuals on a given day (as defined above)
Tests_three_day_mean
The sum of Total_tests, Total_tests the previous day, and Total_tests the day before that divided by three
three_day_percent_positive
Takes the sum of the positivity rate of a given day, the positivity rate of the previous day and the positivity rate day before that, then divides that total by three
Spike
A spike is three or four days of consecutive even or increasing  three_day_percent_positive
“SPIKE” is defined as
 Mean positivity (three_day_percent_positive) >=  Mean positivity the previous day (three_day_percent_positive, lag 1) 
AND  Mean positivity the previous day (three_day_percent_positive, lag 1)  >=  Mean positivity the day before that (three_day_percent_positive, lag 2 ) 
AND  Mean positivity the day before that (three_day_percent_positive, lag 2 ) >  Mean positivity the day before that (three_day_percent_positive, lag 3 )  
AND  Mean positivity the day before that (three_day_percent_positive, lag 3 )  >  Mean positivity the day before that (three_day_percent_positive, lag 4 )
MAYBE  Mean positivity the day before that (three_day_percent_positive, lag 4 )  >  Mean positivity the day before that (three_day_percent_positive, lag 5 )

14-day period
Day 14 of a fourteen-day period is the date
Day 1 of a fourteen-day period is 13 days prior to the date
REOPENING CRITERIA & ANALYSIS

Criteria 1: A 14-day period where positivity on day 14 is lower than positivity on day 1 
Last_lower_than_first
Three_day_percent_positive < three_day_percent_positive at the beginning of the 14 day period(13 days prior), IF true, then “Y” otherwise “N”
Criteria 2: overall positivity trajectory is “downward” 
Meets_trajectory_criteria
A linear trend line for Three_day_percent_positive and the Three_day_percent_positive for the previous 13 days has a negative slope, IF TRUE, “Y” otherwise “N”
Criteria 3: Testing is increasing or even
Meets_testing_criteria
A linear trend line for Tests_three_day_mean and the Tests_three_day_mean for the previous 13 days has a positive or zero slope, IF TRUE, “Y” otherwise “N”
Criteria 4: positivity does not increase for more than two to three consecutive days
Spike_criteria
14-day period does not include a spike
There is no spike on that day, or any of the 10 days prior. If TRUE, “Y” otherwise “N”
Can_reopen
“Y” means that 
Last_lower_than_first = “Y” 
AND Meets_trajectory_criteria = “Y” 
AND Meets_testing_criteria = “Y”
AND Spike_criteria = “Y”

LARGE BATCHES REMOVED
DATA SOURCE
DOH: Internal DOH data (good through May 13) on all individuals tested, both positive and negative.
TEST DATA: internal testing data on all positive individuals. Includes dates of first negative results and first positive. (Good through May 16)

Analysis for positivity and new cases was rerun after batches of more than 20 tests positive or negative from a particular address on a single day 
