# Hands On - Creating Sessions Properties

In this lab, we will create a session properties to expose business daTA

Access the easyTravel application monitoring settings
  Applications > easyTravel > (...) Edit

Select **Session and User action properties** and click **Add property** and enter the following:

    Expression Type: **CSS Selector**
    Data Type: **String**

    Key:  **membershipstatus**

    CSS Selector:  **#loginForm\3a j_idt42**

    Cleanup Rule Regex: **(.*?) Status!**

![User Session Property Config](/img/usersession-config.PNG)

