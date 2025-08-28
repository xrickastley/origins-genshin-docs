---
title: Action on Element Applied (Power Type)
---

# Action on Element Applied

[Power Type](../power_types.md)

Executes an [Entity Action Type](../entity_action_types.md) when an element is applied to the entity.

Type ID: `origin-genshin:action_on_element_applied`

!!! warning
	This action type will only trigger on **living** entities.

### Fields
| Field				| Type | Default | Description
|-------------------|------|---------|------------
|`elements`			| [Element](../data_types/element.md) or Array of [Element](../data_types/element.md) | | The elements to check for. |
|`entity_action`	| [Entity Action Type](../entity_action_types.md) | | The action to be executed when the specified `elements` are applied. |

### Examples
```json
{
	"type": "origins-genshin:action_on_element_applied",
	"elements": ["HYDRO", "ELECTRO"],
	"entity_action": {
		"type": "origins:explode",
		"power": 3,
		"destruction_type": "break",
		"damage_self": true,
		"create_fire": true
	}
}
```
This example will create an explosion upon being applied with either the <span class="hydro">**Hydro**</span> or <span class="electro">**Electro**</span> element.