**Email marketing analysis using Power BI**

**End-to-End Power BI project BY Biswojit Mohnanty**


Problem Statement

As an E-Commerce company they run different campaign for their products ,services etc. things via Email. So it is necessary to know how this email campaigns are performing like how it is benefiting their users .

So our task is to perform analysis the data provided by the company in Excel sheet and give them insights about their Email campaign like how many mails are opened by the user, total mail sent in each campaign, how many mails are clicked by the user etc .

It will help the company to make the changes in their marketing strategy to attract more customer and run their campaign successfully and with high mail opening rate.



**Click on load**

Now our data is loaded in Power BI .

You can view the loaded data by clicking on left most corners table like icon.

**Cleaning and Transforming Data**

In this step we go through our data see how our data is present like how many missing values, null values and also creating measures, columns which will be used in visualization .

Our data needs some calculated columns and measures which will be useful for our visualization part

so lets create the additional columns and measures

Add new columns name it as “unique_click_count”
The purpose of this column is to count the unqiue click count from the “Email_click_count”.

Use below formula in the formula bar as shown in below figure

Unique_click = IF(TBL_Communication[Email_Click_Count]>0,1,0)


Hit enter .
Now you will see the column is added into your data.

2 . Add new columns name it as “unique_open_count”

The purpose of this column is to count the unqiue open count from the “Email_open_count”.

Formula :

Unique_open = IF(TBL_Communication[Email_Open_Count]>0,1,0)

3 . We have to count total email bounced from “Email_Sent_Stautus” so to do that we have to add another new column name it as “Bounced_email”

Formula:

Bounced_email = IF(TBL_Communication[Email_Sent_Status]=”Bounced”,1,0)

4 . Now we have to count the total delivered mail means Sent mail .So now we have to get the count of Sent mail from the “Email_Sent_Stautus” column and create new column for sent count .So to do that name new column as “Delivered_email” and write below formula in formula bar and hit enter.

Formula :

Delivered_email = IF(TBL_Communication[Email_Sent_Status]=”Sent”,1,0)

5 . We are now calculating the percentage of click through rate of email to do that

Add measure to add the measure see the below image and follow


Click on new measure
To calculate CTR Click Through Rate use below formula paste it in formula bar

CTR = SUM(TBL_Communication[Email_Click_Count])/(SUM(TBL_Communication[Is_Email_Sent])-(SUM(TBL_Communication[Bounced_email])))

After that hit enter new measure will be created and also don’t forgot to make the output formatting in percentage to do that click on that measure and under the “Measure Tools” option choose the format as percentage.

6 . We are now calculating the percentage of Bounce Rate of email to do that

create new measure and add below formula

Formula :

BR = SUM(TBL_Communication[Bounced_email])/SUM(TBL_Communication[Is_Email_Sent])

After that hit enter new measure will be created and also don’t forgot to make the output formatting in percentage to do that click on that measure and under the “Measure Tools” option choose the format as percentage.

7 . We are now calculating the percentage of Open Rate of email to do that

create new measure and add below formula

Formula :

OR = SUM(TBL_Communication[Email_Open_Count])/SUM(TBL_Communication[Delivered_email])

Don’t forgot to make the output formatting in percentage to do that click on that measure and under the “Measure Tools” option choose the format as percentage.

8 . We are now calculating the percentage of Deliver Rate of email to do that

create new measure and add below formula

Formula :

DR = SUM(TBL_Communication[Delivered_email])/SUM(TBL_Communication[Is_Email_Sent])

Don’t forgot to make the output formatting in percentage to do that click on that measure and under the “Measure Tools” option choose the format as percentage.

9 . Add the below 2 columns by clicking on “Add Column” and write the below formula

Memeber who clicked the email

Member_clicked = IF(TBL_Communication[Email_Click_Count]>0,TBL_Communication[PartyUId])

Member who opened the email

Member_open = IF(TBL_Communication[Email_Open_Count]>0,TBL_Communication[PartyUId])

So these are the measures and columns which we have created for visualization.

Data visualization


Conclusion :

From the above dashboard we can see that by going through each campaign that the open count of mails are less.

So marketing teams needs to work on the this to attract and make sure customer open the email may be they have to change the content ,subjects of the email.

 ![Email Campaign Analysis](https://github.com/BiswojitMohanty/Insurance-Data-Analysis/assets/155844093/d258b2e2-0506-4927-9b0d-230dca439552)

 
