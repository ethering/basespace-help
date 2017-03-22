---
layout: article
title: Obtain Python Run Downloader Token
hide_welcome_banner: true
---

In order to communicate with our API you will need an access token. Here are the steps to obtain one from your account.


1.	Go to https://developer.basespace.illumina.com/ and log in.

2.	From the toolbar, select **My Apps**.
{% screenshot /images/articles/my-apps-link.png %}

3.	In the applications tab, select **Create a New Application**.
{% screenshot /images/articles/create-button.png %}

4. Fill out the Applications Details and then select **Create Application**.

5. On the application page, select the **Credentials** tab. {% screenshot /images/articles/credentials-tab.png %}

6. Copy the access token and Run ID to the Windows batch file or Linux script that will run the python run downloader. The Run ID can be obtained from the URL for the desired run.<br /><br />Example Windows batch file/Linux shell script (single line):<br />python BaseSpaceRunDownloader_v2.py -r \<Run ID\> -a \<access token\>
{% callout note, NOTE %}The runfolder downloads to the same directory that the script is executed from.  Make sure you have enough space in the directory for the downloaded runs.{% endcallout %}

7. Run the script.
 