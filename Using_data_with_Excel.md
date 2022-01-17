# Playing with Data
After we get acquainted with the database and make some changes, we want to start to see some insights.

About the Data and The cleaning process. 
https://github.com/MiguelAAP90/Excel-_cleaning_data/blob/main/Prep_Data_excel.md.


# separet data.
From the full Sheet of our data  we going to work this time just with four columns "rideable_type,	member_casual,	ride_length,	Week_day", 
this with the objective of answearing our principal questions.

What type of customer do we have?

What day of the week do customers tend to use the service?

What type of bicycles customers are using?


![Small_data](https://user-images.githubusercontent.com/60878213/149678672-06852ba4-7102-445f-8467-1d59f74e7a83.png)


# What type of customer do we have?
from our new Dataset, we can see that there are two types of customers, "members" and "casual", after researching the data we know that pricing plans: single-ride passes,
full-day passes and annual memberships. Customers who purchase single-ride or full-day passes are referred to as casual riders. Customers
who purchase annual memberships are Cyclistic members.

To get the total of each type we performance the next function.

	=COUNTIF(B1:B96835,F53)
	and 
	=COUNTIF(B1:B96835,F54)

This function basically, gets a range of data member_casual = “B1:B96835”, and counts the number of times the argument F53=“members” and f54=” casual” appears in that range,
This would give us the total of Members and total of Casual in our data set. 

![type of customers ](https://user-images.githubusercontent.com/60878213/149678979-4b84bcb0-36cc-462c-b0a8-b1a13327356e.png)

Is Clear that most of our customers are Members representing 81% of our data, something to keep in mind. This is January 2021, a question that comes across for future exploration
is to see if these numbers would be different by the middle of the year or even the end of the year when people are less proactive as is the beginning of the year,
the hypothesis is that customers tend to pay the membership to do more exercise as proposed of a new year. But this is a question to answer some other day.

![image](https://user-images.githubusercontent.com/60878213/149680795-a9f3fc79-f2eb-4412-acd3-1ddd2f22df6a.png)



# Day of the week
Remember that we change the day of the week previously and now, our column of days are numbered from 1 to 7, where 1=Monday,2=Tuesday....etc.etc.etc
To get the correct value we have a couple of options, I chose to continue using the function.
		
	=Countif()
	
In this case, we create a table with numbers from 1 to 7 and the name of the Days,to get the total number of bikes used per day during the month of January 2021.
	
	=COUNTIF($D$2:$D$96835,F2)

where $D$2:$D$96835 is the range of Week_day column and F2 is where the index of the day is placed. since we have the total of number per day we can calculate also the percentage.

	=H2/$H$9
Where H2 is the Day_total and H9 is the Tatal_absolut.

and the table looks somethin like this.


![day of the week](https://user-images.githubusercontent.com/60878213/149680138-b3e4480a-f7aa-4210-8d50-d9fe6c90bd68.png)

We can see that weekend days takes almost 50% of the total used per week, but speaking individualy the porcentage is almost similar to each other.with a difference of 5% from the Min and max values.

![Jenuary_2021](https://user-images.githubusercontent.com/60878213/149680314-e7546f08-ce78-4b25-8f89-299ec9b0b6bd.png)

# Type of bikes use per customers.
We know that we have 3 types of bikes that customers can use:

				*docked_bike
				*electric_bike
				*classic_bike

Again we use the "counif" function: but this time 
	
	=COUNTIF(A2:A96835,[@Column1])
	
Where @column1 is our reference cell from our table. 

![image](https://user-images.githubusercontent.com/60878213/149680589-9dedf567-d1bb-4b62-ba23-0af2d3deb215.png)

Here, is clear that customers prefers to use electric and classic bikes rather than docked, whereas Classic has a notable percentage respective the electric bike.

![image](https://user-images.githubusercontent.com/60878213/149680703-fa3e8a68-7009-48e3-af37-997118b42d9e.png)



What about the percentage of use per customer related to each type of bike available??

Is here where Countifs come to place.

	=COUNTIFS($A$2:$A$96835,F62,$B$2:$B$96835,$G$61)
	
Where we have two conditionals to have one single output. here "$A$2:$A$96835,F62" is the type of Bike and $B$2:$B$96835,$G$61 is the type of customer, if the first argument is true F62= "bike_type the function would count the second argument if this second argument is G61= "type_of_member".



![image](https://user-images.githubusercontent.com/60878213/149681804-902d8886-3454-4698-acba-2dba12c77628.png)

![image](https://user-images.githubusercontent.com/60878213/149681825-2596acc6-d13f-4261-bb96-e7db95470e5f.png)

 # Statistics.
 Now that we have more knowledge about the data and how this data is structured. We could continue performing this manually other analysis, but as the data increases(other 11 months to analyse) the time-consuming rises up too.
For example, we can manually calculate the Mean, Median, Mode, Min and Max from this data set.

![image](https://user-images.githubusercontent.com/60878213/149790436-a904e873-99ca-4b1c-9d6a-81a88550c464.png)

This is ok, however, Pivot tables would performance a better job and almost immediately.

Here are same arguments from the above table, with the exception that we separate the statistics by the two types of customers.

 ![image](https://user-images.githubusercontent.com/60878213/149745769-d8979210-9520-4082-84fc-ae3fd644eb54.png)
 ![image](https://user-images.githubusercontent.com/60878213/149745822-8c496124-2adf-4097-8985-ae5e46cb53a5.png)
 
We can see that both types of customers use the bikes almost similar, with the majority of use between 3 and 10 minutes, respectively. With a histogram skewed to the right.
Still, “Casual” customers tend to use the bike for a longer time of period.

### Calculate the average ride_length for users by day_of_week.
Where the number 1=monday, 2=Tuesday..etc.
	
	PivotFields columns = day_of_week; Rows =member_casual; Values = Average of ride_length

![image](https://user-images.githubusercontent.com/60878213/149795594-51e26f4c-b291-4484-b52d-363e3f462c43.png)
![image](https://user-images.githubusercontent.com/60878213/149796282-ffb731ba-3e8a-41b6-ab6f-38db8ec4c83e.png)


### Number of rides for users by day_of_week
#### Members:
	PivotFields columns = day_of_week; Rows =member_casual; Values = ACount of ride-id
![image](https://user-images.githubusercontent.com/60878213/149797374-1519f5a6-d91c-405e-8c44-1e3a9523fe88.png)
![image](https://user-images.githubusercontent.com/60878213/149797443-4f1730a1-a2b4-4db9-83f4-727f2a357f9c.png)

#### Casual:
	PivotFields columns = day_of_week; Rows =member_casual; Values = ACount of ride-id
![image](https://user-images.githubusercontent.com/60878213/149797504-2e093a40-05d0-4abd-8200-c6fd26a1ca33.png)
![image](https://user-images.githubusercontent.com/60878213/149797536-2ba06826-fbf4-4f80-b332-06ef5b575b65.png)

# Conclusion:
Excel is a powerful tool to analyse a small data set, and we Could automatise the cleaning process recording Macros and would take around 10 min to put the other 11 data sets with the same format we just did, notwithstanding, this time we going to omit this process as we have SQL and, in my opinion, is a better tool and faster to performance when we talk about bigger data. 
