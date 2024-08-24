# Elemental Skill

[Data Type](../types/data_types.md)

An [Object](<https://origins.readthedocs.io/en/latest/types/data_types/object/>) used to specify an "Elemental Skill" for a power under the [Active Self](../power_types/active_self.md) power type.

## Fields
| Field   | Type | Default    | Description |
|---------|------|------------|-------------|
|`show_cooldown`    |[Boolean](https://origins.readthedocs.io/en/latest/types/data_types/boolean/)|`false`|Whether or not the Elemental Skill's cooldown is rendered. Changing this will only affect the timer text.|
|`should_render`    |[Boolean](https://origins.readthedocs.io/en/latest/types/data_types/boolean/)|`false`|Whether or not the Elemental Skill icon is rendered. This includes the icon, cooldown effect, and the cooldown text, and will override the selection made in `show_cooldown` if set to `false`.|
|`disable_condition` |[Entity Condition Type](https://origins.readthedocs.io/en/latest/types/entity_condition_types/)|*optional*|If specified, the Elemental Skill will appear "disabled" when the provided condition holds true.|
|`icon_conditions`   |[Array](<https://origins.readthedocs.io/en/latest/types/data_types/array/>) of [Elemental Skill Icons](./elemental_skill_icon.md)| |An [Array](<https://origins.readthedocs.io/en/latest/types/data_types/array/>) of [Elemental Skill Icons](./elemental_skill_icon.md) that determines the Elemental Skill icon to be rendered. The first icon with the condition on the list that holds true will be the icon used for the Elemental Skill. If no such icon exists, renders no Elemental Skill. |

## Examples
```json
{
	"type": "origins:active_self",
	
	// ...

	"elemental_skill": {
		"show_cooldown": true,
		"should_render": true,
		"icon_condition": [
			// ...
		]
	}
}
```