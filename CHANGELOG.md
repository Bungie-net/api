# Changelog

## [2.1.4] -2018-03-07
### Added
* Insert Plugs action now ready for Bungie use, alongside the Advanced Write Action authorization flow. These features are not yet available to 3rd parties, but we will keep you posted.
* A new Application History page shows a user the in-game actions performed through both 1st and 3rd party applications, so that users can more reliably monitor what apps are doing with their characters, items etc.
* Team Scores added to Nightfall Strikes view on the web.
* There is a new component for Vendor requests, "VendorGroups".  This grabs dynamic categorizations of groups for vendors, and comes with its own new set of Destiny Definitions in the manifest.  This is a replacement for the confusing and obsolete "VendorCategories" concept from the Destiny 1.0 API, which not only wasn't as dynamic as we want but also was very confusing to talk about (given that vendor sale items are also grouped by "Categories").
* Two new activity modes: ScoredNightfall and ScoredHeroicNightfall.

### Changed
* Vendor location data should now be accurate.
* Nightfall activities should now be categorized correctly.
* The following bugs were fixed:
  * #430 Gunsmith reports the wrong mods for sale
  * #429 Sonic Simulation Emblem is Classified
  * #424 UnhandledException for Vendors on profile with little/no progress
  * #423 All masterwork plugs are returned even if they can't actually be used
  * #415 GetVendor: Kind of messy data
  * #413 Some items are classified
### Removed
* Vendor Categories was removed as a concept.  There was already no data populating for this type of entity in Destiny 2, so it shouldn't cause anyone harm.

## [2.1.3] - 2018-02-22
### Added
* Vendor definitions will now have "location" data, and DestinyVendorComponent will now have a "vendorLocationIndex" property. If a valid (>= 0) index, it will point to the index of DestinyVendorDefinition.locations data that you can use to show a vendor's destination and other human readable info. (actual population of that info is TBD, didn't quite make it out for release yet: but you can begin implementing against it in anticipation)
### Changed
* Vendor components should be getting returned now from requests. Some data, such as time sensitive items, may still be incorrect and will have fixes in the next release.
* Vendors will no longer be returned if they can't be accessed in the game by the character in question (for instance, Xur will only appear once he appears on the map on Friday: but also, if the character hasn't reached the point where they are at the Tower, they won't see Tower-related Vendors in the results) (spoiler alert for those who haven't beaten the D2 campaign yet, sorry not sorry)
* Further improvements to the new Advanced Write Actions
* The following Github Issues were addressed:
 * #412 NOTICE: DestinyVendorCategoryDefinition is going to be removed rfc
 * #411 NOTICE: The Aura activity bucket will be left unused starting 2/27
 * #402 RFC: emblemHash on DestinyCharacterComponent may no longer necessarily point to an emblem item
 * #399 Weapon Mods with empty itemCategoryHashes
 * #397 Include Mayhem in AllPvP mode
 * #395 The daily strike milestone claims to have 48 challenges! instead of 3
 * #394 Transfer between char x vault returning error for some item types
 * #393 Armour Ornaments missing itemCategoryHashes
 * #392 New Item Categories lack localized text for name/description
 * #379 Clarification around instanced reusablePlugHashes data
 * #348 Mayhem Mode in API
 * #334 Heroic Strike DestinyActivityModeType

