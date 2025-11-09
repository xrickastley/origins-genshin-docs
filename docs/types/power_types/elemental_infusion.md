---
title: Elemental Infusion (Power Type)
---

# Elemental Infusion

[Power Type](../power_types.md)

Creates an Elemental Infusion on the entity, infusing each attack from them with the specified Elemental Application.

Type IDs: `seven-elements:elemental_infusion`, `origins-genshin:elemental_infusion`

!!! warning
	This power type will only exist if [Seven Elements](https://modrinth.com/mod/seven-elements) is installed.

### Fields
| Field				| Type | Default | Description
|-------------------|------|---------|------------
|`element`			| [Elemental Application](../data_types/elemental_application.md) | | The elemental application to apply to the target per attack. |
|`internal_cooldown`| [Internal Cooldown](../data_types/internal_cooldown.md) | | The internal cooldown attributed to the elemental application. |
|`priority`			| [Integer](https://origins.readthedocs.io/en/latest/types/data_types/integer/) | | The priority of this Elemental Infusion over the others. |

### Examples

```json
{
	"type": "seven-elements:elemental_infusion",
	"element": {
		"type": "gauge_unit",
		"element": "hydro",
		"gauge_units": 1.0
	},
	"internal_cooldown": {
		"tag": "origins-genshin:normal_attack",
		"type": "seven-elements:default"
	},
	"priority": 1
}
```
This example will give the entity infinite <span class="hydro">**Hydro**</span> infusion.

Note that due to the [Internal Cooldown ↗](https://xrickastley.github.io/SevenElements/wiki/guide/elements/internal_cooldown), the <span class="hydro">**Hydro**</span> element isn't always applied per hit of the entity. However, the damage will still be <span class="hydro">**Hydro DMG**</span>.