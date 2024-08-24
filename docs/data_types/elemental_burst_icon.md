# Elemental Burst Icon

[Data Type](../types/data_types.md)

An [Object](<https://origins.readthedocs.io/en/latest/types/data_types/object/>) used to specify an icon for an [Elemental Burst](./elemental_burst.md).

## Fields
| Field   | Type | Default    | Description |
|---------|------|------------|-------------|
|`icon`           |[Identifier](<https://origins.readthedocs.io/en/latest/types/data_types/identifier/>)| |The path to the file that contains the Elemental Burst icon.
|`cooldown`       |[Identifier](<https://origins.readthedocs.io/en/latest/types/data_types/identifier/>)|*optional*|The namespace and ID of a power that uses the [Resource (Power Type)](https://origins.readthedocs.io/en/latest/types/power_types/resource/) or a power type that has a built-in cooldown. When specified, uses values from this power to render the cooldown instead of the cooldown provided in the original power.|
|`reverse`        |[Boolean](https://origins.readthedocs.io/en/latest/types/data_types/boolean/)|`false`|Whether or not the cooldown value should be reversed. Origin powers have their cooldown go from `0` to `max`, so the cooldown will be rendered accordingly. If you use a custom cooldown that goes the opposite way (`max` to `0`), then set this to `true`.|
|`energy_resource`       |[Identifier](<https://origins.readthedocs.io/en/latest/types/data_types/identifier/>)|*optional*|The namespace and ID of a power that uses the [Resource (Power Type)](https://origins.readthedocs.io/en/latest/types/power_types/resource/) or a power type that has a built-in cooldown. When specified, this power is used as the value for the Elemental Burst's Energy.|
|`color`          |[Color](./color.md)|`{ "hex": "#ffffff00" }`|The color of the Elemental Burst's Energy.|
|`outline_color`  |[Color](./color.md)|`{ "hex": "#ffffff00" }`|The outline color of the Elemental Burst's Energy.|
|`new_max`        |[Integer](<https://origins.readthedocs.io/en/latest/types/data_types/integer/>)|`-1`|The new maximum value of `resource`. To accomodate for multiple powers using the same resource, this allows you to set the new `max` value of the `resource` to be used in rendering Energy. When set to `-1`, uses the default `max` value of `resource`.|
|`condition` |[Array](<https://origins.readthedocs.io/en/latest/types/data_types/array/>) of [Objects](<https://origins.readthedocs.io/en/latest/types/data_types/object/>)|*optional*|Each object has to have an `icon` [Identifier](<https://origins.readthedocs.io/en/latest/types/data_types/identifier/>) and a `condition` [Entity Condition Type](https://origins.readthedocs.io/en/latest/types/entity_condition_types/) object. The first icon with the condition on the list that holds true will be the icon used for the Elemental Burst. If no such icon exists, renders no Elemental Burst. |
|`disable_condition` |[Entity Condition Type](https://origins.readthedocs.io/en/latest/types/entity_condition_types/)|*optional*|If specified, the Elemental Burst will appear "disabled" when this provided condition holds true. This condition will **not** override the `"disable_condition"` field found in [Elemental Burst](./elemental_burst.md), but instead will be joined with the other condition using an or.|

## Examples
```json
{
	"icon": "origins-genshin:skills/elemental_burst_enhanced.png",
	"condition": {
		"type": "origins:resource",
		"resource": "origins:my_example_resource",
		"comparison": ">",
		"compare_to": 6
	}
}
```
This is an example of an Elemental Skill Icon using the `origins-genshin:skills/elemental_burst_enhanced.png` texture that is only shown when the player's `origins:my_example_resource` value is greater than `6`.

## Images
![Elemental Burst](../img/elemental_burst.png)

*Anatomy of an Elemental Burst Icon.*