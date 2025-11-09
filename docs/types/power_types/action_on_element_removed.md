---
title: Action on Element Removed (Power Type)
---

# Action on Element Removed

[Power Type](../power_types.md)

Executes an [Entity Action Type](../entity_action_types.md) when an element is removed from the entity.

Type ID: `origins:action_on_element_removed`

!!! warning
	This action type is not intended to be with the Origins/Apoli namespace, and is fixed on **Origins: Genshin v3.0.0**

!!! warning
	This action type will only trigger on **living** entities.

### Fields
| Field				| Type | Default | Description
|-------------------|------|---------|------------
|`elements`			| [Element](../data_types/element.md) or Array of [Element](../data_types/element.md) | | The elements to check for. |
|`entity_action`	| [Entity Action Type](../entity_action_types.md) | | The action to be executed when the specified `elements` are removed. |

### Examples
```json
{
	"type": "origins-genshin:action_on_element_removed",
	"elements": "CRYO",
	"entity_action": {
		"type": "origins:heal",
		"duration": 5,
	}
}
```
This example will heal the entity for 2.5 hearts when their <span class="cryo">**Cryo**</span> aura is removed.