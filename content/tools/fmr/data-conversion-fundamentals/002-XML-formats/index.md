+++
title = "Unit 02 SDMX XML data transmission formats"
description = "Unit 02 SDMX XML data transmission formats"
date = "2022-08-17T00:00:00+00:00"
weight = 2
hidden = false
+++


## Introduction
The XML data transmission format was introduced with SDMX 1.0 and is known as **SDMX-ML data**.

It provides a good balance between usability, human readability and transmission efficiency - particularly if compressed. These characteristics in addition to its early introduction have made XML the most widely used format.

Since SDMX 1.0, the standard has accumulated seven different variants of the XML data format.\
In this unit we'll look at the three most relevant:
- SDMX-ML 2.1 Generic data message
- SDMX-ML 2.1 Structure-specific data message
- SDMX-ML 3.0 Structure-specific data message


## SDMX-ML 2.1 Generic data message

The **Generic message** is characterised by having a fixed XML schema irrespective of the structure of the dataset.

By contrast, the **structure-specific** XML schema is variable and defined by the dataset's DSD. While a little more verbose, the fixed schema can make it easier to create and process Generic messages because the XML structure is always the same.

{{% notice note %}}
The SDMX-ML 2.1 Generic data message aligns with the SDMX 2.1 information model. 
{{% /notice %}}

Example:\
The example below is an *excerpt* from a Generic data message.

A Generic ````Dataset```` consists of a sequence of ````Series```` elements.\
You'll note that a series starts by defining its ````SeriesKey```` which sets the dimension values followed by a sequence of ````obs```` observation elements containing the time period and its associated observation value.
```` xml
	<message:DataSet structureRef="WB_GCI_1_0">
		<generic:Series>
			<generic:SeriesKey>
				<generic:Value id="REF_AREA" value="GHA"/>
				<generic:Value id="INDICATOR" value="GCI"/>
				<generic:Value id="SUB_INDICATOR" value="RANK"/>
				<generic:Value id="FREQ" value="A"/>
			</generic:SeriesKey>
			<generic:Obs>
				<generic:ObsDimension value="2008"/>
				<generic:ObsValue value="102"/>
			</generic:Obs>
			<generic:Obs>
				<generic:ObsDimension value="2009"/>
				<generic:ObsValue value="114"/>
			</generic:Obs>
			<generic:Obs>
				<generic:ObsDimension value="2010"/>
				<generic:ObsValue value="114"/>
			</generic:Obs>
````

{{%expand "See the complete message..." "badge" %}}

