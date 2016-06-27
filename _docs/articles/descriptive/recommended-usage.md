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
		<td>Browsing and interacting directly with files without having to download them locally</td>
		<td><code>bs mount</code></td>
		<td></td>
	</tr>
	<tr>
		<td>Interactive selective copying</td>
		<td><code>bs mount</code></td>
		<td>The interactive nature of BaseMount makes it easier to select files to copy</td>
	</tr>
	<tr>
		<td>Scripted or programmatic copying</td>
		<td><code>bs cp</code></td>
		<td><p><li> Using <code>bs cp</code> in scripts avoids having to <code>bs mount</code> first<br>
		       <li> <code>bs cp</code> has better error reporting</td>
	</tr>
	<tr>
		<td>Downloading runfolders with thousands of small files</td>
		<td><code>bs cp</code></td>
		<td>BaseMount relies on Unix tools like <code>cp</code> and <code>rsync</code>, which only copy one file at a time.
		    By copying more than one file in parallel, <code>bs cp</code> performs better on these examples</td>
	</tr>
	<tr>
		<td>Uploading samples</td>
		<td><code>bs sample upload</code></td>
		<td>The sample uploader is the only tool able to do fastq validation</td>
	</tr>
</table>
