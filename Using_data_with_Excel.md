#Playing with Data
After we get acquainted with the database and make some changes, we want to start to see some insights.

About the Data and The cleaning process. 
https://github.com/MiguelAAP90/Excel-_cleaning_data/blob/main/Prep_Data_excel.md.


#separet data.
From the full Sheet of our data  we going to work this time just with four columns "rideable_type,	member_casual,	ride_length,	Week_day", 
this with the objective of answearing our principal questions.

What type of customer do we have?

What day of the week do customers tend to use the service?

What type of bicycles customers are using?


![Small_data](https://user-images.githubusercontent.com/60878213/149678672-06852ba4-7102-445f-8467-1d59f74e7a83.png)


#What type of customer do we have?
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



#Day of the week
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

#type of bikes use per customers.
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


![image](https://user-images.githubusercontent.com/60878213/149681804-902d8886-3454-4698-acba-2dba12c77628.png)

![image](https://user-images.githubusercontent.com/60878213/149681825-2596acc6-d13f-4261-bb96-e7db95470e5f.png)


