# Sales Funnel Dashboard

In this lab, we will build on the Basic Funnel we created earlier to create this dashsboard

![USQL Icon](/img/sales-funnel-done.PNG)

In the Dynatrace UI, edit the dashboard you created during the Basic Funnel exercise.

Add the following elements to the dashboard:

### Abandons

Homepage  

    select count(*) as "Abandons" from usersession where useraction.name="Loading of page /orange.jsf" and useraction.name!="Loading of page /orange-booking-review.jsf"  
    
Review  
      
    select count(*) as "Abandons" from usersession where useraction.name="Loading of page /orange.jsf" and useraction.name="Loading of page /orange-booking-review.jsf" and useraction.name!="Loading of page /orange-booking-payment.jsf"  
      
Payment  
    
    select count(*) as "Abandons" from usersession where useraction.name="Loading of page /orange.jsf" and useraction.name="Loading of page /orange-booking-review.jsf" and useraction.name="Loading of page /orange-booking-payment.jsf" and useraction.name!="Loading of page /orange-booking-finish.jsf"  

Finish  
     
    select count(*) as "Abandons" from usersession where useraction.name="Loading of page /orange.jsf " and useraction.name="Loading of page /orange-booking-review.jsf" and useraction.name="Loading of page /orange-booking-payment.jsf" and useraction.name="Loading of page /orange-booking-finish.jsf"

### Errors

Homepage  
      
     select sum(errorCount) as "Errors" from useraction where name="Loading of page /orange.jsf"
    
Review
     
     select sum(errorCount) as "Errors" from useraction where name="Loading of page /orange-booking-review.jsf"
      
Payment
     
     select sum(errorCount) as "Errors" from useraction where name="Loading of page /orange-booking-payment.jsf"

Finish
     
     select sum(errorCount) as "Errors" from useraction where name="Loading of page /orange-booking-finish.jsf"

      
When you are finished your dashboard should look something like this:

![Dashboard Basic Funnel](/img/usql-basic-funnel.PNG)
