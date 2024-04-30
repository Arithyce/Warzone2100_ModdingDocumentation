  
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

### Modules <br>

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
The following will be appended to key names to denote there value type: <br>
Quotes are included, `compare: "old:new"`, `string: "value"`, `integer: whole number`, `float: decimal`. <br>
`double: whole/decimal`, `boolean: false/true`, `varies: depends on parent`, `null: no value`, `integer boolean: 0=false/1=true`. <br>
For keys that accept boolean or integer boolean, removing the key is equivalent to false. <br>

**Note that although the game accepts the double and float data types, the game rounds these up to a whole number.** <br>
**Keys here are in the order commonly found in `research.json`, however, they can be in any order.** <br>
- `disabledWhen` `Integer` <br>
  - `1`: Tanks, unused, `2`: Cyborgs, `4`: VTOLs, `8`: Satellite Uplink Center, `16`: Laser Satellite Command Post. <br>
- `iconID` `String` <br>
  - Icon shown on topic, find ==iconID== below for a list. <br>
- `id`* `String` <br>
  - Needs to be the same as the JS object name, and it needs to be unique. <br>
- `msgName` `Ssring` <br>
  - Message ID of the message inside the Intelligence Display, see "`mp/messages`", Mutual Exclusion: `techCode`. <br>
- `keyTopic` `Integer Boolean` <br>
  - Unused in multiplayer/skirmish. See the campaign documentation for it's use in campaign. <br>
- `imdName` `String` <br>
  - File name for the 3D model to be displayed in the topic, find ===3D Models=== below for a list, Mutual Exclusion: `statID`. <br>
- `name`* `String` <br>
  - Display name. <br>
- `replacedComponents` `String Compare` <br>
  - Components to be replaced. `OldItem:NewItem`. The values must be in an array. <br>
- `redComponents` `String Array` <br>
  - Components to be made redundant without replacing. The values must be in an array. <br>
- `requiredResearch` `String Array` <br>
  - Research IDs of required research. The values must be in an array. <br>
- `researchPoints` `Double` <br>
  - How many research points it takes to research, max is 65535 (16-bit). <br>
- `researchPower` `Double` <br>
  - How much power it takes to research, max is 65535 (16-bit). <br>
- `resultStructures` `String Array` <br>
  - Structures to be made available. The values must be in an array. <br>
- `resultComponents` `String` <br>
  - Components to be made available.  The values must be in an array. <br>
- `results` `Null` <br>
  - Upgrades to be given, details follow. <br>
  - `class`* `String` <br>
    - See temp for a list of accepted values, each header is an accepted value. <br>
  - `filterParameter` `String` <br>
    - The stat parameter to filter for, find ==Filter Parameters== below for a list of useful ones. <br>
  - `filterValue` `Varies` <br>
    - The stat value to filter for, find ===List of weapon classes=== below for a list of weapon classes. <br>
  - `parameter`* `String` <br>
    - The parameter to be modified. <br>
  - `value`* `Varies` <br>
    - The amount the parameter is modified by, can sometimes be negative. <br>
- `statID` `String` <br>
  - The 3D component to be displayed in the topic, Mutual Exclusion: `imdName`. <br>
- `subgroupIconID` `String` <br>
  - Icon shown on the topic, find ==subgroupIconID== below for a list. <br>
- `techCode`** `Integer Boolean` <br>
  - No Intelligence Display entry, mandatory if `msgName` is not provided, Mutual Exclusion: `msgName`. <br>
[Key Names](#key-names-from-researchjson-)
***
