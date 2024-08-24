# Color

[Data Type](../types/data_types.md)

An [Object](<https://origins.readthedocs.io/en/latest/types/data_types/object/>) used to specify an "Elemental Burst" for a power under the [Active Self](../power_types/active_self.md) power type.

## Fields
| Field   | Type | Default    | Description |
|---------|------|------------|-------------|
|`default_icon`     |[Identifier](<https://origins.readthedocs.io/en/latest/types/data_types/identifier/>)| |The path to the file that contains the Elemental Burst icon.
|`show_cooldown`    |[Boolean](https://origins.readthedocs.io/en/latest/types/data_types/boolean/)|`false`|Whether or not the Elemental Burst's cooldown is rendered. Changing this will only affect the timer text.|
|`should_render`    |[Boolean](https://origins.readthedocs.io/en/latest/types/data_types/boolean/)|`false`|Whether or not the Elemental Burst is rendered. This includes the icon, cooldown effect, and the cooldown text, and will override the selection made in `show_cooldown`|
|`default_icon`     |[Identifier](<https://origins.readthedocs.io/en/latest/types/data_types/identifier/>)| |The path to the file that contains the Elemental Burst icon.
|`resource`   |[Identifier](<https://origins.readthedocs.io/en/latest/types/data_types/identifier/>)|*optional*|The namespace and ID of a power that uses the [Resource (Power Type)](https://origins.readthedocs.io/en/latest/types/power_types/resource/) or a power type that has a built-in cooldown. When specified, uses values from this power to render the cooldown instead of the cooldown provided in the original power.|
|`color`     |[Color](./color.md)|`{ "hex": "#ffffff00" }`|The path to the file that contains the Elemental Burst icon.|
|`icon_condition`   |[Array](<https://origins.readthedocs.io/en/latest/types/data_types/array/>) of [Objects](<https://origins.readthedocs.io/en/latest/types/data_types/object/>)|*optional*|Each object has to have an `icon` [Identifier](<https://origins.readthedocs.io/en/latest/types/data_types/identifier/>) and a `condition` [Entity Condition Type](https://origins.readthedocs.io/en/latest/types/entity_condition_types/) object. The first icon with the condition on the list that holds true will be the icon used for the Elemental Burst. If no such icon exists, resorts to `default_icon`. |