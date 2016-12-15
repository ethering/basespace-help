---
layout: article
title: Generate Usage Reports
hide_welcome_banner: true
---


Enterprise subscription accounts include usage history reports. Users can download detailed reports of their personal account usage. Domain Administrators can download detailed reports for all users in the domain.

1. Use 1 of the following methods to view the usage report.
	- From the Dashboard iCredits panel, click **Details.** {% screenshot /images/articles/icredits-dashboard.png %}
	- Click the Account drop-down arrow, and select **Settings**. In the usage page, select **Usage**. 
	
	The usage report contains the following information:
 + **Billing Cycle**—The billing cycle in which the usage was logged. Only the last 6 billing cycles are listed.   
	+ **Total iCredits**—The total number of iCredits accrued in the billing cycle.
    + **Workgroup/User**—The name of the personal account or workgroup that incurred charges during the billing period. 
     	+ Domain Administrators can see all workgroups in the domain.
     	+ Workgroup owners can see consumption for their workgroups.
     	+ All users can see their personal consumption.
    + **Storage iCredits**—The storage iCredit charges accrued for the workgroup or personal account. Storage charges are recomputed daily.
    + **App iCredits**—The app iCredit charges accrued for the workgroup or personal account.
    + **Compute iCredits**—The compute iCredit charges accrued for the workgroup or personal account.


	{% screenshot /images/articles/icredits-usage-report.png %}
    
 
2. [Optional] Download the transaction detail report.<ol type="a"><li>Click the **Download** icon, and then select a billing period. 
 {% screenshot /images/articles/icredits-usage-report.png %}</li>
<li>Click **Save** and save the CSV file in the designated folder. By default, the file is named Workgroup-[Workgroup-Name]-Usage-[YYYY-MM].csv.
</li></ol><br />The report includes the workgroup name, billing period, storage rate, compute rate, and the following columns.
	+ **Date and Time**—The date and time of the activity.
  + **User Email**—The login email of the user.
  + **App Name**—The name of the app used.
  + **Storage Used (Bytes)**—The number of storage bytes used. 
  + **Storage Charge (iCredits)**—The storage charge, in iCredits, for the activity. 
  + **App License Charge (iCredits)**—The app license fee charge, iCredits.
  + **Compute Time (Minutes)**—The compute time, in minutes, for the activity.
  + **Compute Unit Price**—The app compute rate.
  + **Description**—The storage, compute, or app activity that incurred the charge.  