+++
title = "Unit 05 EDI data transmission formats"
description = "Unit 05 EDI data transmission formats"
date = "2022-08-21T00:00:00+00:00"
weight = 5
hidden = false
+++

## Introduction
SDMX-EDI is based on the <a href="https://en.wikipedia.org/wiki/Electronic_data_interchange">EDI (Electronic Data Interchange)</a> method for electronically communicating information between computer systems.

EDI originated in the 1970s and is characterised by a very terse text-based format for encoding the information. This terseness was originally needed due to the low communications bandwidths and processing power available. Over time, other formats such as XML became technically feasible as communications and computing improved, however EDI remains in use for the exchange of statistical data particularly in central banking.

## SDMX-EDI is GESMES/TS
SDMX-EDI is also known as <a href="https://en.wikipedia.org/wiki/GESMES/TS">GESMES/TS</a>, a data model and message format designed specifically for the standardised exchange of statistical data and metadata. GESMES/TS is a derivation of the GESMES EDI message, a <a href="https://en.wikipedia.org/wiki/UN/CEFACT">UN/CEFACT</a> a standard using the <a href="https://en.wikipedia.org/wiki/EDIFACT">EDIFACT</a> syntax.

## SDMX-EDI data transmission use case
SDMX-EDI was intended for batch exchange of large amounts of time series data data between counterparties, its terseness allowing for extremely compact expression of large whole or partial data sets. Non time series data such as cross-sectional can be supported if represented as repackaged time series, but there is no direct support for cross-sectional data in this format.

## Limitations
In addition to only supporting time series, SDMX-EDI is limited to the SDMX version 1.0 information model meaning that more sophisticated features like transmitting reference metadata as part of the data messages as introduced in SDMX 3.0 are not supported.

