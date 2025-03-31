# Land Usage Information Model

## Requirements

Related to animals and crops parcels of land are used for different purposes. The purpose of the land usage is important for planning and monitoring purposes. The land usage information model should be able to capture the following information:

- legal boundaries of land parcels
- land parcel ownership
- land parcel usage
- land parcel usage history
- land parcel usage changes
- land parcel usage planning
- land parcel usage monitoring
- land parcel type
- creation and evolution of land parcel usage

## General Concepts and Approach

Land usage modelling will make heavy use of geo-spatial data. The land parcel will be the core entity in the model. This entity will have a number of attributes, including: 

- unique identifier (s) URIs
- geo-spatial data (e.g. polygon)
- names (e.g. legal name, common name)
- creating organisation (BR org - e.g. NIBIO, of farmer)
- is owned by (BR org)
- is managed by (BR org)

It is expected that parcels of land can be contained within other parcels of land. The logic for enforcement will be different in different application contexts. 

To support history and tracablity of evolving land usage the model will support the following events:

- Points
- LandParcelCreationEvent
- LandParcelRetirementEvent
- LandParcelOwnershipChangeEvent
- LandParcelNameChangeEvent

Parcels of land are considered to be immutable. Changes to the land parcel will be modelled as new land parcels. identifiers do not change.

There are then a series of events that can be used to model the usage of the land parcel:

These events MUST reference the land parcel that they are related to.

e.g. planted crops, harvested crops, animals on the land, applied fertiliser, applied pesticides, etc.

For now we only describe the abstract event from which all these events MUST be derived:

- LandUsageEvent : location:Event
    - land parcel

## Expected Usage

A national registry such as Kartverket or NIBIO in Norway will be the source of truth for land parcel data at the legal level. 

A farmer can register land parcels that reflect the actual usage of the land, specifically, there could be several land parcels that are used for different purposes, that geopsatially are contained by 1 land parcel defined by Kartverket.

These land parcels can also be retired or split into new land parcels.

These two sets of data are only connected by performing geospatioal analysis. e.g. there is no explicit partOf relationship. 

As we have all events, we can also perform analysis on the land usage over time.

We can ask questions like:

For this land parcel (and those contained), what is the land usage over time?

For this land parcel (and those contained), how has the ownership changed over time?









