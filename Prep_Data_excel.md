# Cleaning Data.

692 stations in Chicago city data, the main goal here is to analyse the first month of the data in Excel: cleaning, preparing and analysing a single part to understand the data. 
At the end of the analysis, we going to learn how to use Advance Excel formulas, understand how the data is structured and resolve a couple of questions.

What type of customer do we have?

What day of the week do customers tend to use the service?

What type of bicycles customers are using? 


# About the data.

A bike-share program that features more than 5,800 bicycles and 600 docking stations. Cyclistic sets itself
apart by also offering reclining bikes, hand tricycles, and cargo bikes, making bike-share more inclusive to people with
disabilities and riders who can’t use a standard two-wheeled bike. The majority of riders opt for traditional bikes; about
8% of riders use the assistive options. Cyclistic users are more likely to ride for leisure, but about 30% use them to
commute to work each day.(Note: The datasets have a different name because Cyclistic is a fictional company. For the purposes of this case study.The data has been made available by Motivate International Inc. under this [License] (https://ride.divvybikes.com/data-license-agreement).)

This is the 1/12 data set from year 2021.
[202101-divvy-tripdata - Copy.csv](https://github.com/MiguelAAP90/Excel-_cleaning_data/files/7877654/202101-divvy-tripdata.-.Copy.csv)

![Screenshot 2022-01-16 192528](https://user-images.githubusercontent.com/60878213/149674768-d91991f0-a7f2-4e7c-9cec-e848022764e9.png)

As we can see we have 13 columns and around 95000 rows, after analysing we have to clean the data and check formats:
														
				Changed A,B,E,G,M columns to Text format: format > cells > Text
				Changed C,D, columns to Time format: format > cells > Time
				Changed F,H,I,L columns to int format: format > cells > Number(no decimals)
				Changed J,L columns to Float format: format > cells > Number(10 decimal)


# Split text and numbers.

In column F "start_station_id" and H "end_station_id" a couple of IDs are not consistent as some are mixed with letters, after research, I found out that it's a data mistake and need to sort.  
		![Screenshot 2022-01-16 194828](https://user-images.githubusercontent.com/60878213/149675510-7d77c0a2-8561-4d60-8d56-d1a9640bb437.png)

First I would create 2 extra columns beside F  to performance the next code.

1.-Find the index where the first number from the cell is positioned.in other words for example from "KA1504000117" we want to know where the first number "1" [left to right] is positioned, from that number the number "1" is on array index 3. to do this automatic.
Creat a new colum and place the formula.


	=MIN(FIND({0,1,2,3,4,5,6,7,8,9},F2&"0123456789"))

FIND function locate the starting position of the number. For the find_text, we are using the array constant {0,1,2,3,4,5,6,7,8,9}, which causes the FIND function to perform a separate search for each value in the array constant. Since the array constant contains 10 numbers, the result will be an array with 10 values.
MIN function returns the smallest value in the list, which corresponds to the position of the first number that appears in the original text. In essence, the FIND function gets all number positions, and MIN gives us the first number position.

	F2&"0123456789"

This part of the formula concatenates every possible number 0-9 with the original text in F2. Unfortunately, FIND doesn't return zero when a value isn't found, so this is just a clever way to avoid errors that could occur when a number isn't found.

2.- After when we have the array index, we can separate the text from the number, in this case we just want the number and no longer need the text so we just extract this.
again we creat a second column biside G.to do this automatic.
Creat a new colum and place the formula.

	=RIGHT(F2,LEN(F2)-G2+1)
	
Right would select from right to left  by the lend of F cell and substract the len of G (text + 1) to get the total of values in F.
		
![extract ](https://user-images.githubusercontent.com/60878213/149676911-e37de356-cf7c-45a2-ab1d-aa7d67d2e4fa.png)

we repeat the same process with column H.

# Calculate the time bike was use
Column C contains the date and time of when the ride started and D contains the date and time of when the same bike ends the ride. 
To calculate the total time of use we create a new column and place the formula.

	=D2-C2
This simple would give us the total time of use.
It is important to put this last column in time format "HH:MM:SS"

# Day of the Week 
One more thing I want to do is to see the day of the week the bike was taken.

	=WEEKDAY(C2)
This would give us a number from 1 to 7, where 1=Monday,2=Tuesday....etc.etc.etc 

![time_day](https://user-images.githubusercontent.com/60878213/149677692-0b5792d3-4f80-4b26-bb4d-47579f688b97.png)

# Removing unnessesary data.

Removing unnecessary data
When we calculate the time of use, we notice that a couple of the data is less than a minute of use, and most of them have the same station value “start_station_name” and “end_station_name”. For the analysis of this data, we going to consider a length of time of no less than a 1 minute to reduce the data error of a customer taking a bike and placed back by mistake in the same station, reducing the duplicates. 
![removing_data](https://user-images.githubusercontent.com/60878213/149733633-b43958cb-29c6-4b4d-9343-d62173824440.png)

This is  simple as filtering with conditional, where ride_length is less than "00:01:00", and remove rows.

	Filter > number filters > Less than..> range. 

### We can continue cleaning this single data set but for the analysis of this we have what we need, and now  we can start answering some questions and see some relevant  numbers.

https://github.com/MiguelAAP90/Data_analysis_with_Excel/blob/main/Using_data_with_Excel.md

