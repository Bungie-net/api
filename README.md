# The Bungie.Net API

Full Documentation: https://bungie-net.github.io/multi/index.html

Documentation as one single, gigantic page: https://bungie-net.github.io

This section will be added to as time goes by - we're working with it as we go!

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

## 2020-03-10 Update for Season of the Worthy

Includes changes for Season of the Worthy, Trials of Osiris, and Stat Trackers (aka Metrics).

## 2020-02-13 Late Winter Refresh

Upkeep update.  Includes traits info and new activity types.

## 2019-12-05 Winter Wishlist!  File your requests here!

Go here for more information: https://github.com/Bungie-net/api/issues/1158

We would love your input!  Even though we will have a very limited amount of time to work on improvements over the upcoming holiday season, it'll still be useful to know what you folks consider to be the highest priorities so that we can hopefully push in those directions in the coming year!

## 2019-09-26 Pre-release Shadowkeep API Changes

Head here for more information: https://github.com/Bungie-net/api/wiki/2.4.0-(Shadowkeep)-API-Changes

# I'm New to the API.  What can I do with it?
- (TODO: Create a grand overview tour of Destiny API features for new users in wiki, including how to get mobile databases and what the heck a mobile database is)

# How do I register to use the API?
- You're in luck!  Check out our wiki article... in fact, check out the wiki in general, we'll be adding to it as time allows:

https://github.com/Bungie-net/api/wiki/Bungie.net-Application-Portal

# Are there any restrictions on the API?

Right now the API doesn’t require a User-Agent header for requests and we haven’t set a standard for one. We will continue the policy of not requiring one for the foreseeable future. Starting now we do ask you send a User-Agent header as a best practice. Your agent string should include the app name and ap-id with an optional web url and/or email address. A suggested format is “AppName/Version AppId/appIdNum (+webUrl;contactEmail)” 

For example: 
User-Agent: Really Cool App/1.0 AppId/#####  (+www.example.com;contact@example.com)

It would be helpful to us and may also allow us to provide more detailed metrics in the future to app owners who provide one. On the off chance we need to contact you about your app this will help us reach out to you and may prevent us from having to disable an app (though only as a last resort!).

# What about the Destiny 1 API?
- It is alive and well, under the /d1/Platform/Destiny/ root URL.  We unfortunately don't have the time to write documentation for the D1 API, but community member Lowlines made [this fantastic documentation](http://destinydevs.github.io/BungieNetPlatform/docs/Getting-Started).  Buy him a beer sometime, or name your first kid after him or something.  Or donate to him if he accepts donations, which he should because the work he did in D1 was totally boss.

# I'm a Destiny 1 API Veteran.  What's new in the API?

