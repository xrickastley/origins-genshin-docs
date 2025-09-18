---
title: Action on Element Refreshed (Power Type)
---

# Action on Element Refreshed

[Power Type](../power_types.md)

Executes an [Entity Action Type](../entity_action_types.md) when an entity's Elemental Application is refreshed.

Type ID: `origin-genshin:action_on_element_refreshed`

!!! warning
	This action type will only trigger on **living** entities.

### Fields
| Field				| Type | Default | Description
|-------------------|------|---------|------------
|`elements`			| [Element](../data_types/element.md) or Array of [Element](../data_types/element.md) | | The elements to check for. |
|`entity_action`	| [Entity Action Type](../entity_action_types.md) | | The action to be executed when the specified `elements` are refreshed. |

### Examples
```json
{
	"type": "origins-genshin:action_on_element_refreshed",
	"elements": "PYRO",
	"entity_action": {
		"type": "origins:set_on_fire",
		"duration": 3,
	}
}
```
This example will set the entity on fire when their <span class="pyro">**Pyro**</span> aura is refreshed.