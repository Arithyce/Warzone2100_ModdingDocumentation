  
# Research Documentation <br>

## Format <br>

### Research body <br>

```json
	"______": {
		"id": "______",
		"name": "___",
		"techCode": _,
	},
```

### Arrays <br>

```json
		"replacedComponents": [
			"___:___",
		],

		"redComponents": [
			"___",
		],

		"requiredResearch": [
			"______",
		],

		"resultStructures": [
			"___",
		],

		"resultComponents": [
			"___",
		],

		"results": [
			{
				"class": "___",
				"parameter": "___",
				"value": ___,
			},
		],
```
**Note that comma placement isn't exact. You should generally leave out commas when they would be on the second to last entry.** <br>
See ["Research Temp.md"](https://github.com/Arithyce/Warzone2100_ModdingDocumentation/blob/main/Templates/Research%20Temp.txt) for common research templates. <br>
***

## Key Names from `research.json` <br>

Most keys are optional, asterisk denotes mandatory, double asterisk denotes conditionally mandatory (read description). <br>
The following will be appended to key names to denote their value type: <br>
Quotes are included, `compare: "old:new"`, `string: "value"`, `integer: whole number`, `float: decimal`. <br>
`double: whole/decimal`, `boolean: false/true`, `varies: depends on parent`, `null: no value`, `integer boolean: 0=false/1=true`. <br>
For keys that accept boolean or integer boolean, removing the key is equivalent to false. <br>

**Note that although the game accepts the double and float data types, the game rounds these up to a whole number.** <br>
**Keys here are in the order commonly found in `research.json`, however, they can be in any order.** <br>
- `disabledWhen` `Integer` <br>
  - `1`: Tanks, unused, `2`: Cyborgs, `4`: VTOLs, `8`: Satellite Uplink Center, `16`: Laser Satellite Command Post. <br>
- `iconID` `String` <br>
  - Icon shown on topic, go to [iconID](#iconid-) below for a list. <br>
- `id`* `String` <br>
  - Needs to be the same as the JS object name, and it needs to be unique. <br>
- `msgName` `Sring` <br>
  - Message ID of the message inside the Intelligence Display, see `mp/messages`, Mutual Exclusion: `techCode`. <br>
- `keyTopic` `Integer Boolean` <br>
  - Unused in multiplayer/skirmish. See the campaign documentation for it's use in campaign. <br>
- `imdName` `String` <br>
  - File name for the 3D model to be displayed in the topic, go to [3D Models](#3d-models-) below for a list, Mutual Exclusion: `statID`. <br>
- `imdName2` `String` <br>
  - File name for the 2nd 3D model to be displayed in the topic, go to [3D Models](#3d-models-) below for a list, Mutual Exclusion: `statID`. <br>
- `name`* `String` <br>
  - Display name. <br>
- `replacedComponents` `String Compare` <br>
  - Components to be replaced. `OldItem:NewItem`. The values must be in an array. <br>
- `redComponents` `String Array` <br>
  - Components to be made redundant without replacing. The values must be in an array. <br>
- `requiredResearch` `String Array` <br>
  - Research IDs of required research. The values must be in an array. <br>
- `researchPoints` `Double` <br>
  - How many research points it takes to research, max is `65535` (16-bit). <br>
- `researchPower` `Double` <br>
  - How much power it takes to research, max is `65535` (16-bit). <br>
- `resultStructures` `String Array` <br>
  - Structures to be made available. The values must be in an array. <br>
- `resultComponents` `String` <br>
  - Components to be made available.  The values must be in an array. <br>
- `results` `Null` <br>
  - Upgrades to be given, details follow. It must be an array. <br>
  - `class`* `String` <br>
    - Go to [Parameter Names](#parameter-names-from-the-source-code-) for a list of accepted values, each header except for `Filter Parameters` is an accepted value. <br>
  - `filterParameter` `String` <br>
    - The stat parameter to filter for, go to [Filter Parameters](#filter-parameters-) below for a list of useful ones. <br>
  - `filterValue` `Varies` <br>
    - The stat value to filter for, go to [List of weapon classes](#list-of-weapon-classes-) below for a list of weapon classes. <br>
  - `parameter`* `String` <br>
    - The parameter to be modified. See `Upgrade Parameter Doc.md` for a list. <br>
  - `value`* `Varies` <br>
    - The amount the parameter is modified by, can sometimes be negative. See `Upgrade Parameter Doc.md` for a list. <br>
- `statID` `String` <br>
  - The component or structure to be displayed in the topic, Mutual Exclusion: `imdName`. <br>
- `subgroupIconID` `String` <br>
  - Icon shown on the topic, go to [subgroupIconID](#subgroupiconid-) below for a list. <br>
- `techCode`** `Integer Boolean` <br>
  - No Intelligence Display entry, mandatory if `msgName` is not provided, Mutual Exclusion: `msgName`. <br>
***

## Parameter Names from the source code <br>

Special note for `HitPointPct`, it increases the total HP, it is 100% by default, giving +25% would buff final HP by 25%. <br>
This is additive, +25% to weapon, +25% to body, and +25% to propulsion would be 175% (+75%) total. <br>
Describing each parameter is outside the scope of this file, see `Upgrade Parameter Doc.md` for detailed decriptions. <br>
You may also be interested in `Key Name Table.md`. <br>

### Filter Parameters <br>

**Any of the parameters used in the source code work, but these are the useful ones.** <br>
`ImpactClass` `ImpactType` `Effect` `Id` <br>

### Body <br>

`Armour` `HitPointPct` `HitPoints` `Power` `Resistance` `Thermal` <br>

### Brain <br>

`BaseCommandLimit`  `CommandLimitByLevel`  `HitPointPct`  `HitPoints`  `RankThresholds` <br>

### Building <br>

`Armour` `HitPointPct` `HitPoints` `Limit` `ModulePowerPoints` `ModuleProductionPoints` <br>
`ModuleResearchPoints` `PowerPoints` `ProductionPoints` `RearmPoints` `RepairPoints` <br>
`ResearchPoints` `Resistance` `Thermal` <br>

### Construct <br>

`ConstructorPoints` `HitPointPct` `HitPoints` <br>

### ECM <br>

`HitPointPct` `HitPoints` `Range` <br>

### Propulsion <br>

`HitPointPctOfBody` `HitPointPct` `HitPoints` <br>

### Repair <br>

`HitPointPct` `HitPoints` `RepairPoints` <br>

### Sensor <br>
`HitPointPct` `HitPoints` `Range` <br>

### Weapon <br>

`Damage` `EmpRadius` `FirePause` `HitChance` `HitPointPct` `HitPoints` `MaxRange` `MinRange` `MinimumDamage` <br>
`Radius` `RadiusDamage` `ReloadTime` `RepeatDamage` `RepeatRadius` `RepeatTime` <br>
`Rounds` `ShortHitChance` `ShortRange` <br>

***

## List of weapon classes <br>

### Classes <br>

`KINETIC` `HEAT` <br>

### Sub Classes <br>

`MACHINE GUN` `CANNON` `MORTARS` `MISSILE` `ROCKET` <br>
`ENERGY` `GAUSS` `FLAME` `HOWITZERS` `ELECTRONIC` <br>
`A-A GUN` `SLOW MISSILE` `SLOW ROCKET` `LAS_SAT` <br>
`BOMB` `COMMAND` `EMP` <br>

### Effects <br>

`ALL ROUNDER` `ANTI PERSONNEL` `ANTI TANK` `ARTILLERY ROUND` `BUNKER BUSTER` `FLAMER` <br>

***

## Icon IDs <br>

### `iconID` <br>

**`iconID` icons are displayed in the top left.** <br>
- `IMAGE_RES_DROIDTECH` <br>
  - Droids. <br>
- `IMAGE_RES_WEAPONTECH` <br>
  - Weapons. <br>
- `IMAGE_RES_COMPUTERTECH` <br>
  - Research. <br>
- `IMAGE_RES_POWERTECH` <br>
  - Power. <br>
- `IMAGE_RES_SYSTEMTECH` <br>
  - Systems. <br>
- `IMAGE_RES_STRUCTURETECH` <br>
  - Structures. <br>
- `IMAGE_RES_QUESTIONMARK` <br>
  - Unknown. <br>
- `IMAGE_RES_CYBORGTECH` <br>
  - Cyborgs. <br>
- `IMAGE_RES_DEFENCE` <br>
  - Defenses. <br>

### `subgroupIconID` <br>

**`subgroupIconID` icons are displayed in the top right.** <br>
- `IMAGE_RES_GRPUPG` <br>
  - `(+)` All other upgrades not covered below. <br>
- `IMAGE_RES_GRPREP` <br>
  - Repair upgrade (components only). <br>
- `IMAGE_RES_GRPROF` <br>
  - Rate-Of-Fire upgrade. <br>
- `IMAGE_RES_GRPACC` <br>
  - Accuracy upgrade. <br>
- `IMAGE_RES_GRPDAM` <br>
  - Damage upgrade <br>

***

## 3D Models <br>

You can use any pie file for `imdName`, here are the ones dedicated to it, as well as the ones used in `research.json`. <br>
If your research gives a component or structure, use `statID` instead. <br>
If the research topic is blank in-game despite giving a component or structure, then use `imdName` instead. <br>

### `imdName` from researchimds folder <br>

- `dpvtol.pie` <br>
  - VTOL. Trivia: I have no idea why this exists, sense `statID` works fine, though that may not have always been the case. <br>
- `icamrhot.pie` <br>
  - Thermal Armour. <br>
- `icamrknt.pie` <br>
  - Kinetic Armour. Trivia: Alloy research now includes kinetic armor, however, it used to be it's own research that used this model. <br>
- `iccccons.pie` <br>
  - NEXUS/Reed-Tech/High-Tech/Future-Tech/Misc. <br>
- `iccybmg.pie` <br>
  - Cyborg Machinegun. Trivia: A research topic for unlocking Cyborg research used to use this. <br>
- `iceng.pie` <br>
  - Engine. <br>
- `icmolql.pie` <br>
  - Materials/Alloys/Misc. <br>
- `icmslcd.pie` <br>
  - Missile Codes/Misc. <br>
- `icspaner.pie` <br>
  - Spanner/Wrench. Trivia: It used to be used for auto-repair. <br>

### `imdName` from others found in `research.json` <br>

- `blwallh.pie` <br>
  - Hardcrete Wall. <br>
- `blfact1.pie` <br>
  - Factory. <br>
- `blpower4.pie` <br>
  - Power Generator. <br>
- `blresch4.pie` <br>
  - Research Facility. <br>
- `trlcon.pie` <br>
  - Truck/Spade <br>
- `gnlsnsr1.pie` <br>
  - Sensor Turret. <br>
- `trlvtlhe.pie` <br>
  - Cluster Bomb Bay. <br>
- `trmvtlhe.pie` <br>
  - HEAP Bomb Bay. <br>
- `trlvtlin.pie` <br>
  - Phosphor Bomb Bay. <br>
- `trmvtlin.pie` <br>
  - Thermite Bomb Bay. <br>
- `micapsul.pie` <br>
  - Artifact/Misc <br>
