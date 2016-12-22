---
layout: article
title: Generate Usage Reports
hide_welcome_banner: true
---


Enterprise subscription accounts include usage history reports. Users and administrators can download detailed usage reports.

+ Domain administrators can view and download usage history for all workgroups in the domain.
+ Workgroup administrators can view and download usage history for their workgroups.
+ All users can view and download their personal usage history.
 
----------------
##View Reports

1. Use 1 of the following methods to view the usage report.
	- From the Dashboard iCredits panel, select **Details.** {% screenshot /images/articles/icredits-dashboard.png %}
	- Select the Account drop-down arrow, and then select **Settings**. In the Settings page, select **Usage**. 
	
The usage report contains the following information.

 + **Billing Cycle**—The billing cycle in which the usage was logged. Only the last 6 billing cycles are listed.   
+ **Total iCredits**—The total number of iCredits accrued in the billing cycle.    
+ **Workgroup/User**—The name of the personal account or workgroup that incurred charges during the billing period. 
+ **Storage iCredits**—The storage iCredit charges accrued for the workgroup or personal account. Storage charges are recomputed daily.
+ **App iCredits**—The app iCredit charges accrued for the workgroup or personal account.
+ **Compute iCredits**—The compute iCredit charges accrued for the workgroup or personal account.


	{% screenshot /images/articles/icredit-usage-report.png %}
    
-------------
## Download Reports
1. Use 1 of the following methods to view the usage report.
	- From the Dashboard iCredits panel, select **Details.** {% screenshot /images/articles/icredits-dashboard.png %}
	- Select the Account drop-down arrow, and then select **Settings**. In the Settings page, select **Usage**. 
2. Select the **Download** icon, and then select a billing period. 
 {% screenshot /images/articles/icredit-usage-download.png %}
3. Select **Save** and save the CSV file in the designated folder. By default, the file is named [mmmyyyy]_usages.csv.

The report contains the following columns.
	
+ **Timestamp**—The date and time of the activity.
+ **LoggedInUser**—The login email of the user.
+ **Workgroup**—The name of the workgroup.
+ **Quantity**—The number of units of storage, compute, or app license fees used. 
	+ Storage activity is listed in bytes per day for the acting user.
	+ Compute activity is listed in total minutes of compute time.
	+ App license fees are listed in iCredits.
+ **AdjustedCost**—The calculated cost (Quantity &#215; PricePerUnit) of the activity. 
+ **PricePerUnit**—The price charged per unit of storage, compute, or iCredits. 
+ **Description**—The activity that incurred the charge. 