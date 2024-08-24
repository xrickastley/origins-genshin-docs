# Elemental Burst

[Data Type](../types/data_types.md)

An [Object](<https://origins.readthedocs.io/en/latest/types/data_types/object/>) used to specify an "Elemental Burst" for a power under the [Active Self](../power_types/active_self.md) power type.

## Fields
| Field   | Type | Default    | Description |
|---------|------|------------|-------------|
|`show_cooldown`     |[Boolean](https://origins.readthedocs.io/en/latest/types/data_types/boolean/)|`false`|Whether or not the Elemental Burst's cooldown is rendered. Changing this will only affect the cooldown text.|
|`should_render`     |[Boolean](https://origins.readthedocs.io/en/latest/types/data_types/boolean/)|`false`|Whether or not the Elemental Burst is rendered. This includes the icon, cooldown effect, and the cooldown text, and will override the selection made in `show_cooldown` if set to `false`.|
|`disable_condition` |[Entity Condition Type](https://origins.readthedocs.io/en/latest/types/entity_condition_types/)|*optional*|If specified, the Elemental Burst will appear "disabled" when the provided condition holds true.|
|`icon_conditions`   |[Array](<https://origins.readthedocs.io/en/latest/types/data_types/array/>) of [Elemental Burst Icons](./elemental_burst_icon.md)| |An [Array](<https://origins.readthedocs.io/en/latest/types/data_types/array/>) of [Elemental Burst Icons](./elemental_burst_icon.md) that determines the Elemental Burst icon to be rendered. The first icon with the condition on the list that holds true will be the icon used for the Elemental Burst. If no such icon exists, renders no Elemental Burst. |

## Examples
```json
{
	"type": "origins:active_self",
	
	// ...

	"elemental_burst": {
		"show_cooldown": true,
		"should_render": true,
		"default_icon": "origins-genshin:skills/elemental_burst.png",
		"icon_condition": [
			// ...
		]
	}
}
```