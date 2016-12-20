---
layout: article
title: iCredits and Billing
hide_welcome_banner: true
---

BaseSpace Sequence Hub storage, compute, and third-party application costs are charged in iCredits. 

## iCredits
-----
iCredits are the common currency in which BaseSpace Sequence Hub services are priced. iCredits cannot be purchased in advance.

Free Trial accounts and new Professional or Enterprise subscription accounts are granted 250 iCredits that can be used to pay for compute, storage, and third-party applications. 

Once these promotional iCredits are used, Professional and Enterprise accounts accrue charges in iCredits for storage, compute, and third-party application fees. Usage is invoiced billed monthly in arrears. [Contact your sales representative]( http://www.illumina.com/forms/contact_request.html?mktofrm=GM-Informatics-Basespace-Website-Contact-Question-2.0-Responsive&sciid=2016019IBN2) for more information. 

Promotional and subscription iCredit charges are rounded up to the nearest iCredit. The BaseSpace Sequence Hub dashboard displays your current iCredit usage.


 <table class="table table-bordered" width ="75%">
            <col />
            <col />
            <col />
            <col />
            <col />
            <tr>
                <th>&#160;</th>
                <th style="text-align: center;">Free Trial</th>
                <th style="text-align: center;">Basic</th>
                <th style="text-align: center;">Professional</th>
                <th style="text-align: center;">Enterprise</th>
            </tr>
            <tr>
                <td>Included Storage</td>
                <td style="text-align: center;">1 TB</td>
                <td style="text-align: center;">1 TB<sup>1</sup></td>
                <td style="text-align: center;">1 TB</td>
                <td style="text-align: center;">1 TB</td>
            </tr>
            <tr>
                <td>Additional Storage</td>
                <td style="text-align: center;">iCredits<sup>2</sup></td>
                <td style="text-align: center;">No</td>
                <td style="text-align: center;">iCredits<sup>3</sup></td>
                <td style="text-align: center;">iCredits<sup>3</sup></td>
            </tr>
            <tr>
                <td>Purchase Storage Subscription</td>
                <td style="text-align: center;">No</td>
                <td style="text-align: center;">No</td>
                <td style="text-align: center;">Yes</td>
                <td style="text-align: center;">Yes</td>
            </tr>
            <tr>
                <td>Free Apps</td>
                <td style="text-align: center;">Yes</td>
                <td style="text-align: center;">Yes<sup>1</sup></td>
                <td style="text-align: center;">Yes</td>
                <td style="text-align: center;">Yes</td>
            </tr>
            <tr>
                <td>Paid Apps<sup>2</sup></td>
                <td style="text-align: center;">iCredits<sup>3</sup></td>
                <td style="text-align: center;">No</td>
                <td style="text-align: center;">iCredits<sup>4</sup></td>
                <td style="text-align: center;">iCredits<sup>4</sup></td>
            </tr>
        </table>

<p><small><sup>1</sup> Basic accounts using more than 1 TB of storage can perform instrument runs and download or delete data but cannot share data or use any apps until storage use is below the 1 TB limit. </small></p>


<p><small><sup>2</sup>If an app terminates due to a BaseSpace Sequence Hub error, fees associated with the terminated run are not charged; if the app is terminated by a user, fees associated with the terminated run are applied.</small><p>


<p><small><sup>3</sup>Free trial iCredits expire after 30 days. To add iCredits after the trial period has expired, [Contact your sales representative]( http://www.illumina.com/forms/contact_request.html?mktofrm=GM-Informatics-Basespace-Website-Contact-Question-2.0-Responsive&sciid=2016019IBN2) about upgrading to a Professional or Enterprise account.  </small><p>

<p><small><sup>4</sup> Professional and Enterprise subscription accounts are billed monthly. Promotional iCredits are valid as long as the subscription is current; subscription renewals are not granted additional iCredits. Promotional and billable iCredit usage is reflected in the dashboard and the monthly invoice.</small><p>

###iCredit Usage


The BaseSpace Sequence Hub dashboard displays your iCredit usage for the current billing period. 

{% screenshot /images/articles/icredits-dashboard.png %}

Click **Details** to view the usage history report.

{% screenshot /images/articles/icredit-usage-report.png %}

For more information about usage reports and instructions for downloading detailed reports, see [Generate Usage Reports](/articles/tutorials/generate-usage-reports).

###Storage
-----
All accounts include a 1 TB<sup>*</sup> storage allowance. Professional and Enterprise accounts are invoiced monthly for storage over 1 TB, at a rate of 0.03 iCredits per GB month. 

Professional and Enterprise accounts can purchase additional storage subscriptions. [Contact your sales representative]( http://www.illumina.com/forms/contact_request.html?mktofrm=GM-Informatics-Basespace-Website-Contact-Question-2.0-Responsive&sciid=2016019IBN2) for more information.

{% callout note, NOTE %}Basic tier customers cannot purchase additional storage. If you need more than 1 TB of storage, [contact your sales representative]( http://www.illumina.com/forms/contact_request.html?mktofrm=GM-Informatics-Basespace-Website-Contact-Question-2.0-Responsive&sciid=2016019IBN2) about upgrading to a Professional or Enterprise account.  {% endcallout %}

{% callout note, NOTE %}Storage charges are deducted from promotional iCredits at the end of the month. For subscription accounts, storage is tabulated daily. The storage calculation rate is based on a 30-day month.{% endcallout %}

<p>*<small> 1 TB == 2<sup>40</sup> == 1024<sup>4</sup> bytes</small>
###Compute
-----
Compute usage is billed at a per-minute rate in iCredits per node hour. The compute rate for an application is displayed on the application details page.

{% callout note, NOTE %}Compute charges are deducted from promotional iCredits immediately. For subscription accounts, compute is tabulated in real time. {% endcallout %}
###Third-Party Applications
-----
You can use iCredits to purchase third-party application subscriptions, analysis, and reports. Price information for third-party services is displayed on the application details page. 

{% callout note, NOTE %}Third-party app charges are deducted from promotional iCredits at the end of each day. For subscription accounts, third-party app charges are tabulated in real time. For a list of free apps available to Basic accounts, see Basic and Free Trial Accounts.{% endcallout %}

##Monthly Invoices
-----
For Professional or Enterprise subscription accounts with a valid Purchase Order, Illumina invoices the sum of storage, compute, and third-party application iCredit charges each month. The sum is rounded up to the nearest whole iCredit when the invoice is calculated.


{% callout note, NOTE %}If an app terminates due to a BaseSpace Sequence Hub error, fees associated with the terminated run are not charged; if the app is terminated by a user, fees associated with the terminated run are applied.{% endcallout %}