```` xml
<message:GenericData xmlns:footer="http://www.sdmx.org/resources/sdmxml/schemas/v2_1/message/footer" xmlns:generic="http://www.sdmx.org/resources/sdmxml/schemas/v2_1/data/generic" xmlns:common="http://www.sdmx.org/resources/sdmxml/schemas/v2_1/common" xmlns:message="http://www.sdmx.org/resources/sdmxml/schemas/v2_1/message" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.sdmx.org/resources/sdmxml/schemas/v2_1/message https://registry.sdmx.org/schemas/v2_1/SDMXMessage.xsd">
	<message:Header>
		<message:ID>IREF353870</message:ID>
		<message:Test>false</message:Test>
		<message:Prepared>2022-08-17T11:23:05Z</message:Prepared>
		<message:Sender id="Unknown"/>
		<message:Receiver id="guest"/>
		<message:Structure structureID="WB_GCI_1_0" dimensionAtObservation="TIME_PERIOD">
			<common:StructureUsage>
				<Ref agencyID="WB" id="GCI" version="1.0"/>
			</common:StructureUsage>
		</message:Structure>
		<message:DataSetAction>Information</message:DataSetAction>
		<message:Extracted>2022-08-17T11:23:05</message:Extracted>
		<message:ReportingBegin>2008-01-01T00:00:00</message:ReportingBegin>
		<message:ReportingEnd>2017-01-01T23:59:59</message:ReportingEnd>
	</message:Header>
	<message:DataSet structureRef="WB_GCI_1_0">
		<generic:Series>
			<generic:SeriesKey>
				<generic:Value id="REF_AREA" value="GHA"/>
				<generic:Value id="INDICATOR" value="GCI"/>
				<generic:Value id="SUB_INDICATOR" value="RANK"/>
				<generic:Value id="FREQ" value="A"/>
			</generic:SeriesKey>
			<generic:Obs>
				<generic:ObsDimension value="2008"/>
				<generic:ObsValue value="102"/>
			</generic:Obs>
			<generic:Obs>
				<generic:ObsDimension value="2009"/>
				<generic:ObsValue value="114"/>
			</generic:Obs>
			<generic:Obs>
				<generic:ObsDimension value="2010"/>
				<generic:ObsValue value="114"/>
			</generic:Obs>
			<generic:Obs>
				<generic:ObsDimension value="2011"/>
				<generic:ObsValue value="114"/>
			</generic:Obs>
			<generic:Obs>
				<generic:ObsDimension value="2012"/>
				<generic:ObsValue value="103"/>
			</generic:Obs>
			<generic:Obs>
				<generic:ObsDimension value="2013"/>
				<generic:ObsValue value="114"/>
			</generic:Obs>
			<generic:Obs>
				<generic:ObsDimension value="2014"/>
				<generic:ObsValue value="111"/>
			</generic:Obs>
			<generic:Obs>
				<generic:ObsDimension value="2015"/>
				<generic:ObsValue value="119"/>
			</generic:Obs>
			<generic:Obs>
				<generic:ObsDimension value="2016"/>
				<generic:ObsValue value="114"/>
			</generic:Obs>
			<generic:Obs>
				<generic:ObsDimension value="2017"/>
				<generic:ObsValue value="111"/>
			</generic:Obs>
		</generic:Series>
		<generic:Series>
			<generic:SeriesKey>
				<generic:Value id="REF_AREA" value="GHA"/>
				<generic:Value id="INDICATOR" value="GCI"/>
				<generic:Value id="SUB_INDICATOR" value="VALUE"/>
				<generic:Value id="FREQ" value="A"/>
			</generic:SeriesKey>
			<generic:Obs>
				<generic:ObsDimension value="2008"/>
				<generic:ObsValue value="3.616139933"/>
			</generic:Obs>
			<generic:Obs>
				<generic:ObsDimension value="2009"/>
				<generic:ObsValue value="3.448062477"/>
			</generic:Obs>
			<generic:Obs>
				<generic:ObsDimension value="2010"/>
				<generic:ObsValue value="3.55568976"/>
			</generic:Obs>
			<generic:Obs>
				<generic:ObsDimension value="2011"/>
				<generic:ObsValue value="3.64915433"/>
			</generic:Obs>
			<generic:Obs>
				<generic:ObsDimension value="2012"/>
				<generic:ObsValue value="3.792629136"/>
			</generic:Obs>
			<generic:Obs>
				<generic:ObsDimension value="2013"/>
				<generic:ObsValue value="3.693773108"/>
			</generic:Obs>
			<generic:Obs>
				<generic:ObsDimension value="2014"/>
				<generic:ObsValue value="3.713529283"/>
			</generic:Obs>
			<generic:Obs>
				<generic:ObsDimension value="2015"/>
				<generic:ObsValue value="3.582722052"/>
			</generic:Obs>
			<generic:Obs>
				<generic:ObsDimension value="2016"/>
				<generic:ObsValue value="3.679439434"/>
			</generic:Obs>
			<generic:Obs>
				<generic:ObsDimension value="2017"/>
				<generic:ObsValue value="3.72270246361418"/>
			</generic:Obs>
		</generic:Series>
	</message:DataSet>
</message:GenericData>
````

{{% /expand%}}

## SDMX-ML 2.1 Structure-specific data message

Unlike Generic, the **Structure-specific** messages's XML elements and XML attributes are defined by the Data Structure Definitions of the datasets being transmitted. This approach provides two key benefits:
1. The datasets' validity can be checked by validating the XML message against its XML schema using standard XML processing tools
2. The message is less verbose - for this reason **Compact** is used as another name for Structure-specific

Note that 'validity' in this case concerns the following:
- Conformance of the dataset to the defined Data Structure Definition - does it have the right SDMX Dimensions and Attributes
- Mandatory attributes are reported
- The value of each Dimension, Attribute and Measure complies with the component's defined representation - for coded components for example, the values must appear in the relevant Codelists
- Compliance with any defined Constraints

The SDMX-ML 2.1 Structure-specific data message aligns with the SDMX 2.1 information model. 

