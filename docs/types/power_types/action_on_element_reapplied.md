---
title: Action on Element Reapplied (Power Type)
---

# Action on Element Reapplied

[Power Type](../power_types.md)

Executes an [Entity Action Type](../entity_action_types.md) when an entity's Elemental Application is reapplied.

An element is "reapplied" when the [gauge units ↗](https://xrickastley.github.io/SevenElements/wiki/guide/elements/elemental_gauge_theory) of its Elemental Application are changed. 

In [Elemental Gauge Theory ↗](https://xrickastley.github.io/SevenElements/wiki/guide/elements/elemental_gauge_theory) terms, the Elemental Application is *refreshed*, i.e. another Elemental Application of the same element is applied to the entity that already has an existing Elemental Application of the element in question.

Type IDs: `seven-elements:action_on_element_reapplied`, `origins-genshin:action_on_element_reapplied`

!!! warning
	This power type will only exist if [Seven Elements](https://modrinth.com/mod/seven-elements) is installed.

!!! warning
	This power type will only trigger on **living** entities.

### Fields
| Field				| Type | Default | Description
|-------------------|------|---------|------------
|`elements`			| [Element](../data_types/element.md) or Array of [Element](../data_types/element.md) | | The elements to check for. |
|`entity_action`	| [Entity Action Type](../entity_action_types.md) | | The action to be executed when the specified `elements` are reapplied. |

### Examples
```json
{
	"type": "origins-genshin:action_on_element_reapplied",
	"elements": "PYRO",
	"entity_action": {
		"type": "origins:set_on_fire",
		"duration": 3,
	}
}
```
This example will set the entity on fire when their <span class="pyro">**Pyro**</span> aura is reapplied.