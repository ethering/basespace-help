---
layout: article
title: Which tool should I use?
---

##Overview
This table helps you choose which tool is most suitable for your application

<table class="table table-bordered">
	<tr>
		<th>Application</th>
		<th>Recommended Tool</th>
		<th>Discussion</th>
	</tr>
	<tr>
		<td>Sample name</td>
		<td>The sample name from the sample sheet</td>
	</tr>



	<tr>
		<td>Installation on a computer without root access</td>
		<td><pre>bs cp</pre></td>
		<td>BaseMount needs root access for apt-get/yum and FUSE configuration</td>
	</tr>
	<tr>
		<td>Browsing and interacting directly with files without having to download them locally</td>
		<td><pre>bs mount</pre></td>
		<td></td>
	</tr>
	<tr>
		<td>Interactive selective copying</td>
		<td><pre>bs mount</pre></td>
		<td>The interactive nature of BaseMount makes it easier to select files to copy</td>
	</tr>
	<tr>
		<td>Scripted or programmatic copying</td>
		<td><pre>bs cp</pre></td>
		<td><p><li> Using <pre>cp</pre> in scripts avoids having to <pre>mount</pre> first<br>
		       <li> The underlying `cp` has better error reporting</td>
	</tr>
	<tr>
		<td>Downloading runfolders with thousands of small files</td>
		<td><pre>bs cp</pre></td>
		<td>BaseMount relies on Unix tools like cp and rsync, which only copy one file at a time. By copying more than one file in parallel, <pre>cp</pre> performs better on these examples</td>
	</tr>
	<tr>
		<td>Downloading appresult files</td>
		<td><pre>bs cp</pre>/<pre>bs mount</pre></td>
		<td></td>
	</tr>
	<tr>
		<td>Downloading appresult files and metadata</td>
		<td><pre>bs mount</pre></td>
		<td></td>
	</tr>
	<tr>
		<td>Downloading sample files</td>
		<td><pre>bs cp</pre>/<pre>bs mount</pre></td>
		<td></td>
	</tr>
	<tr>
		<td>Downloading sample files and metadata</td>
		<td><pre>bs mount</pre></td>
		<td></td>
	</tr>
	<tr>
		<td>Uploading runfolders with thousands of small files</td>
		<td>N/A</td>
		<td></td>
	</tr>
	<tr>
		<td>Uploading appresults</td>
		<td><pre>bs cp</pre>/<pre>bs mount</pre></td>
		<td></td>
	</tr>
	<tr>
		<td>Uploading samples</td>
		<td><pre>bs sample upload</pre></td>
		<td>The sample uploader is the only tool able to do fastq validation</td>
	</tr>
</table>
