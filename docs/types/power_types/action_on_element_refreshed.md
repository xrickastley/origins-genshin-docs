---
title: Action on Element Refreshed (Power Type)
---

# Action on Element Refreshed

[Power Type](../power_types.md)

Executes an [Entity Action Type](../entity_action_types.md) when an entity's Elemental Application is refreshed.

An element is "refreshed" when its Elemental Application is replaced with another Elemental Application of the same element entirely.

It is recommended to use [Action on Element Reapplied (Power Type)](./action_on_element_reapplied.md) over this power type for *most* use cases.

Type IDs: `seven-elements:action_on_element_refreshed`, `origins-genshin:action_on_element_refreshed`

!!! warning
	This power type will only exist if [Seven Elements](https://modrinth.com/mod/seven-elements) is installed.

!!! warning
	This power type will only trigger on **living** entities.

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