## SDMX-EDI examples
The following is an example SDMX-EDI data message
```` plaintext
UNA:+.? '
UNB+UNOC:3+Unknown+ANONYMOUS+200330:1255+IREF729132++SDMX-EDI'
UNH+MREF000001+GESMES:2:1:E6'
BGM+74'
NAD+Z02+WB'
NAD+MR+ANONYMOUS'
NAD+MS+Unknown'
DSI+GCI'
STS+3+7'
DTM+242:202003301255:203'
DTM+Z02:2008010120170101:711'
IDE+5+GCI'
GIS+AR3'
GIS+1:::-'
ARR++GHA:GCI:RANK:A:20082017:702:102+114+114+114+103+114+111+119+114+111'
ARR++GHA:GCI:VALUE:A:20082017:702:3.616139933+3.448062477+3.55568976+3.64915433+3.792629136+3.693773108+3.713529283+3.582722052+3.679439434+3.7227024636142'
UNT+15+MREF000001'
UNZ+1+IREF729132'
````
You'll note that the equivalent message in SDMX-ML (XML) 2.1 structure specific is more readable, but also more verbose.
```` xml
<message:StructureSpecificData xmlns:ss="http://www.sdmx.org/resources/sdmxml/schemas/v2_1/data/structurespecific" xmlns:footer="http://www.sdmx.org/resources/sdmxml/schemas/v2_1/message/footer" xmlns:ns1="urn:sdmx:org.sdmx.infomodel.datastructure.Dataflow=WB:GCI(1.0):ObsLevelDim:TIME_PERIOD" xmlns:message="http://www.sdmx.org/resources/sdmxml/schemas/v2_1/message" xmlns:common="http://www.sdmx.org/resources/sdmxml/schemas/v2_1/common" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.sdmx.org/resources/sdmxml/schemas/v2_1/message https://registry.sdmx.org/schemas/v2_1/SDMXMessage.xsd urn:sdmx:org.sdmx.infomodel.datastructure.Dataflow=WB:GCI(1.0):ObsLevelDim:TIME_PERIOD https://demo11.metadatatechnology.com/FusionRegistry/ws/public/sdmxapi/rest/schema/dataflow/WB/GCI/1.0?format=sdmx-2.1">
	<message:Header>
		<message:ID>IREF428900</message:ID>
		<message:Test>false</message:Test>
		<message:Prepared>2022-09-29T09:14:50Z</message:Prepared>
		<message:Sender id="MT"/>
		<message:Receiver id="guest"/>
		<message:Structure structureID="WB_GCI_1_0" namespace="urn:sdmx:org.sdmx.infomodel.datastructure.Dataflow=WB:GCI(1.0):ObsLevelDim:TIME_PERIOD" dimensionAtObservation="TIME_PERIOD">
			<common:StructureUsage>
				<Ref agencyID="WB" id="GCI" version="1.0"/>
			</common:StructureUsage>
		</message:Structure>
		<message:DataSetAction>Information</message:DataSetAction>
		<message:Extracted>2022-09-29T09:14:50</message:Extracted>
		<message:ReportingBegin>2008-01-01T00:00:00</message:ReportingBegin>
		<message:ReportingEnd>2017-01-01T23:59:59</message:ReportingEnd>
	</message:Header>
	<message:DataSet ss:dataScope="DataStructure" xsi:type="ns1:DataSetType" ss:structureRef="WB_GCI_1_0">
		<Series REF_AREA="GHA" INDICATOR="GCI" SUB_INDICATOR="RANK" FREQ="A">
			<Obs TIME_PERIOD="2008" OBS_VALUE="102"/>
			<Obs TIME_PERIOD="2009" OBS_VALUE="114"/>
			<Obs TIME_PERIOD="2010" OBS_VALUE="114"/>
			<Obs TIME_PERIOD="2011" OBS_VALUE="114"/>
			<Obs TIME_PERIOD="2012" OBS_VALUE="103"/>
			<Obs TIME_PERIOD="2013" OBS_VALUE="114"/>
			<Obs TIME_PERIOD="2014" OBS_VALUE="111"/>
			<Obs TIME_PERIOD="2015" OBS_VALUE="119"/>
			<Obs TIME_PERIOD="2016" OBS_VALUE="114"/>
			<Obs TIME_PERIOD="2017" OBS_VALUE="111"/>
		</Series>
		<Series REF_AREA="GHA" INDICATOR="GCI" SUB_INDICATOR="VALUE" FREQ="A">
			<Obs TIME_PERIOD="2008" OBS_VALUE="3.616139933"/>
			<Obs TIME_PERIOD="2009" OBS_VALUE="3.448062477"/>
			<Obs TIME_PERIOD="2010" OBS_VALUE="3.55568976"/>
			<Obs TIME_PERIOD="2011" OBS_VALUE="3.64915433"/>
			<Obs TIME_PERIOD="2012" OBS_VALUE="3.792629136"/>
			<Obs TIME_PERIOD="2013" OBS_VALUE="3.693773108"/>
			<Obs TIME_PERIOD="2014" OBS_VALUE="3.713529283"/>
			<Obs TIME_PERIOD="2015" OBS_VALUE="3.582722052"/>
			<Obs TIME_PERIOD="2016" OBS_VALUE="3.679439434"/>
			<Obs TIME_PERIOD="2017" OBS_VALUE="3.72270246361418"/>
		</Series>
	</message:DataSet>
</message:StructureSpecificData>
````

## Tips and points to note
{{% panel %}}
SDMX-EDI is still used for some data exchanges so the ability to convert data messages to and from the format remains useful.

Information such as embedded reference meteadata will be lost when converting from later SDMX-ML, SDMX-JSON and SDMX-CSV formats to SDMX-EDI.

{{% /panel %}}

## Recap
- EDI has been in use since the 1970s and provides a very terse format for data transmission.
- The SDMX-EDI format uses the GESMES/TS message based on the EDIFACT syntax.
- SDMX-EDI is limited to the SDMX 1.0 information model allowing it to encode basic datasets, but does not support the more sophisticated features of the later XML, JSON and CSV formats.

## In the next unit
In the next unit we'll learn how to convert SDMX datasets in practice interactively using FMR's web user interface