## [2.1.2] - 2018-02-07
### Added
* New milestones added for the upcoming Crimson Days event
* Crimson re-added as a historical stats Activity Mode
* Still in-progress work for "Explore 2.0", which will be a new aggregation endpoint that provides a more personalized experience for the homepage and Companion.  Completion date TBD, still in early prototyping phase.  You'll see some new endpoints and contracts related to "Explore": pay no attention to the man behind the curtain!
* Ongoing work on Advanced Write Actions.  We will make an announcement later about how these can be used in conjunction with the API.  Rest assured that you will have to explicitly ask for permissions to use these new actions, that it will require 2 factor auth through Bungie's companion app itself, and that it will come with logging that users can inspect about actions taken through your app to safeguard your app from false accusations of undesired actions.
* #329, #322, #319, #206, #168 - A vast number of new Item Categories and ItemTypes/ItemSubTypes have been added.  Check the documentation for further details.
### Changed
* Vendor API responses should now have correct item component data.  We're still adding more tests and implementing features against this data ourselves, so I'm not going to pull it out of beta until I feel a high level of confidence in it.  But we're nearing the final threshold for having a fully functional vendor endpoint again.
* The "Trending" endpoint has been altered to make the front page of the site and app more news-oriented.
* #349, #88 - Challenges should be greatly improved, with proper challenges on Milestones that need them and not on ones that are unrelated.
* #348 - Mayhem mode should be working again in historical stats.
* #288 - Grenade kills should come through correctly once more.
* #181 - "Globally" applied stat bonuses from mods on equipped items now no longer get applied to any item other than the item on which it is equipped (if relevant to that item).
* #78 - Classified items now have a default blank icon applied to them.
* #166, #69 - Fixes to character stats that should not have been appearing, and forcing other stats to appear even if they are 0.

## [2.1.1] - 2017-12-15
### Added
- Added support for returning Objective/Progress information for Reusable Plugs. When you see plugs that you can insert into sockets, but require you to complete an Objective to do so, that objective information is now being returned. See the changes to DestinyItemSocketsComponent, as this has been modified to store additional data about reusable plugs.
DestinyItemObjectivesComponent now has an optional "flavorObjective" property. When items such as Emblems have stats that they show about the user, those are represented by flavorObjectives.
Various data is added for Masterworks sockets:
- #154 Equipment Slot definitions are now finally making it out to the manifest database.
- The ItemState enum has a new value, "Masterwork", that indicates whether the item has a Masterwork plug inserted (since this ItemState property is on the basic DestinyItemComponent, this makes knowing whether the item is a Masterwork easier than having to iterate through the plugs inserted into the item)
- Extra state information was added to DestinyItemPlugDefinition and DestinySocketTypeDefinition (and its children) that should be useful (see definition for new properties and their documentation). Notably, Socket Type actions now convey the rules under which a plug can be inserted into a socket of that type. (These rules keep piling on each other! Sockets are getting pretty complicated) Socket Type whitelists also have reinitializationPossiblePlugHashes, which is the list of possible masterwork plugs that could be inserted when you "reinitialize" a masterwork socket.
  - The template for player reporting URLs to redirect to us for player reports is:
    - https://www.bungie.net/en/PGCR/Report/[PGCR ID]/?characterId=[Offending Character ID]
    - It's kind of ugly right now, something I need to fix up when I get the time.
### Changed
- #317 Fixed the issue where certain types of daily milestones were not being returned in all situations
- #324 Infusion Category changes mentioned in the bug have been implemented.
- Fixed a bug where challenges weren't being returned for Mercury's landing zone.
- Various items that should not have been redacted are now not redacted.

## [2.1.0] - 2017-12-05

### Added
- New "PullFromPostmaster" endpoint, and accompanying changes to contracts
- New "ReportOffensivePostGameCarnageReportPlayer" endpoint, allowing players to report players that violated terms of service in games in which they participated.
- New Milestones for DLC1 and Season 2.

### Changed
- Historical Stats APIs no longer in pre-release
- Vendor endpoint is still not quite ready for use, but the contracts are changing to better reflect the desired output of the API once it is ready for use. Comments and suggestions are welcome!
- Screenshots will now be at 1920 x 1080 resolution.

## [2.0.1 - 2.1.0] - 2017-09-05 through 2017-12-05

### Added
- Many changes were made over these months that I did not document well previously.  I doubt anyone will care at this point, so I'm not going to bother fishing them all out now.  But if anyone really cares enough that they want this historical information, file a Github issue and I'll get to it when we get to other documentation and spec improvements!  Better documentation for what was specifically going out with releases started with 2.1.0, see above for that history.

## [2.0.0] - 2017-09-03

### Added
- Initial implementation of Destiny 2 API, see documentation for more details
- Historical Stats are in a functional but Beta state, and have many bugs that still need resolving.
- Vendors are offline and not yet implemented; the endpoint and contract documentation is being provided for reference and public evaluation.
