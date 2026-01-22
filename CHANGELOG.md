# Changelog

## 2026-01-13 - 2.21.10 Release
- Resolved certain Renegades activities PGCR screenshots and activity modes to be incorrect
- Added Latest Release Trait hash to Constants which can be used to drive the New label for activities
- Resolved [###Destiny...###: Internal String Replacement #2047](https://github.com/Bungie-net/api/issues/2047)
- Resolved [EquipableItemSet.displayProperties.name do not match contemporary armor set names #2040](https://github.com/Bungie-net/api/issues/2040)
- Resolved [Instances of items having the wrong iconHash def properties #2038](https://github.com/Bungie-net/api/issues/2038)
- Resolved [Bug: Fully Masterworked Armor V3 Items Return Incorrect Stats via API #2000](https://github.com/Bungie-net/api/issues/2000)
- Added PGCR screenshot for D2 Equilibrium Dungeon
- Implemented [Add new API attributes to indentify endpoints with authorization #2008](https://github.com/Bungie-net/api/issues/2008)
- Added vanguardAlertsFireteamFinderActivityGraphRootNodeHash to GlobalConstants for the convenience of getting the vanguard alerts root node

## 2025-12-02 Update for Renegades 
- Added `unclaimedOrderRewards` and `orderRewardsUnlockValueHashesToRewardItemHashes` to offer a method of getting the number of type of earned, unclaimed rewards from Orders. 
- Added images for Featured Quests. 

## 2025-11-18 Portal Root Nodes and enum value fixes 
- Added `portalActivityGraphRootNodesWithIcons` to `DestinyGlobalConstantsDefinition` to assist Portal representation.
- Fix enum values being when Strings when intended to be Integers.

## 2025-10-14 Update for Portal Activities
- Added `curatorBlockDefinition` and `durationEstimate` to `DestinyActivityDefinition`.
- Added `difficultyTierCollections` and `selectableSkullCollections` to `DestinyCharacterActivitiesComponent`.

## 2025-09-26 Nullable Enum Properties
- Updated nullable enum type properties to reference the enum definitions, rather than redefining them.

## 2025-09-16 Extra Item Icon Layers 
- Added extra static item icon layer image paths to `DestinyInventoryItemConstantsDefinition`.

## 2025-09-10 Update for Ash & Iron
- Added `selectableSkullCollections` to `DestinyActivityDefinition`.
- Added `currentSeasonPassHash` to `DestinyProfileComponent` and `Destiny2CoreSettings`.

## 2025-08-26 Destiny Global Constants Definition
- Finally added specs for `DestinyGlobalConstantsDefinition`, but this has existed for a while now. Sorry!

## 2025-08-19 Item Icon Layers and PGCR Scoreboards
- Added `DestinyIconDefinition` for individual inventory item icon layers.
  - Added `iconHash` to `DestinyDisplayPropertiesDefinition` for inventory item icons only.
  - Also added useful static item icon layer image paths to `DestinyInventoryItemConstantsDefinition`.
- Added `scoreboardValues` to `DestinyPostGameCarnageReportExtendedData` for Crucible player scores, reward scores, multipliers, and more.
  - There will be some overlap between `scoreboardValues` and other existing stat values in PGCRs.

## 2025-08-05 Follow-up for The Edge of Fate
- Added `isHolofoil` and `isAdept` to `DestinyInventoryItemDefinition`.
- Fixed `DestinyItemFilterDefinition` and renamed `setItems` to `allowedItems`.

## 2025-07-29 Follow-up for The Edge of Fate
- Added account-owned `seasonPassHashes` to `DestinyProfileComponent`.
- Added `visibleRewards` to `DestinyActvity`, which includes Bonus Focus rewards from the Portal.
- Fixed the incorrect enum flag values for `DestinyGameVersions`.
- Removed Fireteam Finder API specs that are not available to 3rd-party apps.

## 2025-07-15 Update for The Edge of Fate
- Items
  - Added support for featured items and armor sets in `DestinyInventoryItemDefinition`.
  - Added the gear tier to `DestinyItemInstanceComponent`.
  - Added `DestinyInventoryItemConstantsDefinition` for gear tier icon overlays.
  - Added the featured items list and armor archetype plug set hash to `Destiny2CoreSettings`.
- Activities
  - Added support for activity families, traits, difficulty tiers, and selectable skulls in `DestinyActivityDefinition`.
  - Added the difficulty tier index and selected skull hashes to `DestinyPostGameCarnageReportData`.
- Seasons
  - Added `seasonPassList` to support two reward passes in a `DestinySeasonDefinition`.
  - Added the `seasonalHubEventCardHash` to `Destiny2CoreSettings`.

## 2025-05-09 Update for Rite of the Nine 
- Added new fields to `DestinyEventCardDefinition` to support Heavy Metal event cards. 
  - These fields are `eventCardCurrencyList`, `weeklyChallengesPresentationNodeHash`, and `rewardProgressionHash`.
- Fixed the `FireteamFinderApplicantNotInGame` Fireteam Finder error code. 
  - Now it is unique, rather than the same integer as another error code. 

## 2024-12-08 Update for the Dawning
- Added support for socket override definitions and states on season passes.
  - Added `socketOverrides` to `DestinyProgressionRewardItemQuantity` definitions to reference socket types and plug items.
  - Added `rewardItemSocketOverrideStates` to `DestinyProgression` for season pass rewards.
    - This includes `rewardItemStats` for armor rolls and `itemState` for Deepsight red-border weapons.
- Added support for virtual stack sizes on material requirements.
  - Added `hasVirtualStackSize` to `DestinyMaterialRequirement` definitions, which would require the new material requirement states.
  - Added `materialRequirementSetStates` to `DestinyCurrenciesComponent` with the `CurrencyLookups` component.
    - The `materialRequirementStates` include an `itemHash`, a required `count` and a current `stackSize` (which may be virtual).

## 2024-10-08 Update for Episode: Revenant
- Added `DestinyVendorItemComponentSet` to return `DestinyItemComponent` objects for Vendor sale items.
  - Request the `itemComponents` with the `ItemCommonData` component type.
  - `DestinyItemComponent.state` provides Deepsight red-border status.
  - `DestinyItemComponent.tooltipNotificationIndexes` provides tooltips, relevant for the new potions.
- Added `stackSize` and `maxStackSize` to socket plugs.
  - The `stackSize` shows the number of potions you've brewed in the Tonic Capsule sockets.

## 2024-07-16 Update for Lost Sectors

- Added `availableActivityInteractables` to `DestinyCharacterActivitiesComponent`.
  - Finally adds support for today's Expert and Master Lost Sector activities.
  - Also includes in-world activity interactables (totems) for campaign missions and the like.
  - Cross-reference with `availableActivities` for those that can also be launched from the Director.

## 2024-07-10 Update for The Final Shape

- Added `acts` to `DestinySeasonDefinition` for the new Episodes.
- Added an `isVisible` flag to `DestinyArtifactTierItem`.
- Added a new `DestinyActivityModeType` enum value for 'Relic' activities.
- Added a `recordTypeName` to `DestinyRecordDefinition`.
- Replaced `obscuredString` with `obscuredName` and `obscuredDescription` on record definition state blocks.
- Added `commendationNodePercentagesByHash` to `DestinySocialCommendationsComponent`.
- Added a `tintedIcon` to `DestinySocialCommendationNodeDefinition`.
- Added `guardianRankHashes` to `DestinyGuardianRankConstantsDefinition`.
- Added the `renewedGuardianRank` to `DestinyProfileComponent`.

## 2023-02-28 Update for Lightfall

- Added Loadouts, Guardian Ranks, and Commendations!

## 2022-12-06 Update for the Season of the Seraph

- Added `responseMintedTimestamp` and `secondaryComponentsMintedTimestamp` to DestinyProfileResponse.
  - Use these new values to handle stale cached responses from the `Destiny2.GetProfile` API.
- Added new EquipFailureReason enum flag values, and renamed `ItemNotOnCharacter` to `ItemWrapped`.
- Added new `categoryfilter` and `includebody` parameters to the `/Content/Rss/NewsArticle/<page>/` API.
  - Going forward, new news content will be available via the RSS feeds and this API.

## 2022-08-23 Update for the Season of Plunder

- Added Support for Epic Games accounts.

## 2022-07-19 Update for Solstice 2022

- Added `DestinyEventCardDefinition` for the new seasonal Event Card feature.
  - The Event Card challenges root node has three child nodes (one for each character class), so clients should respect node visibility to show the appropriate records.
- Added new properties for `eventCardHashesOwned` and `activeEventCardHash` to `DestinyProfileComponent`.

## 2022-05-24 Update for the Season of the Haunted

- Added new `DestinyActivityModeType` enum values for Zone Control, Rift, and Iron Banner: Rift.
- Added a `displayHint` string property to `DestinyTraitDefinition`.
- Added a `shouldShowLargeIcons` boolean property to `DestinyRecordDefinition`.
- Added a new `DestinyVendorItemState` enum value for `Locked` sale items.

## 2022-05-01 Update for housekeeping

- Added a definition mapping and specification for `DestinySandboxPatternDefinition`.
- Fixed the `DestinyTraitCategoryDefinition.traitHashes` mapping to properly reference `DestinyTraitDefinition`.
- Added a deprecation warning to `DestinyObjectiveDefinition.valueStyle`, which is no longer populated by game content.
  - Please use `inProgressValueStyle` and `completedValueStyle` instead.

## 2022-02-22 Update for The Witch Queen

- Items
  - Added new `ItemState` flag values for Shaped (`Crafted`) and Deepsight (`HighlightedObjective`) weapons.
  - Added `DestinyItemCraftingBlockDefinition` for more details in crafting recipe (Pattern) item definitions.
  - Added `recipeItemHash` to `DestinyItemInventoryBlockDefinition` for a reference to the crafted item's recipe (Pattern) definition.
  - Added `craftingRequirements` to `DestinyItemSocketEntryPlugItemRandomizedDefinition` for plugs used in crafting.
    - New 'Enhanced Trait' plug item definitions have an `inventory.tierType` value of `Common` (3) instead of `Basic` (2).
  - Added a new `DestinyItemSubType` for `Glaive` weapons.
- Objectives
  - Added `uiLabel` and `uiState` properties to `DestinyObjectiveDefinition`.
  - Added `DestinyObjectiveUiStyle` enum values for highlighted objectives (Deepsight), crafted item objectives (date, level, progress), and memento reward objectives.
  - Added `LevelAndReward` to `DestinyUnlockValueUIStyle` for memento reward objectives.
- Craftables
  - Added the `craftingRootNodeHash` to `Destiny2CoreSettings` for the display of Shaping progress.
    - The `exoticCatalystsRootNodeHash` now includes unlock progress records for weapon shaping 'Patterns' as well as Exotic Catalysts.
  - Added `craftables` (crafting recipe items) as children of `DestinyPresentationNodeDefinition`.
  - Added a new `Craftables` enum value for `DestinyComponentType` for use with `GetProfile`.
  - Added `characterCraftables` state to `DestinyProfileResponse`.
    - Only initial Shaping state is returned, not Reshaping state.
- Material Requirements can now have non-constant values.
  - Added `countIsConstant` for constant `count` values.
  - Non-constant counts will have a value of `0` in the definition.
  - We plan to add support for non-constant counts in the API, but we don't have an ETA.
- Activities
  - Added `activityWasStartedFromBeginning` to `DestinyPostGameCarnageReportData` as an alternative to `startingPhaseIndex`.
  - Added a new `DestinyActivityModeType` enum value for `Offensive` activities.
    - We plan to add another enum value for Master and Legend `LostSector` activities soon.

## 2022-01-06 Update for Mapped Definition Attributes

Added hash-to-definition-type mapping attributes that were missing for many contract class properties.

## 2021-12-07 Update for Bungie's 30th Anniversary

Added a new `InsertSocketPlugFree` API for 'free and reversible' socket actions available to 3rd-party Destiny 2 apps (no new application scopes required).
- This includes Armor 2.0 mods, Weapon perks, Stasis abilities, Shaders, Ornaments, and Ghost Projections.
  - Only 'randomized' or 'reusable' socket plugs items with no 'insertion material requirements' will be allowed.
  - You will not be able to overwrite a 'non-free' plug item with a 'free' plug item (for example: replacing a Weapon mod with an 'Empty Socket Mod').
- 3rd-party Destiny 2 apps will still not be able to spend your currencies for socket actions.
  - As such, 3rd-party Destiny 2 apps won’t be able to apply Weapon and Armor Masterwork tiers, Weapon mods, Armor 1.0 mods, Ghost 2.0 mods, and Ship Transmat effects.
- `Destiny2CoreSettings` includes new hash arrays for some additional restrictions:
  - Check `insertPlugFreeProtectedPlugItemHashes` for protected plug item hashes that you can't overwrite (currently just Riven's Curse and Transcendent Blessing mods).
  - Check `insertPlugFreeBlockedSocketTypeHashes` for blocked socket type hashes that you can't change (currently just Weapon 'Kill Tracker' sockets).
- The `InsertSocketPlugFree` API will initially be rate-limited to 2 socket actions per-second, per-user.
  - This rate can be adjusted based on your feedback and service stability.

## 2021-11-18 Update for Bungie Name Search

Added new Bungie Name search APIs with POST requests for special characters.
- You can call these to find player names that have colons, slashes, angle brackets, etc.

## 2021-10-12 Update for Uninstanced Item Perks

Added support for perk state components on uninstanced items.
- Mostly just for the Trials of Osiris 'Passage' quest items to show whether a 'Mercy' has been used or not.

## 2021-09-03 Update for Display Name Search and Stasis Energy

Added docs for the new Bungie Name search API and the Stasis Energy type enum value.

## 2021-08-24 Update for Cross Play and the Season of the Lost

Added Bungie Names and Bungie Friends.

## 2021-05-25 Update for Vendor String Variables

Added the 'StringVariables' component option to the D2 Vendor APIs.

## 2021-05-11 Update for the Season of the Splicer

Includes reward item visibility and string variables.
- String variable placeholders (formatted as {var:1234567890}) are found in Destiny definition localized strings.
- D2 Profile API clients can request the new StringVariables component to get per-character integer values by hash.
- Clients can then replace the {var:(hash)} placeholders with the corresponding integer values.
- String variables are currently used in the following places:
  - Armor Synthesis bounties from Ada-1 (descriptions, reward names, tooltips, failure strings)
  - A single Seasonal Challenge record description

## 2021-02-09 Update for the Season of the Chosen

Includes seasonal challenges, item flavor text, gilded titles, record interval rewards, and season preview definitions.

## 2020-12-08 Update for Destiny 2 version 3.0.1

Includes 'ApiPurchasable' values for vendor items, and 'currentlyCanRoll' for randomized socket plugs.

## 2020-11-19 Update for Ghost Energy

Includes new enum values for Ghost and Subclass energy types.

## 2020-11-10 Update for Beyond Light and the Season of the Hunt

Includes changes for Stasis, item icon watermarks, 'Active' and 'Legacy' Triumphs, and scored presentation nodes.

Caveat - The new energy type for Ghost mods is not yet implemented.

## 2020-07-07 Update for Bungie Day 2020

Includes changes for the 'SetTrackedState' API and the current season reward power cap.

## 2020-06-09 Update for Season of Arrivals

Includes changes for Season of Arrivals, item versions, and power caps.

## [2.8.0] - 2020-03-10

Almost a year since we last touched this changelog!

For this release, we've updated content for the Season of the Worthy and Trials of Osiris, and added support for new Traits, Trait Categories, and Metrics (aka Stat Trackers). We've also added 'icon sequences' to display properties, so that all of the icon frames from the game are now included in the content definitions.

## 2020-02-13 Late Winter Refresh

Upkeep update.  Includes traits info and new activity types.

## 2019-12-05 Winter Wishlist!  File your requests here!

Go here for more information: https://github.com/Bungie-net/api/issues/1158

We would love your input!  Even though we will have a very limited amount of time to work on improvements over the upcoming holiday season, it'll still be useful to know what you folks consider to be the highest priorities so that we can hopefully push in those directions in the coming year!

## 2019-09-26 Pre-release Shadowkeep API Changes

Head here for more information: https://github.com/Bungie-net/api/wiki/2.4.0-(Shadowkeep)-API-Changes

## [2.3.5] - 2019-03-19

I've been gone for a bit, so there's some other mostly content changes that have occurred between 2.3.4 and 2.3.5, but aside from that only some small changes have occurred in the API.

* Activity Categories and Modes now includes Gambit Prime and Reckoning, though Reckoning is experiencing ongoing issues with data consistency that may not be resolved given the way that the activity is set up.  For the forseeable future, we recommend not attempting to build features around Reckoning historical stats.
* Removed some API endpoints that aren't actually possible to use with the rights we allow Applications to ask for.
* Some minor bug fixes for Milestones, and addition of new Vendor and PGCR data for Season of the Drifter.

## [2.3.4] - 2019-01-29

In this patch, we have several changes from the Winter Wishlist, along with new content for Crimson Days and a variety of other smaller changes.

### Added/Changed
* Github Issues Resolved:
  * https://github.com/Bungie-net/api/issues/148 Add data to schema to indicate Flag enumerations
  * https://github.com/Bungie-net/api/issues/77 gendered*Names properties keyed by English strings
  * https://github.com/Bungie-net/api/issues/472 allPvP is including private matches
  * https://github.com/Bungie-net/api/issues/502 Provide a public Xur API
  * https://github.com/Bungie-net/api/issues/566 The Fall Will Kill You Objective is still classified 
  * https://github.com/Bungie-net/api/issues/642 Release custom icon font
  * https://github.com/Bungie-net/api/issues/696 Vendor Lord Saladin's manifest definition has missing info
  * https://github.com/Bungie-net/api/issues/712 Can Competitive be added to the DestinyActivityModeType?
  * https://github.com/Bungie-net/api/issues/761 Feature Request: Add Vendor Hash to Applicable Items
  * https://github.com/Bungie-net/api/issues/796 Add Lord Saladin to Iron Banner Milestone [3427325023]
  * https://github.com/Bungie-net/api/issues/803 Add Triumph rewards to manifest
  * https://github.com/Bungie-net/api/issues/805 Sub-ranks for Valor and Glory are not reflected in the api
  * https://github.com/Bungie-net/api/issues/808 Clan Staffs are Classified
  * https://github.com/Bungie-net/api/issues/811 Account for randomized perks in base item definition stats
  * https://github.com/Bungie-net/api/issues/833 ActivityMode 68 (IronBannerSalvage) returning Iron Banner Control activities
  * https://github.com/Bungie-net/api/issues/844 Vendor caching is f'd
  * https://github.com/Bungie-net/api/issues/849 Activity history for forges

## [2.3.3] - 2018-12-11

We've actually had a series of smaller updates and fixes between 2.3.2 and 2.3.3, but this is a rough outline of the changes as of today's deployment to catch us up.

### Added/Changed
* Github Issues Resolved:
  * #805 Sub-ranks for Valor and Glory are not reflected in the api
  * #785 The manifest will start including JSON-formatted Destiny definitions definitions 
  * #784 GameVersion in GetProfile once black armory comes out 
  * #771 Destiny endpoints will begin returning DestinyThrottledByGameServer in periods of high traffic
  * #753 titles on Seal records not populated 
  * #744 Too many items' data returned in ItemComponents with GetProfile/GetCharacter/etc requests 
  * #742 Leviathan in Milestone Endpoint returns 2 normal and 2 GG hashes 
  * #724 2 burst side arms report 'zero' rounds per minute in the api 
  * #714 Some weapon show not available masterwork Tier upgrades 
  * #696 Vendor Lord Saladin's manifest definition has missing info 
  * #694 Record Objective 
  * #651 GetHistoricalStats (account or character) endpoints will not return Gambit/PvECompetitive stats for now 
  * #77 genderedNames properties keyed by English strings

## [2.3.2] - 2018-09-19

### Added/Changed
* Many entities unredacted.  More to come in 2018-10-02 release.
* Presentation Nodes now have an "Obscured" state, to reflect that state as it exists in the game
* Ongoing work to fix Activity Modes that are broken, and add support for upcoming activity modes
* Added Vendor and Item refresh/expiration dates (referenced through the issues below, but may be unclear unless you read all the details)
* Github Issues Resolved:
  * #646 - Forsaken Checklist Updates
  * #666 - Nightfalls' (et al) manifest displayProperties.name is just "Nightfall"
  * #665 - PGCR Returning Mode 0
  * #659 - Expiration time for items (bounties)
  * #654 - Vendors (esp. Spider): wrong RefreshDate
  * #651 - GetHistoricalStats (account or character) endpoints will not return Gambit/PvECompetitive stats for now
  * #650 - Stats not returning Bow, Beam Rifle weapon/precision weapon stats
  * #649 - sourceString hash for collectibles
  * #648 - Public Milestones reports wrong end dates for 4 day reset items
  * #641 - Need a Forsaken flag in DestinyGameVersions
  * #638 - DestinyUnhandledException for various Stats endpoint calls on some accounts/activity modes
  * #637 - Legendary/Rare Energy/Power with Kinetic Damage Type
  * #629 - Daily Crucible Challenge missing from Milestones when Weekly Flashpoint is completed
  * #628 - Unable to map Daily Heroic Story Mission Activitiy to specific mission
  * #624 - Feature request: collectableHash on items
  * #622 - (Some?) Items with Kinetic Damage have damageTypes but empty damageTypeHashes

## [2.3.1] - 2018-09-14

### Added
* Changes related to new features in Forsaken (See [the Wiki](https://github.com/Bungie-net/api/wiki/2.3.0-and-2.3.1-Changes-(Forsaken-Release)) for more information)

### Changed
* See the wiki linked above for more information: it covers the significant changes in this release.

## [2.3.0] - 2018-08-28

### Added
* Changes related to new features in Forsaken (See [the Wiki](https://github.com/Bungie-net/api/wiki/2.3.0-and-2.3.1-Changes-(Forsaken-Release)) for more information)

### Changed
* See the wiki for more info: Milestones in particular have changed in potentially backwards-incompatible ways

## [2.2.2] - 2018-06-27

### Fixed
* #539 Curse of Osiris milestones
* #532 [question] where to get flashpoint location ?
* #523 Known Issue: Clans may be inaccessible, increase in timeouts
* #522 plugSources does not seem correct for shaders
* #514 Wrong kills/deaths/assists numbers for Rumble
* #513 "You're Welcome" ghost perk incorrectly classified as a Weapon Mod
* #511 Glass modifier missing in DestinySandboxPerkDefinition
* #506 /Platform/GlobalAlerts/ 
* #493 Display properties for PlugSets

### Added
* Added a new component for Profile-level Progression data:  ProfileProgressions.
  - For now, this will only have checklists.  More will likely be added to it as time goes by.
* Added the concept of [DestinyChecklistDefinition](https://bungie-net.github.io/multi/schema_Destiny-Definitions-Checklists-DestinyChecklistDefinition.html#schema_Destiny-Definitions-Checklists-DestinyChecklistDefinition), and checklist data to Progression components returned from the API.
* Added some throwaway APIs for an upcoming update to the game.
  - If you happen to dig through our Platform Client Javascript libraries to find our unpublished APIs, you'll likely see some APIs about "Triumphs."  Yes, Triumphs are coming.  Please don't build anything that relies on these endpoints: as the name of them implies, they're going to be thrown away once Triumphs is over.  Such is the ethereal and ever-changing nature of Triumphs.  It's very Zen-like, I assure you.  The data that will both be truly interesting and that will actually persist once Triumphs is over is in the new Checklists data.  (though not all checklists will be used in Triumphs, and vice-versa!  I tried to get you all as many checklists as I could find data for.)

## [2.2.1] - 2018-05-30

### Added
* A new endpoint, ["GetLinkedProfiles"](https://bungie-net.github.io/multi/operation_get_Destiny2-GetLinkedProfiles.html#operation_get_Destiny2-GetLinkedProfiles), has been added to the Destiny 2 endpoints.  The hope is that this will simplify some of your workflows if you find you've had to do a lot of manual workarounds and querying to find out if linked Platform accounts actually have Destiny information.
* A new activity mode, "Showdown", has been added.

### Fixed
* #504 : Known issue: "Crucible Labs" Activity Mode won't be in data until May 30th, Crucible Labs PGCRs will return as "All" until then. bug 
* #501 : Equip Items (added a workaround where logged off characters can still equip)
* #485 : New Warmind items are not appearing in screenshots bug
* #476 : Official companion app doesn’t display the counter on Sentinel’s Shove bug
* #470 : The new Warmind vendor's (Ana Bray) faction definition is lacking tokenValues property bug investigation
* #469 : Since Warmind itemState property is not showing if an item is a masterwork bug
* #468 : Known bug: Nightfall Score Multiplier and Handicap not being returned bug
* #466 : Content Warning for DLC2: Several Activities removed from database, replaced with variants that have only changed identifiers definitions

## [2.2.0] -2018-05-08
### Added
* Item Stats now have "categories" enum, in case you want to sort stats
* Equipment Slot Definitions now have Art Dye Channels, so you don't have to hard code what channels to apply to items in a given equipment slot if you're doing 3D rendering.
* Item Preview Blocks now expose a "screenStyle" property: a string that the game UI (and you!) can use as a hint for how the item should be rendered if shown in a preview window/view.
* Vendor Categories now have information indicating if they are for display only (i.e. you can't actually buy the items shown), whether there is a currency item shown as a "featured" currency for that section, and various new fields about progressions that can be shown along with the category and other display information and hints.
* Various Activity Modes have been added for Private Match subcategories and Heroic Adventures
	- The bug with private matches not categorizing correctly still exists, and will hopefully be resolved in time for the 5/16 BNet hotfix release.
* Objective Definitions now have new properties that can help you determine when you should show the objective's progress information (minimumVisibilityThreshold, allowOvercompletion, showValueOnComplete)
* Item's Plug definitions now expose style information that could be useful for you (styles, whether it's a "dummy" plug or a legitimate one etc...)
* Item's socket definitions now have "plug source" information, which tells you what components in live data need to be inspected to assemble all of the socket's possible reusable plug states.
* "Plug Sets" now exist as a concept: they indicate a set of reusable plugs that share common state across character or Account boundaries, and may be referred to by multiple sockets across multiple characters.
	* Paired with this is the new "profilePlugSets" and "characterPlugSets" components on GetProfile/GetCharacter which will give you this reusable plug information that was previously only found on the item's "itemSockets" component itself.
* Item Objectives can now optionally have a "dateCompleted", which will tell you when the objective successfully was completed if it has been.
* Vendor components now have an optional "seasonalRank" property, that will tell you the value of their rank for this season if the vendor has one.
* Vendor sale items now have "augments": a flags enumeration value that indicates modifiers you can apply visually to the items being sold.
* New Milestones for DLC2!
* Emote wheel support (through "Plug Sets", see above), though changing your equipped emotes must take place with an "insert plugs" operation now, which is not currently available to 3rd parties.  We hope to rectify that situation in the near future.
### Changed
* All PVP activities have had their identifiers altered in game content, and thus the hash identifiers for them have been altered as well.  PGCR data should compensate for this automatically, but if you had hard coded references to PVP activity names you will need to update those accordingly.

## [2.1.6] -2018-04-04
### Added
* GetApplicationApiUsage - A new endpoint for viewing your application's API usage.
* Fireteam Services - Many new endpoints for creating Fireteams through Clans that result in on-console Fireteam creation.  Currently not available for 3rd party developers, but the documentation exists here for your reference in case we release this for more general use in the future.
* non-Crimson "Doubles" added as an Activity Mode, for potential future use.  Added an "All Doubles" mode as a parent mode to both Crimson Doubles and non-Crimson doubles.
* Added a field to mark some Item Categories as "deprecated": categories that neither have any items currently in that category, nor will likely have items in that category in the future, but that I won't remove from the API in case doing so would break anyone with hard references to them.

## [2.1.5] -2018-03-27
### Added
* Rumble as an activity mode
* A new component, CurrencyLookups, that you can ask for alongside Vendor data for a quick reference of the requesting character's items and quantities of those items.
### Changed
* The Vendor APIs are officially out of beta.  Have at them, and as usual file any bugs you see!

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
