+++
title = "Unit 03 SDMX JSON data transmission formats"
description = "Unit 03 SDMX JSON data transmission formats"
date = "2022-08-17T00:00:00+00:00"
tags = ["JSON"]
weight = 3
hidden = "true"
+++


## Introduction
<a href="https://en.wikipedia.org/wiki/JSON">JSON</a> was introduced as a transmission format for both structures and data as an addition to SDMX 2.1. Unlike XML there are only two versions of the data message. 

In this unit we'll look at the general principles of the JSON data message and note the differences between the two versions.

## SDMX-JSON v1 data transmission message
The SDMX-JSON v1 data message specification was added to SDMX 2.1 principally to satisfy the use case for data dissemination on the Internet where JSON is easier to use for websites and web data publication applications.

SDMX-JSON differs from its XML counterparts in that it transmits both the classification identifiers and their labels. This has the advantage of packaging all the information required to display a dataset in a single message. The XML messages by contrast require applications also have access to the dataset's structural metadata in order to decode enumerated values in particular.

The basic structure of a message is as follows:
```` text
{
    "meta" : { header information },
    "data" : {
        "datasets" : [ {array of one or more datasets} ],
        "structures" : { the structural metadata for the datasets}
    }
}
````

The ````datasets```` element carries an array of one or more datasets with their accompanying series and observation values. However, the metadata in terms of the component Ids, Names, Descriptions, and the observation time period values are under the ````structures```` element and referenced using a zero-based index string of the form ````0:0:1:0````.

