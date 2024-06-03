# Revenue_insights
Data Analytics project - Hospitality Domain

### Project Overview
This data analytics project focuses on uncovering revenue insights within the hospitality domain of Atliq Grands by analyzing booking patterns, customer demographics, and seasonal trends. By leveraging advanced analytics techniques, the project aims to identify key drivers of revenue growth and optimize pricing strategies.  The ultimate goal is to provide actionable insights that can drive profitability and operational efficiency in the hospitality industry.
### Data Sources
Data: The primary dataset used for this analysis is the "input-files-1.zip" file, containing detailed information about each sale made by the company.
### Tools
1. Excel - Data Cleaning
1. PowerBI - Creating reports

## Data Analysis using Power BI
### DAX Queries

1. Revenue:	To get the total revenue_realized [Revenue = SUM(fact_bookings[revenue_realized])]
2. Total Bookings:	To get the total number of bookings happened	[Total Bookings = COUNT(fact_bookings[booking_id])]
3. Total Capacity:	To get the total capacity of rooms present in hotels	[Total Capacity = SUM(fact_aggregated_bookings[capacity])]
4. Total Succesful Bookings:	To get the total succesful bookings happened for all hotels	[Total Succesful Bookings = SUM(fact_aggregated_bookings[successful_bookings])]
5. Occupancy %:	"Occupancy means total successful bookings happened to the 
 total rooms available(capacity)"	[Occupancy % = DIVIDE([Total Succesful Bookings],[Total Capacity],0)]
6. Average Rating:	Get the average ratings given by the customers	[Average Rating = AVERAGE(fact_bookings[ratings_given])]
7. No of days:	"To get the total number of days present in the data. In our case, we have data from May to July. So 92 days."
   [No of days = DATEDIFF(MIN(dim_date[date]),MAX(dim_date[date]),DAY) +1]
1. ADR: 	"Calculate the ADR(Average Daily rate)
It is the ratio of revenue to the total rooms booked/sold and It is the measure of the average paid for rooms sold in a given time period"	[ADR = DIVIDE( [Revenue], [Total Bookings],0)]
1. Total no show bookings:	"To get the""No Show"" bookings out of all Total bookings happened (""No show"" means those customers who neither cancelled nor attend to their booked rooms)"	[Total no show bookings = CALCULATE([Total Bookings],fact_bookings[booking_status]="No Show")]
1. No Show rate %:	calculating the no show percentage.	[No Show rate % = DIVIDE([Total no show bookings],[Total Bookings])]

1. Realisation %	: "calculate  the realisation percentage.It is nothing but the succesful ""checked out"" percentage over all bookings happened."	[Realisation % = 1- ([Cancellation %]+[No Show rate %])]
1. RevPAR:	"Calculate the RevPAR(Revenue Per Available Room) RevPAR represents the revenue generated per available room, whether or not they are occupied. RevPAR helps hotels measure their revenue generating performance to accurately price rooms. RevPAR can help hotels measure themselves against other properties or brands."	[RevPAR = DIVIDE([Revenue],[Total Capacity])]

1. DSRN: "calculate DSRN(Daily Sellable Room Nights) This metrics tells on average how many rooms are ready to sell for a day considering a time period"	[DSRN = DIVIDE([Total Capacity], [No of days])]
