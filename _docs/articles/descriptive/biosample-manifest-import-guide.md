---
layout: article
title: Using BioSample Manifests
hide_welcome_banner: true
---



The BioSample Manifest file allow you to import and edit BioSamples in bulk. You can use the manifest to do the following: 

- Import BioSamples and add metadata key-value pairs.
- Add library prep instructions and auto-launchable Analysis Workflows to new or existing BioSamples.

This page explains the BioSample manifest file structure and requirements.

-   [File Format Requirements](#file-format-requirements)
-   [Adding BioSamples and Projects](#adding-biosamples-and-projects)
-   [Adding Prep Requests to Create Libraries](#adding-prep-requests-to-create-libraries)
-   [Scheduling Analyses for Auto-app Launch](#scheduling-analyses-for-auto-app-launch)
-   [Adding Metadata to BioSamples](#adding-metadata-to-biosamples)
-   [Adding to Existing BioSamples](#adding-to-existing-biosamples)
-   [Using Sample Sheets with the BioSample Manifest](#using-sample-sheets-with-the-biosample-manifest)
-   [Example Manifest](#full-examples)


##File Format Requirements

To correctly parse column data, the manifest file must meet the following requirements:

- BioSample Name and Default Project columns must be included
- Maximum 100 columns
- Column headers must be between 4—60 characters and may not contain special characters
- No blank column headers between existing columns


###Example

  <table class="table table-bordered">
            <tbody>
                <tr>
                    <td>
                        <p>[Header]</p>
                    </td>
                    <td>
                        <p>&#160;</p>
                    </td>
                    <td>
                        <p>&#160;</p>
                    </td>

                </tr>
                <tr>
                    <td>
                        <p>FileVersion</p>
                    </td>
                    <td>
                        <p>1</p>
                    </td>
                    <td>
                        <p>&#160;</p>
                    </td>
                </tr>
                <tr>
                    <td>
                        <p>[Data]</p>
                    </td>
                    <td>
                        <p>&#160;</p>
                    </td>
                    <td>
                        <p>&#160;</p>
                    </td>
                </tr>
                <tr>
                    <td style="color: #0000cd;">
                        <p>BioSample Name</p>
                    </td>
                    <td style="color: #0000cd;">
                        <p>Default Project</p>
                    </td>
                    <td style="color: #0000cd;">
                        <p>Container Name</p>
                    </td>
                </tr>
                <tr>
                    <td style="font-style: italic;">
                        <p>value...</p>
                    </td>
                    <td style="font-style: italic;">
                        <p>value...</p>
                    </td>
                    <td style="font-style: italic;">
                        <p>value...</p>
                    </td>
                </tr>
            </tbody>
        </table>
##BioSample and Project Columns

The BioSamples columns define the biosamples to be added or changed in BaseSpace.

- **BioSample Name**—The unique identifier for the source DNA. If an imported BioSample file includes a biosample name that already exists, the biosample data are added to the existing biosample. For more information, see [Adding to Existing BioSamples](#adding-to-existing-biosamples).
- **Default Project**—The default project in which the biosample data is stored. If a default project does not exist, a new project is created. 
- **Container Name**—This column is optional. It is commonly used to define the source DNA plate barcode. 
- **Container Position**—If a Container Name is entered, this column is required. It is commonly used to define the well location of the DNA plate defined in the Container Name column.

###BioSample Data Requirements

- BioSample Name and Default Project values are required.
- BioSample name contains no spaces or special characters, and is unique in the manifest (ie, a given BioSample can be present in only one row of the manifest).
- If a Container Name is entered, the Container Position is required.
- Container Name must be unique.
- BioSample name contains no spaces or special characters

###Example
<table class="table table-bordered">
            <col />
            <col />
            <col />
            <col />
            <thead>
                <tr>
                    <th style="color: #3E7EBE;">
                        <p style="text-align: left;">BioSample Name</p>
                    </th>
                    <th style="color: #3E7EBE;">
                        <p style="text-align: left;">Default Project</p>
                    </th>
                    <th style="color: #3E7EBE;">
                        <p style="text-align: left;">Container Name</p>
                    </th>
                    <th style="color: #3E7EBE;">
                        <p style="text-align: left;">Container Position</p>
                    </th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td style="color: #3E7EBE;">
                        <p >LP0000001-DNA_A01</p>
                    </td>
                    <td style="color: #3E7EBE;">
                        <p>TestProject</p>
                    </td>
                    <td style="color: #3E7EBE;">
                        <p>LP0000001-DNA</p>
                    </td>
                    <td style="color: #3E7EBE;">
                        <p>A01</p>
                    </td>
                </tr>
                <tr>
                    <td style="color: #3E7EBE;">
                        <p>LP0000001-DNA_B01</p>
                    </td>
                    <td style="color: #3E7EBE;">
                        <p>TestProject</p>
                    </td>
                    <td style="color: #3E7EBE;">
                        <p>LP0000001-DNA</p>
                    </td>
                    <td style="color: #3E7EBE;">
                        <p>B01</p>
                    </td>
                </tr>
                <tr>
                    <td style="color: #3E7EBE;">
                        <p>LP0000001-DNA_C01</p>
                    </td>
                    <td style="color: #3E7EBE;">
                        <p>TestProject</p>
                    </td>
                    <td style="color: #3E7EBE;">
                        <p>LP0000001-DNA</p>
                    </td>
                    <td style="color: #3E7EBE;">
                        <p>C01</p>
                    </td>
                </tr>
                <tr>
                    <td>
                        <p><i>more biosamples...</i></p>
                    </td>
                    <td style="color: #0000cd;">
                        <p>&#160;</p>
                    </td>
                    <td style="color: #0000cd;">
                        <p>&#160;</p>
                    </td>
                    <td style="color: #0000cd;">
                        <p />
                    </td>
                </tr>
            </tbody>
        </table>

##Prep Request Columns

The Prep Request and Required Yield Gbp columns are both optional columns that
are used to tell a connected lab software system (LIMS) how to prepare
biosamples into libraries. 

- **Prep Request**—This column specifies which library prep kit to use.
- **Required Yield Gbp**—If a Prep Request is entered, this column is required. It specifies how much sequencing yield the lab is required to produce to sufficiently launch the planned BaseSpace app. 

###Prep Request Data Requirements

- If a Prep Request is entered, Required Yield Gbp must also be entered
- Required Yield Gbp must be a value between 0-1000 (fractions can be used to specify units of Mbp or kbp)

###Example
<table class="table table-bordered">
            <col />
            <col />
            <thead>
                <tr>
                    <th style="color: #c5246E;">
                        <p style="text-align: left;">Prep Request</p>
                    </th>
                    <th style="color: #c5246E;">
                        <p style="text-align: left;">Required Yield Gbp</p>
                    </th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td style="color: #c5246E;">
                        <p>TruSeq PCR-Free
 High Throughput</p>
                    </td>
                    <td style="color: #c5246E;">
                        <p>105</p>
                    </td>
                </tr>
                <tr>
                    <td style="color: #c5246E;">
                        <p>TruSeq PCR-Free
 High Throughput</p>
                    </td>
                    <td style="color: #c5246E;">
                        <p>105</p>
                    </td>
                </tr>
                <tr>
                    <td style="color: #c5246E;">
                        <p>TruSeq PCR-Free
 High Throughput</p>
                    </td>
                    <td style="color: #c5246E;">
                        <p>105</p>
                    </td>
                </tr>
                <tr>
                    <td>
                        <p><i>more biosamples...</i>
                        </p>
                    </td>
                    <td>
                        <p>&#160;</p>
                    </td>
                </tr>
            </tbody>
        </table>
Example prep requests:

- TruSeq PCR-Free High Throughput
- TruSeq Nano High Throughput

##Analysis Workflow Columns

[Analysis Workflows](https://confluence.illumina.com/display/BS/Analysis+Workflows+for+Auto-App+Launch) are used to schedule a BaseSpace app to automatically perform analysis on BioSamples. The workflow defines the app version, settings, and launch dependencies, as well as optional analysis QC thresholds. 

The BioSample manifest analysis workflow columns configure the workflow settings. Once applied, the platform will schedule an Analyses using a workflow's app version, launch the Analyses once dependencies are met, and perform analysis QC when the Analyses complete successfully.

- **Analysis Group**—Groups multiple rows in a BioSample manifest file. This
column is necessary only for Analysis Workflows that require input data from
multiple BioSamples. For example, a Tumor/Normal Analysis Workflow requires as
input the output of Isaac Analyses of both tumor and normal BioSamples. Note
that it does not matter which BioSample in the group the Tumor/Normal workflow
is scheduled for. <br />
When an Analysis Group is used, parentheses must be added to the relevant
Analysis Workflow name. The Analysis Group only applies within a single
BioSample manifest file, so it is not possible to apply the same group across
different manifest files.
- **Sample Label**—Labels Analysis Workflow inputs that must be distinguished. For example, the Tumor/Normal Analysis Workflow requires that the Isaac Analyses input be labeled with 'Normal' and 'Tumor' (case-sensitive).
- **Delivery Mode**—Assigns an optional Delivery status for an Analysis during accessioning. For example, Analyses can be marked as 'Do Not Deliver' when they shouldn't be delivered or shared outside the sequencing lab, such as for R&D or test analyses. 

###Analysis Workflow Data Requirements

- The **Analysis Workflow** must exist in BaseSpace, and the user must have permission to use the analysis workflow.
- The **Analysis Group**, if provided, must be unique within the manifest file.
- The **Sample Label**, if provided, must be unique among the rows that have the same Analysis Group.
- The **Delivery Mode**, if provided, must be one of the following: 'Deliver' or 'Do Not Deliver'. The Delivery Mode must be the same among BioSamples in the same Analysis Group.

###Scheduling Multiple Analysis Workflows for the Same BioSample

A given BioSample may only be listed in a single row of a manifest file. To schedule multiple Analyses Workflows for a BioSample in the same manifest file, separate the names of Analysis Workflows with a pipe character "\|". This is equivalent to creating multiple manifest files, each containing a single Analysis workflow for the BioSample.

[//]: # (Note that the pipe character does not imply chaining as in UNIX; instead, it indicates that one workflow 'and' another workflow be executed. Primitive app chaining is a supported feature, but the logic is encoded within specific
Analysis Workflow themselves (not in the manifest file). For example, the Tumor/Normal workflow requires as input the output of the Isaac app from tumor and normal BioSamples (this is accomplished with an 'app completion' dependency defined in the Analysis Workflow).)

If the same BioSample manifest is imported twice, the system will duplicate all
requests in the manifest. So two Analyses will be scheduled for every BioSample
listed with an Analysis Workflow(s) in the manifest.

###Example Columns

<table class="table table-bordered">
            
            <thead>
                <tr style="color: 885087;">
                    <th>
                        BioSample Namexxxxxxxxxxxxxxxxxxxxxxxxxxxxxxx
                    </th>
                    <th style="text-align: left;color: 885087">
                        <p>...</p>
                    </th>
                    <th style="text-align: left;color: 81af45;">
                        <p>Analysis Workflow</p>
                    </th>
                    <th style="text-align: left;color: 81af45;">
                        <p>Analysis Group</p>
                    </th>
                    <th style="text-align: left;color: 81af45;">
                        <p>Sample Label</p>
                    </th>
                    <th style="text-align: left;color: 81af45;">
                        <p>Delivery Mode</p>
                    </th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td style="color: 81af45;">
                        <p>BioSample1</p>
                    </td>
                    <td style="color: 81af45;">
                        <p>&#160;</p>
                    </td>
                    <td style="color: 81af45;">
                        <p>IsaacV4.0WF-ANY</p>
                    </td>
                    <td style="color: 81af45;">
                        <p>&#160;</p>
                    </td>
                    <td style="color: 81af45;">
                        <p>&#160;</p>
                    </td>
                    <td style="color: 81af45;">
                        <p>Do Not Deliver</p>
                    </td>
                </tr>
                <tr>
                    <td style="color: 81af45;">
                        <p>BioSample2</p>
                    </td>
                    <td style="color: 81af45;">
                        <p>&#160;</p>
                    </td>
                    <td style="color: 81af45;">
                        <p>IsaacV4.0WF-ANY |
 (TumorNormalV1.1WF-ANY)</p>
                    </td>
                    <td style="color: 81af45;">
                        <p>analysis1234</p>
                    </td>
                    <td style="color: 81af45;">
                        <p>Normal</p>
                    </td>
                    <td style="color: 81af45;">
                        <p>&#160;</p>
                    </td>
                </tr>
                <tr>
                    <td style="color: 81af45;">
                        <p>BioSample3</p>
                    </td>
                    <td style="color: 81af45;">
                        <p>&#160;</p>
                    </td>
                    <td style="color: 81af45;">
                        <p>IsaacV4.0WF-ANY</p>
                    </td>
                    <td style="color: 81af45;">
                        <p>analysis1234</p>
                    </td>
                    <td style="color: 81af45;">
                        <p>Tumor</p>
                    </td>
                    <td style="color: 81af45;">
                        <p>&#160;</p>
                    </td>
                </tr>
                <tr>
                    <td style="color: 81af45;">
                        <p>&#160;</p>
                    </td>
                    <td style="color: 81af45;">
                        <p>&#160;</p>
                    </td>
                    <td style="color: 81af45;">
                        <p>more biosamples...</p>
                    </td>
                    <td style="color: 81af45;">
                        <p>&#160;</p>
                    </td>
                    <td style="color: 81af45;">
                        <p>&#160;</p>
                    </td>
                    <td style="color: 81af45;">
                        <p>&#160;</p>
                    </td>
                </tr>
            </tbody>
        </table>

###Example Using Multiple Manifest Files

The following manifest files in combination are equivalent to the one above.
This use case may occur if a 'normal' BioSample arrives in a lab significantly
earlier than a 'tumor' BioSample. The normal sample can be sequenced and analyzed
with Isaac before the tumor BioSample arrives in the lab. Once the tumor
arrives, both Isaac and tumor/normal subtraction analyses can be scheduled.

####Manifest 1 of 2

<table class="table table-bordered">
            <col />
            <col />
            <col />
            <col />
            <col />
            <col />
            <thead>
                <tr style="text-align: left;">
                    <th style="color: #009900;">
                        <p>BioSample Name
  
  </p>
                    </th>
                    <th style="color: #009900;">
                        <p>...</p>
                    </th>
                    <th style="color: #009900;">
                        <p>Analysis Workflow</p>
                    </th>
                    <th style="color: #009900;">
                        <p>Analysis Group</p>
                    </th>
                    <th style="color: #009900;">
                        <p>Sample Label</p>
                    </th>
                    <th style="color: #009900;">
                        <p>Delivery Mode</p>
                    </th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td style="color: #009900;">
                        <p>BioSample1</p>
                    </td>
                    <td style="color: #009900;">
                        <p>&#160;</p>
                    </td>
                    <td style="color: #009900;">
                        <p>IsaacV4.0WF-ANY</p>
                    </td>
                    <td style="color: #009900;">
                        <p>&#160;</p>
                    </td>
                    <td style="color: #009900;">
                        <p>&#160;</p>
                    </td>
                    <td style="color: #009900;">
                        <p>Do Not Deliver</p>
                    </td>
                </tr>
                <tr>
                    <td style="color: #009900;">
                        <p>BioSample2</p>
                    </td>
                    <td style="color: #009900;">
                        <p>&#160;</p>
                    </td>
                    <td style="color: #009900;">
                        <p>IsaacV4.0WF-ANY</p>
                    </td>
                    <td>
                        <p>&#160;</p>
                    </td>
                    <td>
                        <p>&#160;</p>
                    </td>
                    <td>
                        <p>&#160;</p>
                    </td>
                </tr>
            </tbody>
        </table>

###Manifest 2 of 2

<table class="table table-bordered">
            <col />
            <col />
            <col />
            <col />
            <col />
            <col />
            <thead>
                <tr>
                    <th style="text-align: left;color: #009900;">
                        <p>BioSample Name
  
  </p>
                    </th>
                    <th style="text-align: left;color: #009900;">
                        <p>...</p>
                    </th>
                    <th style="text-align: left;color: #009900;">
                        <p>Analysis Workflow</p>
                    </th>
                    <th style="text-align: left;color: #009900;">
                        <p>Analysis Group</p>
                    </th>
                    <th style="text-align: left;color: #009900;">
                        <p>Sample Label</p>
                    </th>
                    <th style="text-align: left;color: #009900;">
                        <p>Delivery Mode</p>
                    </th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td style="color: #009900;">
                        <p>BioSample2</p>
                    </td>
                    <td style="color: #009900;">
                        <p>&#160;</p>
                    </td>
                    <td style="color: #009900;">
                        <p>(TumorNormalV1.1WF-ANY)</p>
                    </td>
                    <td style="color: #009900;">
                        <p>analysis1234</p>
                    </td>
                    <td style="color: #009900;">
                        <p>Normal</p>
                    </td>
                    <td style="color: #009900;">
                        <p>&#160;</p>
                    </td>
                </tr>
                <tr>
                    <td style="color: #009900;">
                        <p>BioSample3</p>
                    </td>
                    <td style="color: #009900;">
                        <p>&#160;</p>
                    </td>
                    <td style="color: #009900;">
                        <p>IsaacV4.0WF-ANY</p>
                    </td>
                    <td style="color: #009900;">
                        <p>analysis1234</p>
                    </td>
                    <td style="color: #009900;">
                        <p>Tumor</p>
                    </td>
                    <td style="color: #009900;">
                        <p>&#160;</p>
                    </td>
                </tr>
            </tbody>
        </table>

Note that the Isaac Analysis Workflow for BioSample 2 is only entered once (in
the first manifest). The output of this Analysis will be used by the
Tumor/Normal Analysis scheduled in the second manifest.

##Metadata Columns

Custom metadata can be added to new BioSamples by entering in new column headers in
the same row as the required column headers. These custom key-value pairs are displayed on the BioSample Details page. Adding values in these columns is optional.
 
The manifest file cannot be used to add or edit metadata for existing BioSamples.

In the following example columns, the Tissue Source column indicates that one BioSample came from Lung tissue and another came from Liver tissue; the tissue source for a third BioSample is undefined. 


###Example
<table class="table table-bordered">
            <col />
            <col />
            <thead>
                <tr>
                    <th style="text-align: left;color: 885087;">
                        <p>Tissue Source</p>
                    </th>
                    <th style="text-align: left;color: 885087;">
                        <p>Customer Barcode</p>
                    </th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td style="color: 885087;">
                        <p>Lung</p>
                    </td>
                    <td style="color: 885087;">
                        <p>ID-1498124</p>
                    </td>
                </tr>
                <tr>
                    <td style="color: 885087;">
                        <p>Liver</p>
                    </td>
                    <td style="color: 885087;">
                        <p>ID-1498125</p>
                    </td>
                </tr>
                <tr>
                    <td style="color: 885087;">
                        <p>&#160;</p>
                    </td>
                    <td style="color: 885087;">
                        <p>ID-1498126</p>
                    </td>
                </tr>
                <tr>
                    <td style="color: #000000;">
                        <p style="font-style: italic;">more biosamples...</p>
                    </td>
                    <td style="color: #000000;">
                        <p>&#160;</p>
                    </td>
                </tr>
            </tbody>
        </table>



##Adding to Existing BioSamples

When an existing BioSample Name is listed in the manifest, only the entries in the Prep Request and Analysis columns are imported. Although the Default Project column is required in the manifest, entries related to duplicate BioSamples are ignored.

##Adding or Updating New Prep Requests

Users can add a new Prep Request to an existing BioSample by using an already
existing BioSample Name and inputting a new Prep Request name. BaseSpace will
add the new Prep Request for the same BioSample and inform the LIMS that a new
library made with the specified kit should be prepped.

If an Prep Request already exists for the BioSample Name, the Required Yield Gbp value is updated for that BioSample and Prep Request.

All other columns in the manifest, including container and metadata columns, are ignored. 

##Scheduling Additional Analysis Workflows

Users can schedule additional Analysis Workflow for an existing BioSample by
entering in an existing BioSample Name and an Analysis Workflow.

###Requirements

- If you are scheduling an analysis workflow with more than one existing BioSample,
all existing BioSamples must have been imported from same manifest. 
- If the manifest user is not the BioSample owner, a new BioSample with the same name is imported with the user as the owner.

####Update Prep Request Example
<table class="table table-bordered">
            <col />
            <col />
            <col />
            <col />
            <thead>
                <tr>
                    <th style="text-align: left;color: 3e7ebe;">
                        <p>BioSample Name</p>
                    </th>
                    <th style="text-align: left;color: 3e7ebe;">
                        <p>Default Project</p>
                    </th>
                    <th style="text-align: left;color: c5246e;">
                        <p>Prep Request</p>
                    </th>
                    <th style="text-align: left;color: c5246e;">
                        <p>Required Yield
 Gbp</p>
                    </th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td style="color: 3e7ebe;">
                        <p>LP0000001-DNA_A01</p>
                    </td>
                    <td style="color: 3e7ebe;">
                        <p>&#160;</p>
                    </td>
                    <td style="color: c5246e;">
                        <p>TruSeq
 PCR-Free High Throughput</p>
                    </td>
                    <td style="color: c5246e;">
                        <p>555</p>
                    </td>
                </tr>
                <tr>
                    <td style="color: 3e7ebe;">
                        <p>LP0000001-DNA_B01</p>
                    </td>
                    <td style="color: 3e7ebe;">
                        <p>&#160;</p>
                    </td>
                    <td style="color: c5246e;">
                        <p>TruSeq
 PCR-Free High Throughput</p>
                    </td>
                    <td style="color: c5246e;">
                        <p>747</p>
                    </td>
                </tr>
            </tbody>
        </table>


####Update Analysis Workflow Example
 <table class="table table-bordered">
           
            <thead>
                <tr>
                    <th>Lane</th>
                    <th>Sample_ID</th>
                    <th>Sample_Name</th>
                    <th>Sample_Plate</th>
                    <th>Sample_Well</th>
                    <th>Index</th>
                    <th>Index2</th>
                    <th>Project_Name</th>
                    <th>description</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>1</td>
                    <td>LP1234567-DNA_A01</td>
                    <td>LP1234567-NTP_A01</td>
                    <td>LP1234567-DNA</td>
                    <td>A01</td>
                    <td>ATTACTCG</td>
                    <td>ATTACTCC</td>
                    <td>Proj1</td>
                    <td>2-40131</td>
                </tr>
                <tr>
                    <td>2</td>
                    <td>LP1234567-DNA_B01</td>
                    <td>LP1234567-NTP_B01</td>
                    <td>LP1234567-DNA</td>
                    <td>B01</td>
                    <td>ATTACTCG</td>
                    <td>ATTACTCC</td>
                    <td>Proj1</td>
                    <td>2-40132</td>
                </tr>
                <tr>
                    <td>3</td>
                    <td>LP1234567-DNA_C01</td>
                    <td>LP1234567-NTP_C01</td>
                    <td>LP1234567-DNA</td>
                    <td>C01</td>
                    <td>ATTACTCG</td>
                    <td>ATTACTCC</td>
                    <td>Proj1</td>
                    <td>2-40133</td>
                </tr>
            </tbody>
        </table> 

##Using Sample Sheets with the BioSample Manifest

For non-LIMS users, data are uploaded to BaseSpace with an accompanying
sample sheet .csv file placed in the instrument's run folder. The sample sheet contains the names of the BioSamples and libraries put onto flowcell lanes.
BaseSpace uses this information to create datasets for the matching
BioSamples and link newly generated libraries and/or pools.

##Column Mapping

<table class="table table-bordered">
            <col />
            <col />
            <col />
            <thead>
                <tr>
                    <th style="text-align: left;">Sample Sheet Column</th>
                    <th style="text-align: left;">BaseSpace Column</th>
                    <th style="text-align: left;">Notes</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>Lane </td>
                    <td>Lane</td>
                    <td>Optional. If omitted, the row applies to all lanes.</td>
                </tr>
                <tr>
                    <td>  Sample_ID</td>
                    <td>BioSample Name</td>
                    <td>Required</td>
                </tr>
                <tr>
                    <td>  Sample_Name</td>
                    <td>Library Name</td>
                    <td>Optional</td>
                </tr>
                <tr>
                    <td>  Sample_Plate</td>
                    <td>Container Name</td>
                    <td>Optional</td>
                </tr>
                <tr>
                    <td>  Sample_Well </td>
                    <td>Container Position</td>
                    <td>Optional</td>
                </tr>
            </tbody>
        </table>

-   **Lane** (optional) in the sample sheet maps to **Lane** in BaseSpace (if
    omitted the row applies to all lanes)

-   **Sample\_ID** (required) in the sample sheet maps to **BioSample Name** in
    BaseSpace

-   **Sample Name** (optionsal) in the sample sheet maps to **Library Name** in
    BaseSpace

-   **Sample\_Plate** (optional) in the sample sheet maps to **Container Name**
    in BaseSpace

-   **Sample\_Well** (optional) in the sample sheet maps to **Container
    Position** in BaseSpace

If both the BioSample name and Library Name match an existing BioSample and
Library (from that BioSample), and the BioSample is owned by the Run Owner, then
data from the Run will be associated with the existing BioSample and Library. If
only the BioSample name matches an existing BioSample, then a new Library will
created under the existing BioSample, and new Run data will be associated with
the existing BioSample and new Library. If the BioSample Name does not match an
existing BioSample that is owned by the Run owner, then a new BioSample and
Library will be created and Run data associated with them.

The SampleSheet does not contain the Prep Kit that was used to generate each
Library. So, if the BioSample listed in the SampleSheet has an active Lab
Workflow, then the Library is assumed to be the Prep Kit type of the Lab
Workflow. Otherwise, the Library's Prep Kit is set to 'Unknown'.

Validation
----------

**You must match Sample\_ID in the sample sheet to the BioSample Name** entered
into the BaseSpace manifest import. This links the scheduled analysis set for
the BioSample to the yield in any data that is uploaded, via the CLI or web
importer tool. The same logic applies for auto-app launch where if the required
yield for the BioSample is met, the scheduled analysis will auto-launch. If the
Sample\_ID does not match exactly, BaseSpace **cannot** associate the uploaded
data to an existing BioSample and will create new BioSamples that do not have
scheduled analyses.

![](media/4d860c180f4576fe322b7525b9ee739b.png)
 <table class="table table-bordered">
           
            <thead>
                <tr class="TableStyle-Horiz-Head-Header1">
                    <th style="text-align: left;" class="TableStyle-Horiz-HeadE-Column1-Header1">
                        <p>Lane</p>
                    </th>
                    <th style="text-align: left;" class="TableStyle-Horiz-HeadE-Column1-Header1">
                        <p>Sample_ID</p>
                    </th>
                    <th style="text-align: left;" class="TableStyle-Horiz-HeadE-Column1-Header1">
                        <p>Sample_Name</p>
                    </th>
                    <th style="text-align: left;" class="TableStyle-Horiz-HeadE-Column1-Header1">
                        <p>Sample_Plate</p>
                    </th>
                    <th style="text-align: left;" class="TableStyle-Horiz-HeadE-Column1-Header1">
                        <p>Sample_Well</p>
                    </th>
                    <th style="text-align: left;" class="TableStyle-Horiz-HeadE-Column1-Header1">
                        <p>Index</p>
                    </th>
                    <th style="text-align: left;" class="TableStyle-Horiz-HeadE-Column1-Header1">
                        <p>Index2</p>
                    </th>
                    <th style="text-align: left;" class="TableStyle-Horiz-HeadE-Column1-Header1">
                        <p>Project_Name</p>
                    </th>
                    <th style="text-align: left;" class="TableStyle-Horiz-HeadD-Column1-Header1">
                        <p>description</p>
                    </th>
                </tr>
            </thead>
            <tbody>
                <tr class="TableStyle-Horiz-Body-Body1">
                    <td class="TableStyle-Horiz-BodyE-Column1-Body1">
                        <p>1</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyE-Column1-Body1">
                        <p>LP1234567-DNA_A01</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyE-Column1-Body1">
                        <p>LP1234567-NTP_A01</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyE-Column1-Body1">
                        <p>LP1234567-DNA</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyE-Column1-Body1">
                        <p>A01</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyE-Column1-Body1">
                        <p>ATTACTCG</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyE-Column1-Body1">
                        <p>ATTACTCC</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyE-Column1-Body1">
                        <p>Proj1</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyD-Column1-Body1">
                        <p>2-40131</p>
                    </td>
                </tr>
                <tr class="TableStyle-Horiz-Body-Body2">
                    <td class="TableStyle-Horiz-BodyE-Column1-Body2">
                        <p>2</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyE-Column1-Body2">
                        <p>LP1234567-DNA_B01</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyE-Column1-Body2">
                        <p>LP1234567-NTP_B01</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyE-Column1-Body2">
                        <p>LP1234567-DNA</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyE-Column1-Body2">
                        <p>B01</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyE-Column1-Body2">
                        <p>ATTACTCG</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyE-Column1-Body2">
                        <p>ATTACTCC</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyE-Column1-Body2">
                        <p>Proj1</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyD-Column1-Body2">
                        <p>2-40132</p>
                    </td>
                </tr>
                <tr class="TableStyle-Horiz-Body-Body1">
                    <td class="TableStyle-Horiz-BodyB-Column1-Body1">
                        <p>3</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyB-Column1-Body1">
                        <p>LP1234567-DNA_C01</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyB-Column1-Body1">
                        <p>LP1234567-NTP_C01</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyB-Column1-Body1">
                        <p>LP1234567-DNA</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyB-Column1-Body1">
                        <p>C01</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyB-Column1-Body1">
                        <p>ATTACTCG</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyB-Column1-Body1">
                        <p>ATTACTCC</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyB-Column1-Body1">
                        <p>Proj1</p>
                    </td>
                    <td class="TableStyle-Horiz-BodyA-Column1-Body1">
                        <p>2-40133</p>
                    </td>
                </tr>
            </tbody>
        </table>



 <table class="table table-bordered;style=margin-left: 0;margin-right: auto;">
            <col />
            <col />
            <col />
            <col />
            <col />
            <col />
            <col />
            <col />
            <col />
            <thead>
                <tr>
                    <th style="text-align: left;">
                        <p>Lane</p>
                    </th>
                    <th style="text-align: left;">
                        <p>Sample_ID</p>
                    </th>
                    <th style="text-align: left;">
                        <p>Sample_Name</p>
                    </th>
                    <th style="text-align: left;">
                        <p>Sample_Plate</p>
                    </th>
                    <th style="text-align: left;">
                        <p>Sample_Well</p>
                    </th>
                    <th style="text-align: left;">
                        <p>Index</p>
                    </th>
                    <th style="text-align: left;">
                        <p>Index2</p>
                    </th>
                    <th style="text-align: left;">
                        <p>Project_Name</p>
                    </th>
                    <th style="text-align: left;">
                        <p>description</p>
                    </th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td>
                        <p>1</p>
                    </td>
                    <td>
                        <p>LP1234567-DNA_A01</p>
                    </td>
                    <td>
                        <p>LP1234567-NTP_A01</p>
                    </td>
                    <td>
                        <p>LP1234567-DNA</p>
                    </td>
                    <td>
                        <p>A01</p>
                    </td>
                    <td>
                        <p>ATTACTCG</p>
                    </td>
                    <td>
                        <p>ATTACTCC</p>
                    </td>
                    <td>
                        <p>Proj1</p>
                    </td>
                    <td>
                        <p>2-40131</p>
                    </td>
                </tr>
                <tr>
                    <td>
                        <p>2</p>
                    </td>
                    <td>
                        <p>LP1234567-DNA_B01</p>
                    </td>
                    <td>
                        <p>LP1234567-NTP_B01</p>
                    </td>
                    <td>
                        <p>LP1234567-DNA</p>
                    </td>
                    <td>
                        <p>B01</p>
                    </td>
                    <td>
                        <p>ATTACTCG</p>
                    </td>
                    <td>
                        <p>ATTACTCC</p>
                    </td>
                    <td>
                        <p>Proj1</p>
                    </td>
                    <td>
                        <p>2-40132</p>
                    </td>
                </tr>
                <tr>
                    <td>
                        <p>3</p>
                    </td>
                    <td>
                        <p>LP1234567-DNA_C01</p>
                    </td>
                    <td>
                        <p>LP1234567-NTP_C01</p>
                    </td>
                    <td>
                        <p>LP1234567-DNA</p>
                    </td>
                    <td>
                        <p>C01</p>
                    </td>
                    <td>
                        <p>ATTACTCG</p>
                    </td>
                    <td>
                        <p>ATTACTCC</p>
                    </td>
                    <td>
                        <p>Proj1</p>
                    </td>
                    <td>
                        <p>2-40133</p>
                    </td>
                </tr>
            </tbody>
        </table>

##Example Manifests


[BaseSpace Manifest Import no templates.csv](https://confluence.illumina.com/download/attachments/105393997/BaseSpace%20Manifest%20Import%20no%20templates.csv?version=2&modificationDate=1456366067509&api=v2)

[BaseSpace Manifest Import Example with templates.csv](https://confluence.illumina.com/download/attachments/105393997/BaseSpace%20Manifest%20Import%20Example%20with%20templates.csv?version=2&modificationDate=1456366067368&api=v2)

 <table class="table table-bordered">
            
            <thead>
                <tr>
                    <th style="color: #3e7ebe;">BioSample Name</th>
                    <th style="color: #3e7ebe;">Default Project</th>
                    <th style="color: #3e7ebe;">Container Name</th>
                    <th style="color: #3e7ebe;">Container Position</th>
                    <th style="color: #c5246e;">Prep Request</th>
                    <th style="color: #c5246e;">Required Yield Gbp</th>
                    <th style="color: #6c923a;">Analysis Workflow</th>
                    <th style="color: #6c923a;">Analysis Group</th>
                    <th style="color: #6c923a;">Sample Label</th>
                    <th style="color: #885087;">Delivery Mode</th>
                    <th style="color: #885087;">Tissue Source</th>
                    <th style="color: #885087;">Customer Barcode</th>
                </tr>
            </thead>
            <tbody>
                <tr>
                    <td style="color: #3e7ebe;">LP0000001-DNA_A01</td>
                    <td style="color: #3e7ebe;">TestProject</td>
                    <td style="color: #3e7ebe;">LP0000001-DNA</td>
                    <td style="color: #3e7ebe;">A01</td>
                    <td style="color: #c5246e;">TruSeq PCR-Free High Throughput</td>
                    <td style="color: #c5246e;">105</td>
                    <td style="color: #6c923a;">IsaacV4.0WF-ANY</td>
                    <td style="color: #6c923a;">&#160;</td>
                    <td style="color: #6c923a;">&#160;</td>
                    <td style="color: #885087;">&#160;</td>
                    <td style="color: #885087;">Lung</td>
                    <td style="color: #885087;">ID-1498124</td>
                </tr>
                <tr>
                    <td style="color: #3e7ebe;">LP0000001-DNA_B01</td>
                    <td style="color: #3e7ebe;">TestProject</td>
                    <td style="color: #3e7ebe;">LP0000001-DNA</td>
                    <td style="color: #3e7ebe;">B01</td>
                    <td style="color: #c5246e;">TruSeq PCR-Free High
						Throughput</td>
                    <td style="color: #c5246e;">105</td>
                    <td style="color: #6c923a;">IsaacV4.0WF-ANY</td>
                    <td style="color: #6c923a;">&#160;</td>
                    <td style="color: #6c923a;">&#160;</td>
                    <td style="color: #885087;">Do Not Deliver</td>
                    <td style="color: #885087;">Liver</td>
                    <td style="color: #885087;">ID-1498125</td>
                </tr>
                <tr>
                    <td style="color: #3e7ebe;">LP0000001-DNA_C01</td>
                    <td style="color: #3e7ebe;">TestProject</td>
                    <td style="color: #3e7ebe;">LP0000001-DNA</td>
                    <td style="color: #3e7ebe;">C01</td>
                    <td style="color: #c5246E;">TruSeq PCR-Free High
						Throughput</td>
                    <td style="color: #c5246E;">105</td>
                    <td style="color: #6c923a;">IsaacV4.0WF-ANY</td>
                    <td style="color: #6c923a;">&#160;</td>
                    <td style="color: #6c923a;">&#160;</td>
                    <td style="color: #885087;">Deliver</td>
                    <td style="color: #885087;">&#160;</td>
                    <td style="color: #885087;">ID-1498126</td>
                </tr>
                <tr>
                    <td style="color: #3e7ebe;">LP0000001-DNA_D01</td>
                    <td style="color: #3e7ebe;">TestProject</td>
                    <td style="color: #3e7ebe;">LP0000001-DNA</td>
                    <td style="color: #3e7ebe;">D01</td>
                    <td style="color: #c5246E;">TruSeq PCR-Free High
						Throughput</td>
                    <td style="color: #c5246E;">105</td>
                    <td style="color: #6c923a;">IsaacV4.0WF-ANY</td>
                    <td style="color: #6c923a;">&#160;</td>
                    <td style="color: #6c923a;">&#160;</td>
                    <td style="color: #885087;">Deliver</td>
                    <td style="color: #885087;">&#160;</td>
                    <td style="color: #885087;">ID-1498127</td>
                </tr>
                <tr>
                    <td style="color: #3e7ebe;">LP0000001-DNA_E01</td>
                    <td style="color: #3e7ebe;">TestProject</td>
                    <td style="color: #3e7ebe;">LP0000001-DNA</td>
                    <td style="color: #3e7ebe;">E01</td>
                    <td style="color: #c5246E;">TruSeq Nano High Throughput</td>
                    <td style="color: #c5246E;">105</td>
                    <td style="color: #6c923a;">IsaacV4.0WF-ANY</td>
                    <td style="color: #6c923a;">&#160;</td>
                    <td style="color: #6c923a;">&#160;</td>
                    <td style="color: #885087;">Do Not Deliver</td>
                    <td style="color: #885087;">&#160;</td>
                    <td style="color: #885087;">ID-1498128</td>
                </tr>
                <tr>
                    <td style="color: #3e7ebe;">LP0000001-DNA_F01</td>
                    <td style="color: #3e7ebe;">TestProject</td>
                    <td style="color: #3e7ebe;">LP0000001-DNA</td>
                    <td style="color: #3e7ebe;">F01</td>
                    <td style="color: #c5246E;">TruSeq Nano High Throughput</td>
                    <td style="color: #c5246E;">105</td>
                    <td style="color: #6c923a;">IsaacV4.0WF-ANY</td>
                    <td style="color: #6c923a;">&#160;</td>
                    <td style="color: #6c923a;">&#160;</td>
                    <td style="color: #885087;">Do Not Deliver</td>
                    <td style="color: #885087;">&#160;</td>
                    <td style="color: #885087;">ID-1498129</td>
                </tr>
                <tr>
                    <td style="color: #3e7ebe;">LP0000001-DNA_G01</td>
                    <td style="color: #3e7ebe;">TestProject_tumor</td>
                    <td style="color: #3e7ebe;">LP0000001-DNA</td>
                    <td style="color: #3e7ebe;">G01</td>
                    <td style="color: #c5246E;">TruSeq Nano High Throughput</td>
                    <td style="color: #c5246E;">105</td>
                    <td style="color: #6c923a;">IsaacV4.0WF-ANY |
						(TumorNormalV1.1WF-ANY)</td>
                    <td style="color: #6c923a;">analysis1234</td>
                    <td style="color: #6c923a;">Normal</td>
                    <td style="color: #885087;">Deliver</td>
                    <td style="color: #885087;">&#160;</td>
                    <td style="color: #885087;">ID-1498130</td>
                </tr>
                <tr>
                    <td style="color: #3e7ebe;">LP0000001-DNA_H01</td>
                    <td style="color: #3e7ebe;">TestProject_tumor</td>
                    <td style="color: #3e7ebe;">LP0000001-DNA</td>
                    <td style="color: #3e7ebe;">H01</td>
                    <td style="color: #c5246E;">TruSeq Nano High Throughput</td>
                    <td style="color: #c5246E;">105</td>
                    <td style="color: #6c923a;">IsaacV4.0WF-ANY</td>
                    <td style="color: #6c923a;">analysis1234</td>
                    <td style="color: #6c923a;">Tumor</td>
                    <td style="color: #885087;">Deliver</td>
                    <td style="color: #885087;">&#160;</td>
                    <td style="color: #885087;">ID-1498131</td>
                </tr>
            </tbody>
        </table>

Each row of the BioSample manifest specifies a new or existing BioSample and the
information about that BioSample. There are specific validations BaseSpace
performs on the values in each column of the manifest to assist the
sample-to-answer process being automated. These validations are explained in the
sections below.