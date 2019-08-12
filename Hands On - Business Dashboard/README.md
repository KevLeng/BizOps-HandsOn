# Hands On - Creating Business Dashboard

In this lab, we will create the following dashboard:

![Business Dashboard](/img/business_dashboard_done.PNG)

## Dashboard Components

The above dashboard has the following components:

1) **User Behavior** > **easyTravel**

2) **Top conversion goals** > **easyTravel**

3) **Conversion goal** > **easyTravel** > **Sucessful Bookings**

4) **Bounce Rate** > **easyTravel**

5) **Key user actions** > **easyTravel**

6) **User Session Query**:  

SELECT DATETIME(starttime, 'MM/dd/yyyy hh:mm', '30m'),AVG(usersession.doubleProperties.bookingtotal) FROM usersession WHERE usersession.doubleProperties.bookingtotal IS NOT NULL GROUP BY DATETIME(starttime, 'MM/dd/yyyy hh:mm', '30m')  

7) **User Session Query**:  

SELECT usersession.stringProperties.destination, SUM(usersession.doubleProperties.bookingtotal) FROM usersession WHERE usersession.stringProperties.destination IS NOT NULL GROUP BY usersession.stringProperties.destination  

8) **User Session Query**:  

SELECT usersession.stringProperties.membershipstatus, SUM(usersession.doubleProperties.bookingtotal) FROM usersession WHERE usersession.stringProperties.membershipstatus IS NOT NULL GROUP BY usersession.stringProperties.membershipstatus  
