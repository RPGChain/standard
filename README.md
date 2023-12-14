# RPGChain Standard

## Overview

The RPGChain Standard is an open format for writing quests or stories in a text-based format that offer interactive choose-your-own path style choices and randomized dice rolls.

This document provides a comprehensive guide to the quest file format. RPGChain quests are structured in a json file format. Below is a detailed explanation of each element within the RPGChain quest file.

For a detailed look at the RPGChain Standard, view [resources/rpg-chain-standard.json](resources/rpg-chain-standard.json)

For an example quest file, view the examples folder in this repository.

## Version

To ensure compatibility across version changes, the quest file should specify the RPGChain standard version used

- **rpgChainStandardVersion**: `string`  
  Indicates the version of the RPGChain standard used.  
  Example: `"0.1"`

## Quest Properties

### name

- **type**: `string`  
  Title of the quest.

### description

- **type**: `string`  
  Brief description of the quest.

### image

- **type**: `string` (optional)  
  - **format**: URL  
  - **default**: `null`  
  URL to the quest's cover image file.

### playable_starts_at

- **type**: `string`  
  - **format**: date-time  
  Date and time when the quest becomes available to play.

### playable_ends_at

- **type**: `string`  
  - **format**: date-time  
  Date and time when the quest is no longer playable.

### private

- **type**: `boolean` (optional)  
  - **default**: `true`  
  Indicates whether the quest should be listed in the main index of quests.

### token_contracts

- **type**: `array` (optional)  
  - **default**: `[]`  
  - **items**: `string`  
  - **item format**: Ethereum contract address  
  List of Ethereum contract addresses allowed to interact with this quest. If empty, any player can access.

## Game Mechanics

### rolls

- **type**: `array` (optional)  
  - **default**: `[]`  
  Array of roll mechanics involved in the quest. Each roll object has the following properties:
  - **dc**: Difficulty class or target number for the roll.
  - **key**: Unique identifier for the roll.
  - **label**: Visible label for the roll.
  - **actionSuccess**: Reference to the action on a successful roll.
  - **actionFail**: Reference to the action on a failed roll.

## Quest Content

### pages

- **type**: `array`  
  Array of pages that constitute the quest. Each page object has the following properties:
  - **key**: Unique identifier for the page.
  - **markdown**: Markdown content of the page.
  - **image**: URL of the image associated with the page (optional).
  - **options**: Array of options available on the page (optional).
  - **displayRolls**: Array of rolls to be displayed on the page (optional).
  - **xp**: Experience points awarded for the page (optional).
  - **completionStatus**: Status indicating the completion result of the quest (optional).

---

## Additional Notes

- The `optional` tag indicates that a property is not mandatory and can be omitted. Default values are provided for these properties.
- Use the `enum` values precisely as specified for properties like `completionStatus`.
- Ensure all URLs provided in the `image` properties are accessible and correctly formatted.

---
