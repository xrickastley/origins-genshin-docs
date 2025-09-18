---
title: Action on Elemental Reaction (Power Type)
---

# Action on Elemental Reaction

[Power Type](../power_types.md)

Executes an [Entity Action Type](../entity_action_types.md) or [Bi-entity Action Type](../bientity_action_types.md) when an Elemental Reaction is triggered on the entity.

Type ID: `origin-genshin:action_on_elemental_reaction`

!!! warning
	This action type will only trigger on **living** entities.

### Fields
| Field				| Type | Default | Description
|-------------------|------|---------|------------
|`reactions`		| [Identifier](https://origins.readthedocs.io/en/latest/types/data_types/identifier/) or Array of [Identifier](https://origins.readthedocs.io/en/latest/types/data_types/identifier/) | | The Elemental Reactions to check for. |
|`entity_action`	| [Entity Action Type](../entity_action_types.md) | | The action to be executed when the specified `reactions` are triggered. <br> <br> This is only executed if there is no entity that triggered the reaction (i.e. triggered by the environment), unless `always_trigger` is `true`. |
|`bientity_action`	| [Bi-entity Action Type](../bientity_action_types.md) | | The action to be executed when the specified `reactions` are triggered. <br> <br> The **actor**  is this entity, the entity the reaction was triggered on, while the **target** is the entity triggering the reaction. <br> <br> This is only executed if there is an entity that triggered the reaction.  |
|`always_trigger`	| [Boolean](https://origins.readthedocs.io/en/latest/types/data_types/boolean/) | | Whether the `entity_action` should be executed regardless. |

### Examples
```json
{
	"type": "origins-genshin:action_on_elemental_reaction",
	"reactions": "origins-genshin:overloaded",
	"bientity_action": {
		"type": "origins:heal",
		"duration": 3,
	},
	"bientity_action": {
		"type": "origins-genshin:elemental_damage",
		"amount": 10,
		"damage_type": "minecraft:player_attack",
		"element": {
			"element": "CRYO",
			"gauge_units": 2.0
		},
		"internal_cooldown": {
			"tag": "origins-genshin:overloaded_counter",
			"type": "origins-genshin:none"
		}
	},
	"always_trigger": true
}
```
This example will heal the entity for 1.5 hearts every time the <span style="color: #fc7fa4">**Overloaded**</span> reaction is triggered on them.

If <span style="color: #fc7fa4">**Overloaded**</span> was triggered by another entity, a "counter" is done on them, dealing <span class="cryo">**10 Cryo DMG**</span> and applies 2 [gauge units](../../elements/elements.md#elemental-gauge-theory) of <span class="cryo">**Cryo**</span> to them.