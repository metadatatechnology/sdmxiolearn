+++
title = "Unit 04 SDMX CSV data transmission formats"
description = "Unit 04 SDMX CSV data transmission formats"
weight = 4
hidden = false
+++


## Introduction
<a href="https://en.wikipedia.org/wiki/Comma-separated_values">CSV</a> was introduced as a transmission format for **data only** as an addition to SDMX 2.1 and was subsequently updated with the release of SDMX 3.0.\
Like JSON, there are two distinct versions of the data message: 
- version 1 supports the SDMX 2.1 information model
- version 2 supports the SDMX 3.0 information model

In this unit we'll look at the general principles of the SDMX CSV data messages and note the differences between the two versions.

## SDMX-CSV v1 data transmission message
The SDMX-CSV v1 data message specification was added to SDMX 2.1 to provide a more convenient way to work with SDMX datasets using standard software tools like Excel, 'R', Tableau, Power BI and other business intelligence and statistics packages.

The CSV follows a standard 2-dimensional table layout with fixed columns and one row per observation. 

There must be one column for the dataflow, one column per dimension, one column for the primary measure and one column per attribute. All dimensions defined in the Dataflow's Data Structure Definition (DSD) must be included.

A header row defines the meaning of each column.

In the simple case the value of each component is just the **Id**:

```` plaintext
DATAFLOW,    REF_AREA, INDICATOR, SUB_INDICATOR, FREQ, TIME_PERIOD, OBS_VALUE
WB:GCI(1.0), GHA,      GCI,       RANK,          A,    2008,        102
WB:GCI(1.0), GHA,      GCI,       RANK,          A,    2009,        114
WB:GCI(1.0), GHA,      GCI,       RANK,          A,    2010,        114
WB:GCI(1.0), GHA,      GCI,       RANK,          A,    2011,        114
WB:GCI(1.0), GHA,      GCI,       RANK,          A,    2012,        103
WB:GCI(1.0), GHA,      GCI,       RANK,          A,    2013,        114
WB:GCI(1.0), GHA,      GCI,       RANK,          A,    2014,        111
````

Component **Names** (sometimes called Labels) can also be included by encoding each value as ````Id : Name```` as follows:

```` plaintext
DATAFLOW,                                  REF_AREA:Reference Area, INDICATOR:Indicator,               SUB_INDICATOR:Sub Indicator, FREQ:Frequency, TIME_PERIOD:Time period, OBS_VALUE:Observation
WB:GCI(1.0): Global Competitiveness Index, GHA: Ghana,              GCI: Global Competitiveness Index, RANK: Rank,                  A: Annual,      2008,                    102
WB:GCI(1.0): Global Competitiveness Index, GHA: Ghana,              GCI: Global Competitiveness Index, RANK: Rank,                  A: Annual,      2009,                    114
WB:GCI(1.0): Global Competitiveness Index, GHA: Ghana,              GCI: Global Competitiveness Index, RANK: Rank,                  A: Annual,      2010,                    114
WB:GCI(1.0): Global Competitiveness Index, GHA: Ghana,              GCI: Global Competitiveness Index, RANK: Rank,                  A: Annual,      2011,                    114
WB:GCI(1.0): Global Competitiveness Index, GHA: Ghana,              GCI: Global Competitiveness Index, RANK: Rank,                  A: Annual,      2012,                    103
WB:GCI(1.0): Global Competitiveness Index, GHA: Ghana,              GCI: Global Competitiveness Index, RANK: Rank,                  A: Annual,      2013,                    114
WB:GCI(1.0): Global Competitiveness Index, GHA: Ghana,              GCI: Global Competitiveness Index, RANK: Rank,                  A: Annual,      2014,                    111
````

## SDMX-CSV v2 data transmission message
The SDMX-CSV v2 data message follows the same general principle of one observation per row.

V2 was introduced with SDMX 3.0 and includes support for the additional features added to that version of the standard, in particular:
- multiple measures
- complex attributes and measures : multi-lingual values and arrays of values
- transmission of reference metadata linked to the data as part of the data message

Datasets are also no longer restricted to just Dataflows and can instead reference a Dataflow, Data Structure Definition or a Provision Agreement. SDMX-CSV v2 supports this by changing the first two columns to describe the structure type (**STRUCTURE** : dataflow, datastructure or dataprovision) and its Id (**STRUCTURE_ID**)

In addition, the third column now specifies the action type (**ACTION**) bringing CSV into line with the XML and JSON formats that already provide for this, and better supporting the data exchange use case. The SDMX technical specifications define four action types which are encoded in a v2 CSV message using single characters:
- ````I```` - Information - the data is intended for informational purposes only, but treated as Append by the receiver
- ````A```` - Append - instructs incremental update of existing observations by the received
- ````R```` - Replace - instructs the receiver that existing observations should be replaced or appended if they don't already exist
- ````D```` - Delete - instructs the receiver to delete the referenced data 

There can be a mix of action types within a single data message.

The following simple example message has three observations for the dataflow ````ESTAT:CENS_91SMSTA(1.0)```` with an action type of ````I```` indicating that the data is for information purposes only. Note that ````OBS_STATUS```` is an optional observation level attribute.
```` plaintext
STRUCTURE,STRUCTURE_ID,ACTION,FREQ,MARSTA,AGE,SEX,UNIT,GEO,TIME_PERIOD,OBS_VALUE,TIME_FORMAT,OBS_STATUS
dataflow,ESTAT:CENS_91SMSTA(1.0),I,A,TOTAL,Y25-29,F,PER,FR,1991,2162398,P1Y,
dataflow,ESTAT:CENS_91SMSTA(1.0),I,A,TOTAL,Y25-29,M,PER,FR,1991,2147582,P1Y,
dataflow,ESTAT:CENS_91SMSTA(1.0),I,A,TOTAL,Y25-29,T,PER,FR,1991,4309980,P1Y,
````

## Tips and points to note
{{% panel %}}
Values that contain commas must be enclosed in double-quotes

Some implementations support delimiters other than comma, semi-colon (````;````) for instance.

{{% /panel %}}

## Recap
- The SDMX standard has two versions of the CSV data transmission message, both of which are in use
- All SDMX-CSV messages have one observation per row
- v1 was introduced as an addition to SDMX 2.1
- v2 was introduced with SDMX 3.0, follows the same principles and structure as the v1 message but with extensions to support the additional SDMX 3.0 information model features including multiple measures, complex attributes and reference metadata in transit with the data
- The v2 message also adds support for action type providing better support for the data exchange use case - v1 by contrast was best suited to data query response
- Replication of component Ids and possibly names (labels) for each observation make CSV inefficient for large datasets

## In the next unit
In the next unit we'll look at how to interactively convert SDMX datasets between the various data transmission formats using the FMR web user interface