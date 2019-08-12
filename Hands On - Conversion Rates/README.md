# Hands On - Creating Conversion Rates

In this lab, we will create conversion goals for the easyTravel application

## Membership Status

1) Access the easyTravel application monitoring settings
  Applications > easyTravel > (...) > Edit

2) Select **Comversion Goals** and click **Add goal** and enter the following:

   Name: **Successful Bookings - open final Page**  
   Type of goal: **Destination** > **contains** > **/orange-booking-finish.jsf**  

![Conversion Goal](/img/conversion_goal.PNG)

Check results by running this USQL:
  SELECT * FROM usersession WHERE useraction.matchingConversionGoals IS NOT NULL
