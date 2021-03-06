---
layout: article
title: Use the Python Run Downloader
hide_welcome_banner: true
---

To download files associated with a BaseSpace Run, use a Python script with the Run ID and your account access token. This example uses the [BaseSpace Run Downloader](https://da1s119xsxmu0.cloudfront.net/sites/knowledgebase/API/08052014/Script/BaseSpaceRunDownloader_v2.zip) script.

The downloader script is provided AS-IS without any warranty of any kind. Illumina is not responsible for any loss of data, incorrect results, or any costs, liabilities, or damages that may result from the use of this script. 

1. Download the script and unzip the files to an empty directory. <br />The runfolder downloads to the same directory that the script is executed from.  Make sure that you have enough space in the directory for the downloaded runs.
1.	Go to [https://developer.basespace.illumina.com/](https://developer.basespace.illumina.com/) and log in.
2.	From the toolbar, select **My Apps**.
{% screenshot /images/articles/my-apps-link.png %}
3.	In the applications tab, select **Create a New Application**.
{% screenshot /images/articles/create-button.png %}
4. Fill out the Applications Details and then select **Create Application**.
5. On the application page, select the **Credentials** tab and copy the Access Token. {% screenshot /images/articles/credentials-tab.png %}
6. Create a new text file to serve as a script to run the python run downloader.

	<ol type="a">
     <li>Name the file as desired with an extension appropriate to the operating system:
	<ul>
		<li>Windows batch file (*.bat)</li>
		<li>Linux shell script (*.sh)</li>
	</ul>
	</li>
	<li>Copy the access token and Run ID to the Windows batch file or Linux script. The Run ID can be obtained from the URL for the desired run.</li>
	</ol>
     Example Windows batch file/Linux shell script (single line):<br />
		
		python BaseSpaceRunDownloader_v2.py -r <Run ID> -a <access token>
7. Run the script.<br />When the script executes, the runfolder files appear in a new output directory. 