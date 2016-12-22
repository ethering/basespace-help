---
layout: article
title: Biosample Manifest Import
hide_welcome_banner: true
---
##Biosample Manifest Import


##Intro to Biosample Manifests


The Biosample Manifest file allow BaseSpace users to import new Bioamples in
bulk, add library prep instructions, add auto-launchable Analysis Workflows, and
add metadata key-value pairs to the new Biosamples. Users can also add
additional library prep instructions and add auto-launchable Analysis Workflows
to already existing Biosamples. This page explains the structure of the
Biosample manifest file.

-   [Intro to Biosample Manifests](#intro-to-biosample-manifests)

-   [Full Examples](#full-examples)

-   [File Formatting](#file-formatting)

-   [Adding Biosamples and Projects](#adding-biosamples-and-projects)

-   [Adding Prep Requests to Create
    Libraries](#adding-prep-requests-to-create-libraries)

-   [Scheduling Analyses for Auto-app
    Launch](#scheduling-analyses-for-auto-app-launch)

-   [Adding Metadata to Biosamples](#adding-metadata-to-biosamples)

-   [Adding to Existing Biosamples](#adding-to-existing-biosamples)

-   [Using Sample Sheets with the Biosample
    Manifest](#using-sample-sheets-with-the-biosample-manifest)

![](media/b742294055b9c4ba488ba32598c8e973.png)

Full Examples

[BaseSpace Manifest Import no
templates.csv](https://confluence.illumina.com/download/attachments/105393997/BaseSpace%20Manifest%20Import%20no%20templates.csv?version=2&modificationDate=1456366067509&api=v2)

[BaseSpace Manifest Import Example with
templates.csv](https://confluence.illumina.com/download/attachments/105393997/BaseSpace%20Manifest%20Import%20Example%20with%20templates.csv?version=2&modificationDate=1456366067368&api=v2)

| **BioSample Name** | **Default Project** | **Container Name** | **Container Position** | **Prep Request**                | **Required Yield Gbp** | **Analysis Workflow**                      | **Analysis Group** | **Sample Label** | **Delivery Mode** | **Tissue Source** | **Customer Barcode** |
|--------------------|---------------------|--------------------|------------------------|---------------------------------|------------------------|--------------------------------------------|--------------------|------------------|-------------------|-------------------|----------------------|
| LP0000001-DNA\_A01 | TestProject         | LP0000001-DNA      | A01                    | TruSeq PCR-Free High Throughput | 105                    | IsaacV4.0WF-ANY                            |                    |                  |                   | Lung              | ID-1498124           |
| LP0000001-DNA\_B01 | TestProject         | LP0000001-DNA      | B01                    | TruSeq PCR-Free High Throughput | 105                    | IsaacV4.0WF-ANY                            |                    |                  | Do Not Deliver    | Liver             | ID-1498125           |
| LP0000001-DNA\_C01 | TestProject         | LP0000001-DNA      | C01                    | TruSeq PCR-Free High Throughput | 105                    | IsaacV4.0WF-ANY                            |                    |                  | Deliver           |                   | ID-1498126           |
| LP0000001-DNA\_D01 | TestProject         | LP0000001-DNA      | D01                    | TruSeq PCR-Free High Throughput | 105                    | IsaacV4.0WF-ANY                            |                    |                  | Deliver           |                   | ID-1498127           |
| LP0000001-DNA\_E01 | TestProject         | LP0000001-DNA      | E01                    | TruSeq Nano High Throughput     | 105                    | IsaacV4.0WF-ANY                            |                    |                  | Do Not Deliver    |                   | ID-1498128           |
| LP0000001-DNA\_F01 | TestProject         | LP0000001-DNA      | F01                    | TruSeq Nano High Throughput     | 105                    | IsaacV4.0WF-ANY                            |                    |                  | Do Not Deliver    |                   | ID-1498129           |
| LP0000001-DNA\_G01 | TestProject\_tumor  | LP0000001-DNA      | G01                    | TruSeq Nano High Throughput     | 105                    | IsaacV4.0WF-ANY \| (TumorNormalV1.1WF-ANY) | analysis1234       | Normal           | Deliver           |                   | ID-1498130           |
| LP0000001-DNA\_H01 | TestProject\_tumor  | LP0000001-DNA      | H01                    | TruSeq Nano High Throughput     | 105                    | IsaacV4.0WF-ANY                            | analysis1234       | Tumor            | Deliver           |                   | ID-1498131           |

Each row of the Biosample manifest specifies a new or existing Biosample and the
information about that Biosample. There are specific validations BaseSpace
performs on the values in each column of the manifest to assist the
sample-to-answer process being automated. These validations are explained in the
sections below.

##File Formatting

Headers

The purpose of file formatting is knowing where to parse the columns headers and
values in the manifest. They are not required when adding Biosamples. They will
eventually be required when more sections of data other than Biosamples need to
be bulk imported in future releases.

Formatting Validation

1.  Column headers of BioSample Name and Default Project are required

2.  Max number of columns are 100

3.  Column headers must be between 4-60 characters

4.  Column headers must not have special characters

5.  Column headers must not have empty columns between other column headers

Example
-------

| [Header]           |                     |                    |
|--------------------|---------------------|--------------------|
| FileVersion        | 1                   |                    |
| [Data]             |                     |                    |
| **BioSample Name** | **Default Project** | **Container Name** |
| *value...*         | *value...*          | *value...*         |

##Adding Biosamples and Projects


In these four columns, we are defining the biosamples we are adding or updating
to BaseSpace. The Biosample name is a unique identifier for the source DNA. If a
user tries importing a biosample name that already exists, they will see a
warning informing them that they will be adding information to the existing
biosample instead of creating a new one (see the existing biosample logic
section below).

The default project column defines where data that shows up for that biosample
will be stored by default. If the default project doesn't exist, a new project
will be created for the user. Container name and container position are most
commonly the source DNA plate barcode and the well location of that plate,
respectively, the DNA exists in. They are both optional.

Biosample Validation
--------------------

1.  Biosample name and default project values are required

2.  Biosample name must be unique in the manifest (i.e. a given Biosample can be
    present in only one row of the manifest)

3.  When container name is entered, container position is required

4.  Container name must be new to the system for the user

5.  Biosample name contains no spaces or special characters

Example
-------

| **BioSample Name**   | **Default Project** | **Container Name** | **Container Position** |
|----------------------|---------------------|--------------------|------------------------|
| LP0000001-DNA\_A01   | TestProject         | LP0000001-DNA      | A01                    |
| LP0000001-DNA\_B01   | TestProject         | LP0000001-DNA      | B01                    |
| LP0000001-DNA\_C01   | TestProject         | LP0000001-DNA      | C01                    |
| *more biosamples...* |                     |                    |                        |

##Adding Prep Requests to Create Libraries


The Prep Request and Required Yield Gbp columns are both optional columns that
are used to tell a connected lab software system (LIMS) how to prepare
biosamples into libraries. The Prep Request value specifies which library prep
kit to use and the Required Yield Gbp value specifies how much sequencing yield
the lab is required to produce to sufficiently launch the planned BaseSpace app.

Lab Workflow Validation
-----------------------

1.  Prep Request must be recognized by BaseSpace

2.  When Prep Request is entered, Required Yield Gbp must also be entered

3.  Required Yield Gbp must be a value between 0-1000 (fractions allowed to
    specify units of Mbp or kbp

Example
-------

| **Prep Request**                | **Required Yield Gbp** |
|---------------------------------|------------------------|
| TruSeq PCR-Free High Throughput | 105                    |
| TruSeq PCR-Free High Throughput | 105                    |
| TruSeq PCR-Free High Throughput | 105                    |
| *more biosamples...*            |                        |

Example prep requests:

1.  TruSeq PCR-Free High Throughput

2.  TruSeq Nano High Throughput

##Scheduling Analyses for Auto-app Launch


[Analysis
Workflows](https://confluence.illumina.com/display/BS/Analysis+Workflows+for+Auto-App+Launch)
contain a predefined app version, app settings, app-launch dependencies, and
optional analysis QC thresholds. The Biosample manifest import allow users to
easily apply Analysis Workflows to new or existing Biosamples. Once applied, the
platform will schedule an Analyses using a workflow's app version, launch the
Analyses once dependencies are met, and perform analysis QC when the Analyses
complete successfully.

The **Analysis Group** groups multiple rows in a Biosample manifest file. This
column is necessary only for Analysis Workflows that require input data from
multiple Biosamples. For example, a Tumor/Normal Analysis Workflow requires as
input the output of Isaac Analyses of both tumor and normal Biosamples. Note
that it does not matter which Biosample in the group the Tumor/Normal workflow
is scheduled for.

When an Analysis Group is used, parentheses must be added to the relevant
Analysis Workflow name. The Analysis Group only applies within a single
Biosample manifest file, so it is not possible to apply the same group across
different manifest files.

The **Sample Label** is necessary only when an Analysis Workflow has inputs that
must be distinguished. For example, the Tumor/Normal Analysis Workflow requires
that the input Isaac Analyses be labeled with 'Normal' and 'Tumor'
(case-sensitive).

The **Delivery Mode** is an optional way to assign the Delivery status of an
Analysis during accessioning. For example, Analyses can be marked as 'Do Not
Deliver' when they shouldn't be delivered or shared outside the sequencing lab,
such as for R&D or test analyses.

Scheduling Multiple Analysis Workflows for the same Biosample
-------------------------------------------------------------

Since a given Biosample may only be listed in a single row of a manifest file,
there is a convention for scheduling multiple Analyses Workflows for a Biosample
in the same manifest file. This convention is to separate the names of Analysis
Workflows with a pipe character "\|". This mechanism is only a convenience, and
it would be equivalent to create multiple manifest files that each contain a
single Analysis workflow for the Biosample.

Note that the pipe character does not imply chaining as in UNIX; instead, it
indicates that one workflow 'and' another workflow be executed. Primitive app
chaining is a supported feature, but the logic is encoded within specific
Analysis Workflow themselves (not in the manifest file). For example, the
Tumor/Normal workflow requires as input the output of the Isaac app from tumor
and normal Biosamples (this is accomplished with an 'app completion' dependency
defined in the Analysis Workflow).

If the same Biosample manifest is imported twice, the system will duplicate all
requests in the manifest. So two Analyses will be scheduled for every Biosample
listed with an Analysis Workflow(s) in the manifest.

Auto-app Launch Validation
--------------------------

1.  The **Analysis Workflow** must exist in BaseSpace, and the user must have
    permission to use the analysis workflow.

2.  The **Analysis Group**, if provided, must be unique within the manifest
    file.

3.  The **Sample Label**, if provided, must be unique among the rows that have
    the same Analysis Group.

4.  The **Delivery Mode**, if provided, must be one of the following: 'Deliver'
    or 'Do Not Deliver'. The Delivery Mode must be the same among Biosamples in
    the same Analysis Group.

Example
-------

| **Biosample Name** | ... | **Analysis Workflow**                      | **Analysis Group** | **Sample Label** | **Delivery Mode** |
|                    |     |                                            |                    |                  |                   |
|--------------------|-----|--------------------------------------------|--------------------|------------------|-------------------|
| Biosample1         |     | IsaacV4.0WF-ANY                            |                    |                  | Do Not Deliver    |
| Biosample2         |     | IsaacV4.0WF-ANY \| (TumorNormalV1.1WF-ANY) | analysis1234       | Normal           |                   |
| Biosample3         |     | IsaacV4.0WF-ANY                            | analysis1234       | Tumor            |                   |
|                    |     | *more biosamples...*                       |                    |                  |                   |

Example analysis workflows (in Hyperion environment):

1.  IsaacV4.0WF-ANY

2.  TumorNormalV1.1WF-ANY

Example delivery modes:

1.  *Blank* (leaving the field blank defaults to a value of None)

2.  Do Not Deliver

3.  Deliver

Equivalent Examples
-------------------

The following two manifest files in combination are equivalent to the one above.
This use case could occur if a 'normal' Biosample arrives in a lab significantly
earlier than a 'tumor' Biosample. The normal could be sequenced and analyzed
with Isaac before the tumor Biosample arrived in the lab. Once the tumor
arrives, both Isaac and tumor/normal subtraction analyses can be scheduled.

Manifest 1 of 2:

| **Biosample Name** | ... | **Analysis Workflow** | **Analysis Group** | **Sample Label** | **Delivery Mode** |
|                    |     |                       |                    |                  |                   |
|--------------------|-----|-----------------------|--------------------|------------------|-------------------|
| Biosample1         |     | IsaacV4.0WF-ANY       |                    |                  | Do Not Deliver    |
| Biosample2         |     | IsaacV4.0WF-ANY       |                    |                  |                   |

Manifest 2 of 2:

| **Biosample Name** | ... | **Analysis Workflow**   | **Analysis Group** | **Sample Label** | **Delivery Mode** |
|                    |     |                         |                    |                  |                   |
|--------------------|-----|-------------------------|--------------------|------------------|-------------------|
| Biosample2         |     | (TumorNormalV1.1WF-ANY) | analysis1234       | Normal           |                   |
| Biosample3         |     | IsaacV4.0WF-ANY         | analysis1234       | Tumor            |                   |

Note that the Isaac Analysis Workflow for Biosample 2 is only entered once (in
the first manifest). The output of this Analysis will be used by the
Tumor/Normal Analysis scheduled in the second manifest.

##Adding Metadata to Biosamples


Custom metadata can be added to Biosamples by entering in new column headers in
the same row as the required column headers. Adding values in these columns to
the Biosamples' rows are optional.

In the example to the right, a user creates a custom column called 'Tissue
Source' and tracks that one particular Biosample came from Lung tissue while
another came from Liver tissue. These custom key-value pairs will be displayed
on the Biosample Details page.

Metadata may not be added or edited on existing Biosamples with the Biosample
manifest file.

Validation
----------

No specific validation is done besides the generic limitations of 100 column
headers, 4-60 character limit on column headers, no special characters in column
headers, and 5000 character limit on values.

Example
-------

| **Tissue Source**    | **Customer Barcode** |
|----------------------|----------------------|
| Lung                 | ID-1498124           |
| Liver                | ID-1498125           |
|                      | ID-1498126           |
| *more biosamples...* |                      |

##Adding to Existing Biosamples


When an existing Biosample Name is entered, all columns besides the Prep Request
columns (in orange) or Analysis columns (in green) will be ignored. If a default
project value is entered, it will be ignored. The default project column header
is still required.

Adding/Updating New Prep Requests
---------------------------------

Users can add a new Prep Request to an existing Biosample by using an already
existing Biosample Name and inputting a new Prep Request name. BaseSpace will
add the new Prep Request for the same Biosample and inform the LIMS that a new
library of made with the specified kit should be prepped.

If an already existing Biosample Name is entered with Prep Request that already
exists, the Required Yield Gbp value will be updated for that Biosample and Prep
Request.

All other columns in the manifest will be ignored. Any values entered for
containers or metadata will not be updated.

Scheduling Additional Analyses
------------------------------

Users can schedule additional analyses workflows for an existing Biosample by
entering in an existing Biosample Name and an Analysis Workflow

Validation
----------

1.  When scheduling an analysis workflow with more than one existing BioSample,
    all existing BioSamples must have been imported from same manifest

2.  The user must be the owner, otherwise a new BioSample of the same name will
    be imported with the user as the owner

| **BioSample Name** | **Default Project** | **Prep Request**                | **Required Yield Gbp** |                  |
|--------------------|---------------------|---------------------------------|------------------------|------------------|
| LP0000001-DNA\_A01 |                     | TruSeq PCR-Free High Throughput | 555                    |                  |
| LP0000001-DNA\_B01 |                     | TruSeq PCR-Free High Throughput | 747                    |                  |
| **BioSample Name** | **Default Project** | **Analysis Workflow**           | **Analysis Group**     | **Sample Label** |
| LP0000001-DNA\_A01 |                     | IsaacV4.0WF-ANY                 |                        |                  |
| LP0000001-DNA\_B01 |                     | IsaacV4.0WF-ANY                 |                        |                  |

##Using Sample Sheets with the Biosample Manifest


Purpose
-------

For non-LIMS users, data will be uploaded to BaseSpace with an accompanying
sample sheet .csv file placed in the instrument's run folder. The sample sheet
will contain the names of the biosamples and libraries put onto flowcell lanes.
BaseSpace will use this information to create datasets for the matching
Biosamples and link newly generated libraries and/or pools.

Column Mapping
--------------

-   **Lane** (optional) in the sample sheet maps to **Lane** in BaseSpace (if
    omitted the row applies to all lanes)

-   **Sample\_ID** (required) in the sample sheet maps to **Biosample Name** in
    BaseSpace

-   **Sample Name** (optionsal) in the sample sheet maps to **Library Name** in
    BaseSpace

-   **Sample\_Plate** (optional) in the sample sheet maps to **Container Name**
    in BaseSpace

-   **Sample\_Well** (optional) in the sample sheet maps to **Container
    Position** in BaseSpace

If both the Biosample name and Library Name match an existing Biosample and
Library (from that Biosample), and the Biosample is owned by the Run Owner, then
data from the Run will be associated with the existing Biosample and Library. If
only the Biosample name matches an existing Biosample, then a new Library will
created under the existing Biosample, and new Run data will be associated with
the existing Biosample and new Library. If the Biosample Name does not match an
existing Biosample that is owned by the Run owner, then a new Biosample and
Library will be created and Run data associated with them.

The SampleSheet does not contain the Prep Kit that was used to generate each
Library. So, if the Biosample listed in the SampleSheet has an active Lab
Workflow, then the Library is assumed to be the Prep Kit type of the Lab
Workflow. Otherwise, the Library's Prep Kit is set to 'Unknown'.

Validation
----------

**You must match Sample\_ID in the sample sheet to the Biosample Name** entered
into the BaseSpace manifest import. This links the scheduled analysis set for
the Biosample to the yield in any data that is uploaded, via the CLI or web
importer tool. The same logic applies for auto-app launch where if the required
yield for the Biosample is met, the scheduled analysis will auto-launch. If the
Sample\_ID does not match exactly, BaseSpace **cannot** associate the uploaded
data to an existing Biosample and will create new Biosamples that do not have
scheduled analyses.

![](media/4d860c180f4576fe322b7525b9ee739b.png)

| Lane | Sample\_ID         | Sample\_Name       | Sample\_Plate | Sample\_Well | Index    | Index2   | Project\_Name | description |
|------|--------------------|--------------------|---------------|--------------|----------|----------|---------------|-------------|
| 1    | LP1234567-DNA\_A01 | LP1234567-NTP\_A01 | LP1234567-DNA | A01          | ATTACTCG | ATTACTCC | Proj1         | 2-40131     |
| 2    | LP1234567-DNA\_B01 | LP1234567-NTP\_B01 | LP1234567-DNA | B01          | ATTACTCG | ATTACTCC | Proj1         | 2-40132     |
| 3    | LP1234567-DNA\_C01 | LP1234567-NTP\_C01 | LP1234567-DNA | C01          | ATTACTCG | ATTACTCC | Proj1         | 2-40133     |
