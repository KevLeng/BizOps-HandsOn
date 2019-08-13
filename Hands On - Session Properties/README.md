# Hands On - Creating Sessions Properties

In this lab, we will create a session properties to expose business data to Dynatrace

## Membership Status

1) Access the easyTravel application monitoring settings
  Applications > easyTravel > (...) Edit

2) Select **Session and User action properties** and click **Add property** and enter the following:

   * Expression Type: **CSS Selector**  
   * Data Type: **String**  
   * Key:  **membershipstatus**  
   * CSS Selector:  **#loginForm\\:j_idt43**  
   * Store as user action property: **false**  
   * Store as session property: **true**  
   * Apply cleanup rule: **true**  
   * Cleanup Rule Regex: **(.*?) status!**  

![User Session Property Config](/img/usersession-config.PNG)

3) Click **Save Property**

It may take 5-10 mins to see results in Dynatrace because session properties are only available when the user session is completed.

You can view the user sessions that have the membershipstatus set  by running the following USQL: 

    SELECT * FROM usersession WHERE stringProperties.membershipstatus IS NOT NULL ORDER BY startTime DESC

Now create session properties for the trip destination and booking total

## Booking Total

4) Select **Session and User action properties** and click **Add property** and enter the following:

   Expression Type: **CSS Selector**  
   Data Type: **Double**  
   Key:  **bookingtotal**  
   CSS Selector:  **#iceform\\:j_idt113-11-1**  
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
