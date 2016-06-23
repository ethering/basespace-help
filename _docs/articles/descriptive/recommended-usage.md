---
layout: article
title: Which tool should I use?
---

##Overview
This table helps you choose which tool is most suitable for your application

| Application | Recommended Tool | Discussion |
| --- | --- | --- |
| Installation on a computer without root access | `bs cp` | BaseMount needs root access for apt-get/yum and FUSE configuration |
| Browsing and interacting directly with files without having to download them locally | `bs mount` | |
| Interactive selective copying | `bs mount` | The interactive nature of BaseMount makes it easier to select files to copy |
| Scripted or programmatic copying | `bs cp` | - Using `cp` in scripts avoids having to `mount` first <br>
 - The underlying `cp` has better error reporting |
| Downloading runfolders with thousands of small files | `bs cp` | BaseMount relies on Unix tools like cp and rsync, which only copy one file at a time. By copying more than one file in parallel, `cp` performs better on these examples |
| Downloading appresult files | `bs cp`/`bs mount` | |
| Downloading appresult files and metadata | `bs mount` | |
| Downloading sample files | `bs cp`/`bs mount` | |
| Downloading sample files and metadata | `bs mount` | |
| Uploading runfolders with thousands of small files | N/A | |
| Uploading appresults | `bs cp`/`bs mount` | |
| Uploading samples | `bs sample upload` | The sample uploader is the only tool able to do fastq validation |
| Copying samples or appresults across servers | `bs mount` | BaseMount can copy the metadata and doesn't need a temporary local copy of the files (Note: sample upload currently deactivated from public release) |
 

