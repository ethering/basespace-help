Automatic Lane QC
=================

With automatic lane QC, users will be able to modify settings that enables
Sequence Hub to automatically apply a QC status to the lanes of sequencing runs
as they complete. Settings can be modified to configure specific thresholds and
logic on metrics they want evaluated. Sequence Hub compares the Lane's metrics
given by the sequencer to the user's predefined thresholds and moves the Lane's
status from '--' to either 'QC Passed' or 'QC Failed'.

Lane QC thresholds are configured per user (or per workgroup) and apply to all
lanes generated for sequencing runs that user owns. By default, all lanes will
be set to QC passed until a user configures their QC settings.

When a lane is set to QC failed, its data will be excluded from downstream data
Analyses.

![](/images/articles/auto-lane-qc-1_1382x476.png)

Setting QC Status Manually
==========================

Users may override the QC status set by the system. By clicking the checkboxes
to multi-select lanes, and clicking the Change Status action, a modal opens with
the selected lanes and what status the user wishes to change to.

Currently, lanes can be set to either 'QC Passed' or 'QC Failed'.

Users must multi-select lanes with the same current QC status to make a bulk
change.

It is also possible to change Lane QC status with a REST API (see API access
below).

![](/images/articles/auto-lane-qc-2_1419x652.png)

Available Metrics
=================

Expand the following box to view all available sequencing lane metrics that can
have thresholds for automatic QC. These metrics are also viewable in the
response of the Runs API in more detail below.

Lanes: 

-   LaneNumber: 
-   Density: 773669,
-   PercentPf: 96.0605,
-   Phasing: 0.109476,
-   PrePhasing: 0.184839,
-   Reads: 19788945,
-   ReadsPf: 19008093,
-   PercentGtQ30: 93.6088,
-   Yield: 1.86279,
-   MaxCycleCalled: 5,
-   PercentAligned: 0.00154398,
-   ErrorRate: 0,
-   ErrorRate35: 0,
-   ErrorRate50: 0,
-   ErrorRate75: 0,
-   ErrorRate100: 0,
-   IntensityCycle1: 965.333,
-   Status: "Initial",
-   ProjectedYieldInGbp: 0,
-   MaxProjectedYieldInGbp: 0

LanesByRead:

-   ReadNumber: 1,
-   LaneNumber: 1,
-   TileCount: 12,
-   Density: 773669,
-   DensityDeviation: 18000.2,
-   PercentPf: 96.0605,
-   PercentPfDeviation: 0.348258,
-   Phasing: 0.163381,
-   PrePhasing: 0.279107,
-   Reads: 6596315,
-   ReadsPf: 6336031,
-   PercentGtQ30: 93.3761,
-   Yield: 0.950405,
-   MinCycleCalled: 0,
-   MaxCycleCalled: 150,
-   MinCycleError: 0,
-   MaxCycleError: 0,
-   PercentAligned: 0.0023315,
-   PercentAlignedDeviation: 0.000887718,
-   ErrorRate: 0,
-   ErrorRateDeviation: 0,
-   ErrorRate35: 0,
-   ErrorRate35Deviation: 0,
-   ErrorRate50: 0,
-   ErrorRate50Deviation: 0,
-   ErrorRate75: 0,
-   ErrorRate75Deviation: 0,
-   ErrorRate100: 0,
-   ErrorRate100Deviation: 0,
-   IntensityCycle1: 960.167,
-   IntensityCycle1Deviation: 212.392

(Metric values for other Lanes not shown here)