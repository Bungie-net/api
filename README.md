# The Bungie.Net API

Full Documentation: https://bungie-net.github.io/multi/index.html

Documentation as one single, gigantic page: https://bungie-net.github.io

This section will be added to as time goes by - we're working with it as we go!

# Swagger/OpenAPI Specs

- Grab openapi.json for the OpenAPI 3.0.0 specs
- Grab openapi-2.json for the 2.0.0 specs

# Extension Properties on OpenAPI Specs

- x-mapped-definition = This property has hash identifiers that map to a Manifest Database definition.  This property will reveal which type of Manifest Database definition it points to.  If it's a uint32, it points to a single definition.  If it's a List<uint32>, each value points to a different definition.  If it's a Dictionary<uint32, X>, its' keys point to different definitions.

- x-mobile-manifest-name = If populated, this is the name of the Mobile Manifest table that holds this data as a first-class entity.  The existence of this field implies that this entity is a first-order Destiny Definition aggregate.

- x-enum-values = I really hate that the OpenAPI spec doesn't have a way to tell you both the identifier and the numeric value of an enum, much less documentation for enum values, so I added this extension as a way to return that info.  It'll give you way more than the basically useless base "enum" property.

- x-destiny-component-type-dependency = A new concept in the Destiny 2 API is "Components".  You will see that our Destiny Profile/Character calls have been mostly simplified down to just GetProfile/GetCharacter/GetItem.  This simplification is made possible by Components, which are identifiers you pass into the requests to specify how much data you want back.  An entity with this property will only be returned if you've passed the named Component Identifier into the GetProfile/GetCharacter/GetItem methods.

- x-dictionary-key = OpenAPI didn't have a good way for me to specify that the key of a dictionary was actually meant to be something other than a string (even if always encoded as a string in JSON).  This extension property lets me tell you what it *really* is, so you can strongly type it and convert it if desired.

# The State of the API

The API itself is currently offline in anticipation of the release of Destiny 2.  We have this site as a special sneak preview of the data that will be provided by the API when it comes online.

# FAQ

- Certain APIs are marked as PENDING in the documentation, what does that mean?
-- This may mean that their tentative contracts are being exposed in the documentation for review, or that they're going to be live but in a "Beta" state.  Look at the description of the specific endpoint for details.

- What features 




