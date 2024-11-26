# Livestock Agriculture Information Model Use Cases

## Telledato
Needs to know where an animal is a point in time
Needs animal transfer events

## HusdyrRegister
Needs to know where an animal is a point in time
Needs animal transfer events
Move to data level and away from application
livestock data
other types of data and not just cattle
many other use cases need to know where animals are for planning etc.

## Health Disease Tracking
Needs to know where an animal is a point in time
Needs to know which organisation /person is legally responsible
Needs animal transfer events
Current state, planned state would also be desirable.
Ownership is a separate topic
Responsibility is a person.

Unique identifier for en anlegg, anlegg har drift ansvalig (org or person). 
Anlegg connected to Farm / production / Sted.
Move animals between anlegg, how should this look.

Do we have separate event types for movement between anlegg.
What different types of anlegg exist?

Anlegg in english - Location?
Geo Information about anlegg, distance between (500m) can define if they should be considered one or 2 locations.

facility id
sub facility's connected to the parent.
responsible org / person

can facility just have geocoords.

geo coords for areas
register for areas with ids / alignment of these

Should we model facilities and subfacilities as events?

Registration with one facility confirmed and the other not yet. that the movement event can convey the new facility.


## Regulatory demands

## Local Interpretations

## Enable inspections

## Animal Herd Management

## Animal Slaughter

## Animal Reproduction

## Animal Feeding


# Animal Transfer Events

Questions: What are the entities involved?

- organisation (how much detail do we need here?)
- animal
- movement event


