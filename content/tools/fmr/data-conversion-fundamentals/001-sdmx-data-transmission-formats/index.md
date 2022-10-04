+++
title = "Unit 01 SDMX data transmission formats primer"
description = "Unit 01 SDMX data transmission formats primer"
date = "2022-08-17T00:00:00+00:00"
weight = 1
hidden = false
+++


## SDMX data transmission formats

The SDMX standard has 12 different formats for transmitting statistical data:


| Type | Version of the standard | Format | Currency |
|:---|:----|:----|:---|
| EDI | SDMX 1.0 | SDMX-EDI GESMES/TS EDIFACT data message | **current** |
| XML | SDMX 1.0 / 2.0 | SDMX-ML Generic (time-series) data message | obsolete |
| XML | SDMX 1.0 / 2.0 | SDMX-ML Compact (time-series) data message | obsolete |
| XML | SDMX 1.0 / 2.0 | SDMX-ML Utility (time-series) data message | obsolete |
| XML | SDMX 1.0 / 2.0 | SDMX-ML Cross-Sectional data message | obsolete |
| XML | SDMX 2.1 | SDMX-ML Generic data messages for observations, time-series and cross-sectional data | **current** |
| XML | SDMX 2.1 | SDMX-ML Structure-Specific data messages for observations, time-series and cross-sectional data | **current** |
| XML | SDMX 3.0 | SDMX-ML Structure-Specific data message | **current**  |
| JSON | SDMX 2.1 | SDMX-JSON version 1 data message | **current**  |
| JSON | SDMX 3.0 | SDMX-JSON version 2 data message | **current**  |
| CSV  | SDMX 2.1 | SDMX-CSV version 1 data message | **current**  |
| CSV  | SDMX 3.0 | SDMX-CSV version 2 data message | **current**  |

Many dating from SDMX versions 1.0 and 2.0 are effectively obsolete, however EDI remains in use.


## Format use cases
The different formats suit some use cases better than others:

**EDI**:
- terse allowing smaller file sizes
- but the GESMES/TS EDIFACT message does not support newer information model features introduced in SDMX 3.0 like multi-value attributes

**XML**:
- human readable making it a good all purpose format
- but is relatively verbose resulting in large file sizes making compression needed for efficient transmission

**JSON**: 
- easily read and manipulated by JavaScript and similar languages making it a good format for driving data publication websites and software tools

**CSV**:
- relatively easy to create using standard software tools and programming techniques
- also easy to read using Excel, BI tools and similar software
- however the flattening of the data into a two-dimensional table makes datasets more verbose because component values are repeated for each observation 

## In the next units
In the following units we'll take a closer look at each of the formats in turn starting with XML which is the most commonly used.