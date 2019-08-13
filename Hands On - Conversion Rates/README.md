# Hands On - Creating Conversion Rates

In this lab, we will create conversion goals for the easyTravel application

## Key User Action
First we need to mark the page (/orange-booking-finish.jsf) as a key user action:
1) Access the easyTravel application

2) Under **Top 3 user actions** click **View full details**

3) Scroll down to **Top 100 user a actions** and filter for **orange-booking-finish.jsf**

![Conversion Goal](/img/conversion_goal_filter.PNG)

4) Click on the user user action **Loading of page /orange-booking-finish.jsf** then click on **Matk as key user action**

![Conversion Goal](/img/conversion_goal_makua.PNG)

## Conversion Goal

5) Access the easyTravel application monitoring settings
  Applications > easyTravel > (...) > Edit

6) Select **Conversion Goals** and click **Add goal** and enter the following:

   Name: **Successful Bookings - open final Page**  
   Type of goal: **Destination** > **contains** > **/orange-booking-finish.jsf**  

![Conversion Goal](/img/conversion_goal.PNG)

Check results aginst the application: **easyTravel** > **User behavior**  

![Conversion Goal](/img/conversion_goal-done.PNG)

## Create 3 more Convertion Goals

Follow the above steps to create conversion goals for:  
  Name: Homepage  
  Destination > contains > **Loading of page /orange.jsf**  
  
  Name: Review  
  Destination > contains > **/orange-booking-review.jsf**  
  
  Name: Payment  
  Destination > contains > **/orange-booking-payment.jsf**