The exerpt of a single series below shows this in context. The ````0:0:1:0```` indicates there are four dimensions respectively referencing the first, first, second and first codes in their codelists defined in the ````structures```` section.
````text
"series": {
    "0:0:1:0": {
        "attributes": [],
        "observations": {
            "0": ["102"],
            "1": ["114"],
            "2": ["114"],
            "3": ["114"],
            "4": ["103"],
            "5": ["114"],
            "6": ["111"],
            "7": ["119"],
            "8": ["114"],
            "9": ["111"]
        }
    },
````
This approach of decoupling the metadata from the data is designed to minimise the size of the message by avoiding duplication.

{{%expand "See the complete message..." %}}

```` json
{
    "meta": {
        "id": "IREF519002",
        "prepared": "2022-08-17T15:58:26",
        "test": false,
        "datasetId": "5116be7f-5f35-49f1-9379-54449224bc57",
        "sender": {
            "id": "Unknown"
        },
        "receiver": {
            "id": "guest"
        },
        "links": [{
            "rel": "self",
            "href": "/data/WB,GCI,1.0/GHA.GCI..?format=sdmx-json",
            "uri": "https://raw.githubusercontent.com/sdmx-twg/sdmx-json/develop/structure-message/tools/schemas/1.0/sdmx-json-structure-schema.json"
        }]
    },
    "data": {
        "dataSets": [{
            "links": [{
                "rel": "dataflow",
                "urn": "urn:sdmx:org.sdmx.infomodel.datastructure.Dataflow=WB:GCI(1.0)"
            }],
            "action": "Information",
            "series": {
                "0:0:0:0": {
                    "attributes": [],
                    "observations": {
                        "0": ["102"],
                        "1": ["114"],
                        "2": ["114"],
                        "3": ["114"],
                        "4": ["103"],
                        "5": ["114"],
                        "6": ["111"],
                        "7": ["119"],
                        "8": ["114"],
                        "9": ["111"]
                    }
                },
                "0:0:1:0": {
                    "attributes": [],
                    "observations": {
                        "0": ["3.616139933"],
                        "1": ["3.448062477"],
                        "2": ["3.55568976"],
                        "3": ["3.64915433"],
                        "4": ["3.792629136"],
                        "5": ["3.693773108"],
                        "6": ["3.713529283"],
                        "7": ["3.582722052"],
                        "8": ["3.679439434"],
                        "9": ["3.72270246361418"]
                    }
                }
            }
        }],
        "structure": {
            "links": [{
                "rel": "dataflow",
                "urn": "urn:sdmx:org.sdmx.infomodel.datastructure.Dataflow=WB:GCI(1.0)"
            }, {
                "rel": "datastructure",
                "urn": "urn:sdmx:org.sdmx.infomodel.datastructure.DataStructure=WB:GCI(1.0)"
            }],
            "name": "Global Competitiveness Index",
            "names": {
                "en": "Global Competitiveness Index"
            },
            "description": "Global Competitiveness Index",
            "descriptions": {
                "en": "Global Competitiveness Index"
            },
            "dimensions": {
                "dataset": [],
                "series": [{
                    "id": "REF_AREA",
                    "name": "Reference Area",
                    "keyPosition": 0,
                    "role": null,
                    "values": [{
                        "id": "GHA",
                        "name": "Ghana"
                    }]
                }, {
                    "id": "INDICATOR",
                    "name": "Indicator",
                    "keyPosition": 1,
                    "role": null,
                    "values": [{
                        "id": "GCI",
                        "name": "Global Competitiveness Index"
                    }]
                }, {
                    "id": "SUB_INDICATOR",
                    "name": "Sub Indicator",
                    "keyPosition": 2,
                    "role": null,
                    "values": [{
                        "id": "RANK",
                        "name": "Rank"
                    }, {
                        "id": "VALUE",
                        "name": "Value"
                    }]
                }, {
                    "id": "FREQ",
                    "name": "Frequency",
                    "keyPosition": 3,
                    "role": null,
                    "values": [{
                        "id": "A",
                        "name": "Annual",
                        "description": "To be used for data collected or disseminated every year."
                    }]
                }],
                "observation": [{
                    "id": "TIME_PERIOD",
                    "name": "Time period",
                    "description": "The period of time or point in time to which the measured observation refers.",
                    "keyPosition": 4,
                    "role": "time",
                    "values": [{
                        "start": "2008-01-01T00:00:00",
                        "end": "2008-12-31T23:59:59",
                        "id": "2008",
                        "name": "2008"
                    }, {
                        "start": "2009-01-01T00:00:00",
                        "end": "2009-12-31T23:59:59",
                        "id": "2009",
                        "name": "2009"
                    }, {
                        "start": "2010-01-01T00:00:00",
                        "end": "2010-12-31T23:59:59",
                        "id": "2010",
                        "name": "2010"
                    }, {
                        "start": "2011-01-01T00:00:00",
                        "end": "2011-12-31T23:59:59",
                        "id": "2011",
                        "name": "2011"
                    }, {
                        "start": "2012-01-01T00:00:00",
                        "end": "2012-12-31T23:59:59",
                        "id": "2012",
                        "name": "2012"
                    }, {
                        "start": "2013-01-01T00:00:00",
                        "end": "2013-12-31T23:59:59",
                        "id": "2013",
                        "name": "2013"
                    }, {
                        "start": "2014-01-01T00:00:00",
                        "end": "2014-12-31T23:59:59",
                        "id": "2014",
                        "name": "2014"
                    }, {
                        "start": "2015-01-01T00:00:00",
                        "end": "2015-12-31T23:59:59",
                        "id": "2015",
                        "name": "2015"
                    }, {
                        "start": "2016-01-01T00:00:00",
                        "end": "2016-12-31T23:59:59",
                        "id": "2016",
                        "name": "2016"
                    }, {
                        "start": "2017-01-01T00:00:00",
                        "end": "2017-12-31T23:59:59",
                        "id": "2017",
                        "name": "2017"
                    }]
                }]
            },
            "attributes": {
                "dataset": [],
                "series": [],
                "observation": []
            }
        }
    }
}
````

{{% /expand%}}

## SDMX-JSON v2 data transmission message
The SDMX-JSON v2 data message was introduced with SDMX 3.0 and follows the same principles and structure but with additions to support the new information model features, principally:
- support for multiple measures
- support for **complex attributes and measures** : multi-lingual values and arrays of values 
- support for the transmission of **reference metadata** that is linked to data as part of the data message

## Tips and points to note
{{% panel %}}
SDMX-JSON can be used for any data transmission use case, but is best suited for web data discovery and retrieval applications because it carries all of the data and metadata needed to build an effective user interface.

The SDMX-JSON message is equivalent to SDMX-ML Generic in that its JSON schema is fixed and not dependent on the datasets' DSDs.

{{% /panel %}}

## Recap
- The SDMX standard has two versions of the JSON data transmission message, both of which are in use
- v1 was introduced as an addition to SDMX 2.1
- v2 was introduced with SDMX 3.0, follows the same principles and structure as the v1 message but with extensions to support the additional SDMX 3.0 information model features including multiple measures, complex attributes and reference metadata in transit with the data

## In the next unit
In the next unit we'll look at the options for using CSV for SDMX data transmission.