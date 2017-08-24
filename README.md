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

- x-preview = This boolean indicates that the Operation in question is not yet ready for prime time.  You will have to read the documentation to find out just *how* not ready it is, at least for now.

# What Endpoints are not ready?

- Vendors
-- We experienced breaking changes with how Vendors work under the surface pretty late in our development cycle, and were unable to recover in time to stabilize both it and our other features in time to ship.  Those of you who used Vendors in Destiny 1 remember the great Vendor meltdown of 2016.  The implementation that I built to work around said performance meltdown will no longer work in Destiny 2, which puts me back at the drawing board for finding a way to expose Vendor data in an efficient enough manner to melt neither our servers nor the game's servers.  I regret this deeply - particularly discovering it so late and thus not having time to pivot - but I am using this opportunity to pre-release the proposal for the format in which the Vendor calls will return data for review while I continue to work on making Vendors function again.  It is one of the highest priorities on my plate for post-ship.

- Stats (working, but may have bugs)
-- Stats are pretty much in working order, and as you will see their endpoints have not really changed at all.  These *should* be functioning as desired, but I mark them as Pending because they have not been given as thorough of a review for edge cases as the other Destiny features, because BNet itself isn't currently exposing any stats related features.  This is another high-priority task for future improvements of the site, which will also bring about improvements to the API as a result when our attention can be turned back to it as a team.

# The State of the API

The API itself is currently offline in anticipation of the release of Destiny 2.  We have this site as a special sneak preview of the data that will be provided by the API when it comes online.

# FAQ

- Certain APIs are marked as PENDING in the documentation, what does that mean?
-- This may mean that their tentative contracts are being exposed in the documentation for review, or that they're going to be live but in a "Beta" state.  Look at the description of the specific endpoint for details.

- What features 