Example:\
The *excerpt* from a Structure-specific message below illustrates the principles.

The XML attributes of the ````Series```` element are specific to the DSD for this dataset so refer directly to the DSD's Dimensions (REF_AREA, INDICATOR etc) rather than using key-value pairs. Any Series Attributes would also be included as explicit XML attributes of the Series element. Similarly, Observation Attributes would be included as XML attributes of the Obs elements.

```` xml
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
````

{{%expand "See the complete message..." "badge" %}}

```` xml
<message:StructureSpecificData xmlns:ss="http://www.sdmx.org/resources/sdmxml/schemas/v2_1/data/structurespecific" xmlns:footer="http://www.sdmx.org/resources/sdmxml/schemas/v2_1/message/footer" xmlns:ns1="urn:sdmx:org.sdmx.infomodel.datastructure.Dataflow=WB:GCI(1.0):ObsLevelDim:TIME_PERIOD" xmlns:message="http://www.sdmx.org/resources/sdmxml/schemas/v2_1/message" xmlns:common="http://www.sdmx.org/resources/sdmxml/schemas/v2_1/common" xmlns:xsi="http://www.w3.org/2001/XMLSchema-instance" xsi:schemaLocation="http://www.sdmx.org/resources/sdmxml/schemas/v2_1/message https://registry.sdmx.org/schemas/v2_1/SDMXMessage.xsd urn:sdmx:org.sdmx.infomodel.datastructure.Dataflow=WB:GCI(1.0):ObsLevelDim:TIME_PERIOD https://demo11.metadatatechnology.com/FusionRegistry/ws/public/sdmxapi/rest/schema/dataflow/WB/GCI/1.0?format=sdmx-2.1">
	<message:Header>
		<message:ID>IREF378771</message:ID>
		<message:Test>false</message:Test>
		<message:Prepared>2022-08-17T12:04:37Z</message:Prepared>
		<message:Sender id="Unknown"/>
		<message:Receiver id="guest"/>
		<message:Structure structureID="WB_GCI_1_0" namespace="urn:sdmx:org.sdmx.infomodel.datastructure.Dataflow=WB:GCI(1.0):ObsLevelDim:TIME_PERIOD" dimensionAtObservation="TIME_PERIOD">
			<common:StructureUsage>
				<Ref agencyID="WB" id="GCI" version="1.0"/>
			</common:StructureUsage>
		</message:Structure>
		<message:DataSetAction>Information</message:DataSetAction>
		<message:Extracted>2022-08-17T12:04:37</message:Extracted>
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

{{% /expand%}}

## Changes to the data messages in SDMX 3.0
SDMX 3.0 rationalised the list of XML data transmission formats to just one: **SDMX-ML 3.0 Structure-specific**.

{{% notice note %}}
Note that while the legacy SDMX 2.0 and 2.1 data formats including Generic were deprecated in SDMX 3.0 they remain valid for data transmission. However there are no equivalents in the latest version 3.0 of the SDMX standard.
{{% /notice %}}

## SDMX-ML 3.0 Structure-specific data message
The SDMX-ML 3.0 Structure-specific data message follows the same principles and structure to the original SDMX 2.1 as set out above.

The key differences in the SDMX 3.0 variant are:
- support for multiple measures
- support for **complex attributes and measures** : multi-lingual values and arrays of values 
- support for the transmission of **reference metadata** that is linked to data as part of the data message

The excerpt below from an SDMX 3.0 Structure-specific message illustrates the ````<Comp>```` element which is used to structure complex objects within the message body:

