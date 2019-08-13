# Hands On - Creating Sessions Properties - Part 2

In this lab, we will create a session properties to expose business data Booking Total and Dstination to Dynatrace

## Booking Total

First get the CSS selector for the Booking Total field.

1) Assess the easyTravel homepage (the URL provied to you)
2) Seach for a destination e.g. Gold Coast and click **Book Now**

![easyTravel Step 1](/img/easytravel-step1.PNG)

3) Login with username: **janet** and password: **janet** and click **Next**

![easyTravel Step 2](/img/easytravel-step2.PNG)

4) Right click on the Round-trip ticket price $ value and click **inspect**
5) Right click on the <span> and select **Copy** > **Copy Selector**
  
Second create the session property in Dynatrace.

1) Access the easyTravel application monitoring settings
  Applications > easyTravel > (...) Edit

2) Select **Session and User action properties** and click **Add property** and enter the following:

   Expression Type: **CSS Selector**  
   Data Type: **Double**  
   Key:  **bookingtotal**  
   CSS Selector:  **The CSS Selector you copied above**  
   Display Name: **Booking Total**  
   Store as user action property: **false**  
   Store as session property: **true**  
   Apply cleanup rule: **true**  
   Cleanup Rule Regex: **([^$][^;]*+)**  
   
You can view the user sessions that have the booking total value by running the following USQL: 

    SELECT * FROM usersession WHERE doubleProperties.bookingtotal IS NOT NULL ORDER BY startTime DESC
   
## Trip Destination

5) Select **Session and User action properties** and click **Add property** and enter the following:

   Expression Type: **CSS Selector**  
   Data Type: **String**  
   Key:  **destination**  
   CSS Selector:  **#iceform\\:j_idt126**  
   Store as user action property: **false**  
   Store as session property: **true**  
   Apply cleanup rule: **false**  

You can view the user sessions that have the destination value by running the following USQL: 

    SELECT * FROM usersession WHERE stringProperties.destination IS NOT NULL ORDER BY startTime DESC
    
    
It may take 5-10 mins to see results in Dynatrace because session properties are only available when the user session is completed.