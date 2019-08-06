# Hands On - Creating Sessions Properties

In this lab, we will create a session properties to expose business data to Dynatrace

1) Access the easyTravel application monitoring settings
  Applications > easyTravel > (...) Edit

2) Select **Session and User action properties** and click **Add property** and enter the following:

   Expression Type: **CSS Selector**  
   Data Type: **String**  
   Key:  **membershipstatus**  
   Store as user action property: **true**  
   Store as session property: **true**  
   CSS Selector:  **#loginForm\3a j_idt42**  
   Apply cleanup rule: **true**  
   Cleanup Rule Regex: **(.*?) Status!**  

![User Session Property Config](/img/usersession-config.PNG)

3) Click **Save Property**