```` xml
	<message:DataSet xsi:type="ns1:DataSetType" ss:structureRef="ECB_EXR_COMPLEX_ATTRIBUTES_1_0">
		<Series FREQ="A" CURRENCY="CAD" CURRENCY_DENOM="EUR" EXR_TYPE="SP00" EXR_SUFFIX="A" TIME_FORMAT="P1Y" COLLECTION="A" DECIMALS="4" TITLE_COMPL="ECB reference exchange rate, Canadian dollar/Euro, 2:15 pm (C.E.T.)" UNIT="CAD" UNIT_MULT="0">
			<Comp id="TITLE" xsi:type="ns1:TITLE_ATTRIBUTE">
				<Value>
					<common:Text xml:lang="en">Some English Text</common:Text>
					<common:Text xml:lang="fr">Quelques textes en anglais</common:Text>
				</Value>
				<Value>
					<common:Text>Additional English Text where lang defaults to en</common:Text>
					<common:Text xml:lang="fr">Texte anglais supplémentaire</common:Text>
				</Value>
			</Comp>
			<Comp id="SOURCE_AGENCY" xsi:type="ns1:SOURCE_AGENCY_ATTRIBUTE">
				<Value>4F0</Value>
				<Value>4D0</Value>
				<Value>CZ2</Value>
			</Comp>
			<Comp id="SOURCE_PUB" xsi:type="ns1:SOURCE_PUB_ATTRIBUTE">
				<Value>First publication source</Value>
				<Value>Second publication source</Value>
			</Comp>
			
			<Obs TIME_PERIOD="2017" OBS_VALUE="1.46472274509804">
				<Comp id="OBS_STATUS" xsi:type="ns1:OBS_STATUS_ATTRIBUTE">
					<Value>A</Value>
					<Value>F</Value>
				</Comp>
			</Obs>
			
			<Obs TIME_PERIOD="2018" OBS_VALUE="1.529364705882353">
				<Comp id="OBS_STATUS" xsi:type="ns1:OBS_STATUS_ATTRIBUTE">
					<Value>J</Value>
					<Value>U</Value>
					<Value>N</Value>
				</Comp>			
			</Obs>
````

## Obsolete SDMX 1.0/2.0 XML data messages
SDMX versions 1.0 and 2.0 specified four additional XML data messages all of which are effectively obsolete but may still be used by some systems and organisations:

- SDMX-ML 1.0/2.0 Generic (time-series) data message - general format for exchange of SDMX time-series datasets using a fixed XML schema
- SDMX-ML 1.0/2.0 Compact (time-series) data message - same principle as SDMX-ML 2.1 structure specific in that the message's XML schema is defined by the dataset's DSD making it more 'compact'
- SDMX-ML 1.0/2.0 Utility (time data) data message - a little used alternative to Generic
- SDMX-ML 1.0/2.0 Cross-Sectional data message - a message format designed for exchange of cross-sectional data but little used in practice

## XML 'series keys only' data messages
A data message can optionally carry just the series keys without observation values as illustrated using the Generic message below. 

```` xml
	<generic:Series>
		<generic:SeriesKey>
			<generic:Value id="REF_AREA" value="GHA"/>
			<generic:Value id="INDICATOR" value="GCI"/>
			<generic:Value id="SUB_INDICATOR" value="RANK"/>
			<generic:Value id="FREQ" value="A"/>
		</generic:SeriesKey>
	</generic:Series>
	<generic:Series>
		<generic:SeriesKey>
			<generic:Value id="REF_AREA" value="GHA"/>
			<generic:Value id="INDICATOR" value="GCI"/>
			<generic:Value id="SUB_INDICATOR" value="VALUE"/>
			<generic:Value id="FREQ" value="A"/>
		</generic:SeriesKey>
	</generic:Series>
````

'Series keys only' messages find application in use cases where knowledge of the data available is required but the precise observations are not, for instance in interactive 'data discovery' software tools for data consumers.


## Tips and points to note
{{% panel %}}
The Generic and Structure-specific XML formats are the most useful and those most likely to be encountered in practice.

The SDMX-ML 3.0 Structure-specific data message is the only option for datasets that use information model features introduced in version 3.0 including multi-value and multi-lingual attributes and measures. 

Simlarly the SDMX 3.0 Structure-specific data message must be used for transmission of Reference Metadata with the data when following the SDMX 3.0 model for reference metadata.

{{% /panel %}}

## Recap
- The SDMX standard has seven alternative formats for data transmission using XML 
- The SDMX 2.1 Generic message is commonly used and benefits from a fixed schema that is often simpler to create and interpret
- The SDMX 2.1 Structure specific message is similarly in common usage, it's less verbose and allows validation of the dataset by validating the XML message against its DSD-specific XML schema
- SDMX 3.0 Structure-specific is the only XML data message for SDMX 3.0 use cases - it follows the same principles as the earlier SDMX 2.1 message with additional support for information model features introduced in SDMX 3.0 including multiple measures and multi-value attributes
- 'Series keys only' data messages carry just the series keys and omit the observation values

## In the next unit
In the next unit we'll look at the SDMX-JSON data transmission messages.