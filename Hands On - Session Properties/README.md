# Hands On - Creating Sessions Properties

In this lab, we will create a session properties to expose business data to Dynatrace

## Membership Status

1) Access the easyTravel application monitoring settings
  Applications > easyTravel > (...) Edit

2) Select **Session and User action properties** and click **Add property** and enter the following:

   Expression Type: **CSS Selector**  
   Data Type: **String**  
   Key:  **membershipstatus**  
   Store as user action property: **true**  
   Store as session property: **true**  
   CSS Selector:  **#loginForm\:j_idt42**  
   Apply cleanup rule: **true**  
   Cleanup Rule Regex: **(.*?) status!**  

![User Session Property Config](/img/usersession-config.PNG)

3) Click **Save Property**

Now create session properties for the trip destination and booking total

## Booking Total

4) Select **Session and User action properties** and click **Add property** and enter the following:

   Expression Type: **CSS Selector**  
   Data Type: **Double**  
   Key:  **bookingtotal**  
   Display Name: **Booking Total**
   Store as user action property: **true**  
   Store as session property: **true**  
   CSS Selector:  **#iceform\:j_idt77-11-1**  
   Apply cleanup rule: **true**  
   Cleanup Rule Regex: **([^$][^;]*+)**  
   
## Trip Destination

5) Select **Session and User action properties** and click **Add property** and enter the following:

   Expression Type: **CSS Selector**  
   Data Type: **String**  
   Key:  **destination**  
   Store as user action property: **true**  
   Store as session property: **true**  
   CSS Selector:  **#iceform\:j_idt77-3-1**  
