# Changelog

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
