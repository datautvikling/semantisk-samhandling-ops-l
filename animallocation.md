# Workpackage on Animal Ownership, Location and Movement

## Background
One of the core areas of the workpackage is to model the ownership, location and movement of animals. This is a key area for the animal health and welfare, and for the traceability of animals. The workpackage will focus on the following areas:

- Ownership of animals
- Location of animals
- Movement of animals
- Responsible organisations for animals

## Core Use Cases

We are interested in enabling traceability of animals in terms of ownership, location and responsible organisations. Specifically, we are interested in the following use cases:

1. Register a new calf as part of a herd
2. Transfer an animal from one herd to another
3. Register a new herd
4. Register the movement of animals between herds
5. Register the movement of animals between locations
6. Assigning unique identifiers to animals
7. Knowing the responsible organisation for a herd
8. Knowing the owner of a herd
9. Transport to slaughterhouse


x. transport of animals between locations

## Data Model

The data model will be based on the following core entities:

- Animal
    - Cattle
    - Sheep
    - Pig
    
- Herd (Animal Group)
    - CattleGroup
    - SheepGroup
    - PigGroup

- Location (geospatial)
    - Processing Facility
        - Slaughterhouse
    - Barn
    - Pasture
    - Farm

- OrganisationalUnit
   - Person
   - single person company
   - limited liability company
 
 and the folling core events:

- ParturitionEvent
   - number of calves
   - number of dead
   - birth ease

- BirthEvent
   - MotherId
   - FatherId from IME event
   - Sex of calf
   - Date of birth
   - breed composition

- AnimalTaggingEvent
    - AnimalId
    - TagId
    - Reason (replacement, new tag)

- TransferOfOwnershipEvent
    - AnimalId
    - ToOrganisationId
    - FromOrganisationId (optional)

- AnimalExportEvent

- AnimalImportEvent

- OutOfHerdEvent
    - Sale
    - Death
    - Slaughter

- AnimalIntoLocationEvent
- AnimalOutOfLocationEvent

- HerdOwnershipChangeEvent
- HerdRegistrationEvent
- HerdRemovalEvent
- HerdResponsibleChangeEvent
- OrganisationRegistration
- LicenseGrantedEvent
- LicenseRevokedEvent
- LicenseProhibitedSentenceEvent

They are supported with the following controlled vocabularies:

- IntoHerdReason (e.g. birth, purchase)
- OutOfHerdReason (e.g. sale, death)
- IntoLocationReason (e.g. movement, birth, purchase)
- OutOfLocationReason (e.g. movement, death, sale)

Without going to much into API design, the following API endpoints are expected:

POST /events
GET /events?since={event-seq-no} || datetime (of registatrion not event occurrence)

GET /organisations
GET /organisations/{id}
GET /organisations/{id}/herds
GET /organisations/{id}/locations
GET /organisations/{id}/herds/{id}
GET /organisations/{id}/locations/{id}
GET /organisations/{id}/herds/{id}/animals
GET /organisations/{id}/locations/{id}/animals

## Expected Usage

For Animal welfare there are 2 key drives for the data model. Where are animals located over time, and which organisation is responsible for the animals. This is important for the traceability of animals, and for the management of animal health and welfare. 

An organisation that is responsible for a herd may be different from the one that owns in. 

When a organisation is granted a farming license the following events must be registered:

- HerdRegistrationEvent 
    - with the owning organisation

We are assuming that master data such as the list of people, or organisations, and the list of locations are managed in a separate system but available, and the means of identiy is clear. e.g. PersonId, OrganisationId.

When a new animal is born the following events must be registered:

- IntoHerdEvent
    - with the herd id
    - with the animal id
    - with the reason birth
    - origin marking

- IntoLocationEvent
    - with the location

When an animal is sold the following events must be registered:

When an animal is moved between herds the following events must be registered:


## Identity of things

All items inherit from a common base class with a required globally unique identifer and a collection of externalIdentifiers. The externalIdentifiers are used to map the main identifier to those used in other systems.

Identity for non master data items, e.g. animals, can be minted locally using UUIDs. But to align with semantic technologies these will be urn schemes:

- urn:animal:uuid:xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx

This also aligns with ICAR direction on identifers.