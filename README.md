#Cleaning Data and first step analysis.

692 stations in Chicago city data, the main goal here is to analyse the first month of the data in Excel: cleaning, preparing and analysing a single part to understand the data. 
At the end of the analysis, we going to learn how to use Advance Excel formulas, understand how the data is structured and resolve a couple of questions.

What type of customer do we have?

What day of the week do customers tend to use the service?

What type of bicycles customers are using? 


#About the data:

A bike-share program that features more than 5,800 bicycles and 600 docking stations. Cyclistic sets itself
apart by also offering reclining bikes, hand tricycles, and cargo bikes, making bike-share more inclusive to people with
disabilities and riders who can’t use a standard two-wheeled bike. The majority of riders opt for traditional bikes; about
8% of riders use the assistive options. Cyclistic users are more likely to ride for leisure, but about 30% use them to
commute to work each day.(Note: The datasets have a different name because Cyclistic is a fictional company. For the purposes of this case study.The data has been made available by Motivate International Inc. under this [License] (https://ride.divvybikes.com/data-license-agreement).)

This is the 1/12 data set from year 2021
[202101-divvy-tripdata - Copy.csv](https://github.com/MiguelAAP90/Excel-_cleaning_data/files/7877654/202101-divvy-tripdata.-.Copy.csv)

![Screenshot 2022-01-16 192528](https://user-images.githubusercontent.com/60878213/149674768-d91991f0-a7f2-4e7c-9cec-e848022764e9.png)

As we can see we have 13 columns and around 95000 rows, after analysing we have to clean the data and check formats:
														
				Changed A,B,E,G,M columns to Text format: format > cells > Text
				Changed C,D, columns to Time format: format > cells > Time
				Changed F,H,I,L columns to int format: format > cells > Number(no decimals)
				Changed J,L columns to Float format: format > cells > Number(10 decimal)


##In column F "start_station_id" and H "end_station_id" a couple of IDs are not consistent as some are mixed with letters, after research, I found out that it's a data mistake and need to sort.  
![Screenshot 2022-01-16 194828](https://user-images.githubusercontent.com/60878213/149675510-7d77c0a2-8561-4d60-8d56-d1a9640bb437.png)