- ### Component-based Destiny Requests
  - [Destiny2.GetProfile](https://bungie-net.github.io/multi/operation_get_Destiny2-GetProfile.html#operation_get_Destiny2-GetProfile), [Destiny2.GetCharacter](https://bungie-net.github.io/multi/operation_get_Destiny2-GetCharacter.html#operation_get_Destiny2-GetCharacter), and [Destiny2.GetItem](https://bungie-net.github.io/multi/operation_get_Destiny2-GetItem.html#operation_get_Destiny2-GetItem) are now the fundamental building blocks of Destiny data, replacing our large and disparate specialized endpoints.
  - GetCharacter and GetItem are provided for situations where you know the specific character or item you're looking at in your UI, but we fully anticipate that most calls will be made through GetProfile.  At any layer of depth, you can now get any data for the layer below by passing the components you want returned in the ?components= querystring parameter of the method.
  - For example, you can pass the CharacterInventories component to GetProfile, and you will receive the full inventory for all characters (provided that they have granted you permission to access that data, in the same way as in Destiny 1: our privacy policies and settings have not changed since D1, and still apply to D2 data).
  - In this way, my hope is that we can reduce the number of round trips you're currently having to make, while letting you control how much bandwidth you use up.  Ask for only the components that you need!

- ### Milestones
  - Advisors have disappeared, but in their place are ["Milestones"](https://bungie-net.github.io/multi/schema_Destiny-Definitions-Milestones-DestinyMilestoneDefinition.html#schema_Destiny-Definitions-Milestones-DestinyMilestoneDefinition).  Mirroring the game's concept of Milestones, these reflect all of the activities that a player can do in game.  Essentially these become Advisors with matching Definition data, which reduces the payload we have to return in live requests and makes including Milestone information as part of a Profile or Character request more feasible.
  - We will, as we did with Advisors, tack on additional data that we can associate with the Milestone where possible and add to it over time.
  - Milestones will, like Advisors, continue to evolve over time - and, like Advisors, I will probably come to regret how I implemented our view of them.  But for now, I feel hopeful.
  - Like Advisors, there are "Public" Milestones: views of what can be done in the game right now agnostic to an individual player's state.  For this information, you will want to seek out [Destiny2.GetPublicMilestones](https://bungie-net.github.io/multi/operation_get_Destiny2-GetPublicMilestones.html#operation_get_Destiny2-GetPublicMilestones).
  
- ### The Near-Deprecation of Talent Grids
  - In an act that I can only describe as Benevolence, the designers turned away from Talent Grids like they were going to turn into a pillar of salt.
  - Unfortunately, Talent Grids aren't dead entirely.  Items may still have them, and they have even more rules stacked on top of how they work now, to support the one place where they currently are still being used: Character Builds/Subclasses.
  - Please see [DestinyTalentGridDefinition](https://bungie-net.github.io/multi/schema_Destiny-Definitions-DestinyTalentGridDefinition.html#schema_Destiny-Definitions-DestinyTalentGridDefinition) to delve into the abyss.
  - Eventually, I would like to create a derivative definition of this specifically for Builds in an attempt to simplify what you have to understand: but I did not find time to do so before release (and I'm not 100% confident that I'd be able to remove enough complexity for it to be worth it to create a derivative definition).

- ### The Ascent of Sockets for Item Customization
  - In the place of Talent Grids, the notion of Sockets and Plugs are now the primary means of customization of items.
  - Read more in [DestinyItemSocketBlockDefinition](https://bungie-net.github.io/multi/schema_Destiny-Definitions-DestinyItemSocketBlockDefinition.html#schema_Destiny-Definitions-DestinyItemSocketBlockDefinition) and its children, as well as [DestinyItemPlugDefinition](https://bungie-net.github.io/multi/schema_Destiny-Definitions-Items-DestinyItemPlugDefinition.html#schema_Destiny-Definitions-Items-DestinyItemPlugDefinition) to find out how Sockets and Plugs work.  (to note, both of these are child properties of [DestinyInventoryItemDefinition](https://bungie-net.github.io/multi/schema_Destiny-Definitions-DestinyInventoryItemDefinition.html#schema_Destiny-Definitions-DestinyInventoryItemDefinition), that old venerable bolt-on of functionality.

- ### (Add more... probably redirect this to a set of wiki pages)
  
# Swagger/OpenAPI Specs (or, how to generate your own clients for the BNet API)

- Grab [openapi.json](https://github.com/Bungie-net/api/blob/master/openapi.json) for the OpenAPI 3.0.0 specs
- Grab [openapi-2.json](https://github.com/Bungie-net/api/blob/master/openapi-2.json) for the 2.0.0 specs

NOTE: There are currently bugs in the generated documentation: it worked well enough to build the HTML documentation you'll see at the links above, but users are reporting a variety of issues - and in some cases, missing data - when they go to generate clients.  Due to severe time constraints, I've not been able to prioritize fixing bugs in the documentation.  It's still on our backlog, but for now any client generators you build will have to work with what we've got.

# Extension Properties on OpenAPI Specs (or, how to generate much cooler clients for the BNet API if you want to take the time to do so)

- **x-mapped-definition** = This property has hash identifiers that map to a Manifest Database definition.  This property will reveal which type of Manifest Database definition it points to.  If it's a uint32, it points to a single definition.  If it's a List<uint32>, each value points to a different definition.  If it's a Dictionary<uint32, X>, its' keys point to different definitions.

- **x-mobile-manifest-name** = If populated, this is the name of the Mobile Manifest table that holds this data as a first-class entity.  The existence of this field implies that this entity is a first-order Destiny Definition aggregate.

- **x-enum-values** = I really hate that the OpenAPI spec doesn't have a way to tell you both the identifier and the numeric value of an enum, much less documentation for enum values, so I added this extension as a way to return that info.  It'll give you way more than the basically useless base "enum" property.

- **x-destiny-component-type-dependency** = A new concept in the Destiny 2 API is "Components".  You will see that our Destiny Profile/Character calls have been mostly simplified down to just GetProfile/GetCharacter/GetItem.  This simplification is made possible by Components, which are identifiers you pass into the requests to specify how much data you want back.  An entity with this property will only be returned if you've passed the named Component Identifier into the GetProfile/GetCharacter/GetItem methods.

- **x-dictionary-key** = OpenAPI didn't have a good way for me to specify that the key of a dictionary was actually meant to be something other than a string (even if always encoded as a string in JSON).  This extension property lets me tell you what it *really* is, so you can strongly type it and convert it if desired.

- **x-preview** = This boolean indicates that the Operation in question is not yet ready for prime time.  You will have to read the documentation to find out just *how* not ready it is, at least for now.

# FAQ

- Certain APIs are marked as PENDING in the documentation, what does that mean?
  - This may mean that their tentative contracts are being exposed in the documentation for review, or that they're going to be live but in a "Beta" state.  Look at the description of the specific endpoint for details.

- Can you provide documentation for the specific stat properties and modes that will be returned?
  - For the time being, we can't reveal that data.  I apologize for the inconvenience!

- How do I do X?  What does Feature/Property Z mean?
  - If you've got specific questions, please add a [Question](https://github.com/Bungie-net/api/labels/question) to our Issues list!  We'll try to answer as time allows, and we'll use this input to improve our documentation!
  
- I have suggestions on how to improve the API/alternative ways I'd like to see the data returned!  Where can I submit that input?
  - Add an [Enhancement](https://github.com/Bungie-net/api/labels/enhancement) request to our Issues list!  As time allows, we'll comb through them.  This will be particularly useful for Pending endpoints like Vendors, where there's still time to improve on the contracts before we turn them on.
  - Ideally, I'd like to see these become a place where the dev community as a whole can debate on the benefits and drawbacks of a change to the API, which will help us all to make the experience better for everyone.
  - It'll be a bit harder to make contract-adjusting changes to endpoints that are already release ready, but we can discuss ways to extend it.  If the enhancement is compelling enough, it may even be worth versioning the API.  But we're going to try to avoid that if at all possible.
  
- I've found a bug!
  - Please start up a [Bug](https://github.com/Bungie-net/api/labels/bug) in the Issues list!  It'll give us a good place to organize bugs that are reported, and to report back on them when they are fixed.
  - Note that the API is only part of the work that we do, and we have ongoing Bungie.Net feature work that sometimes pulls us away from the API: as such, Bugs may take a while to be resolved depending on other issues on our plate.  But my hope is that this location will help to make community-located bugs more exposed and easier to track, which should help us in our own prioritization of tasks!
  
- I need technical support for the game! (or Please give me loot!)
  - None of us here have access to the specialized support tools required to diagnose in-game issues and/or give sweet/phat lootz.  Please hit up the #Help forums on Bungie.net if you have technical support questions aside from the API itself!

- Will I be denied access to GetProfile/GetCharacter/GetItem if I lack OAuth scopes?
  - You will *not* be denied results if you don't have particular scopes, but components will be denied to you.  I don't have a good way of encoding this in the spec at the moment, but I will look into doing so in the future (potentially as an extension property, as there's no good way to encode partial success due to OAuth scopes):
  - ReadDestinyVendorsAndAdvisors is required for characterActivities, characterProgressions, kiosks and characterKiosks
  - ReadDestinyInventoryAndVault is required for profileCurrencies, profileInventory, characterInventories and vendorReceipts
  - That is all in addition to the user's privacy settings: you may still be denied the component if you're not passing their auth token and you're asking for components that they've marked private.  Your app should always assume and be able to handle the situation where an expected Component is not returned to you, even if the handling is just showing the user an error message. (if you can of course, a more elegant handling of the situation is always preferred!)
  
- Where are my consumable items?
  - Consumables are now in an Account-level bucket called "Consumables".  They are shared across all of your characters, meaning that you don't have to transfer them back and forth anymore.  Oh, glorious day!
  
- I have a project I'd like to recruit help for, or one that I'd like to show off!
  - We're trying to keep the "Issues" section specific to the API itself, BUT you should definitely go to the officially unofficial Discord for the Bungie.Net API, set up by community member Xorth: https://discord.gg/E5uB4BW There are sections over there for project promotion, general discussion and so on!
  
- I am unable to get results from endpoints that require authentication.  I always get WebAuthRequired back, even though I am passing both my X-API-Key header and the Authorization header.
  - It turns out, if you hit the API with bungie.net rather than www.bungie.net, we currently redirect you and lose the authorization header in the process.  I'd like to fix this along with resolving other redirection issues covered in https://github.com/Bungie-net/api/issues/55, but for now be careful that you're using exactly https://www.bungie.net for your URLs, and make sure that your URLs are terminating with a trailing slash (/).  Otherwise, you'll encounter our undesirable redirections.
  
- Were you sent here by the devil?
  - No, good sir, I'm on the level!

# Known Issues

- If our environment goes down entirely, to the point where we can no longer process your request, we are currently returning the same static error HTML page(s) to any API request that the website is returning.  If you get an HTML response to an API request, know that this is the undesirable side effect of our environment being down and handle it with your own messaging and error handling as needed.

- Some Vendors are currently showing incorrect items in certain situations/times of day (and in some cases, all the time).  Unfortunately the fix we need will require work that isn't going to go live until Forsaken goes live, which means that the Vendor endpoint will be somewhat unreliable until that time.  I apologize for the inconvenience this is causing.  The fix which will go live with Forsaken will hopefully solve Vendor consistency issues once and for all.
