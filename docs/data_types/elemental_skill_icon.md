# Elemental Skill Icon

[Data Type](../types/data_types.md)

An [Object](<https://origins.readthedocs.io/en/latest/types/data_types/object/>) used to specify an icon for an [Elemental Skill](./elemental_skill.md).

## Fields
| Field   | Type | Default    | Description |
|---------|------|------------|-------------|
|`icon`          |[Identifier](<https://origins.readthedocs.io/en/latest/types/data_types/identifier/>)| |The path to the file that contains the Elemental Skill icon.
|`cooldown`      |[Identifier](<https://origins.readthedocs.io/en/latest/types/data_types/identifier/>)|*optional*|The namespace and ID of a power that uses the [Resource (Power Type)](https://origins.readthedocs.io/en/latest/types/power_types/resource/) or a power type that has a built-in cooldown. When specified, uses values from this power to render the cooldown instead of the cooldown provided in the original power.|
|`reverse`       |[Boolean](https://origins.readthedocs.io/en/latest/types/data_types/boolean/)|`false`|Whether or not the cooldown value should be reversed. Origin powers have their cooldown go from `0` to `max`, so the cooldown will be rendered accordingly. If you use a custom cooldown that goes the opposite way (`max` to `0`), then set this to `true`.|
|`charges`       |[Integer](<https://origins.readthedocs.io/en/latest/types/data_types/integer/>)|`1`|The amount of charges this skill has. Maximum of `3`. Charges only start being rendered at `2`. Specifying `1` will not render any sort of charges on the skill. |
|`charge_render` |[Charge Render](./charge_render.md)|*optional*|Determines how the charges of this Elemental Skill are visualized.|
|`condition`     |[Array](<https://origins.readthedocs.io/en/latest/types/data_types/array/>) of [Objects](<https://origins.readthedocs.io/en/latest/types/data_types/object/>)|*optional*|Each object has to have an `icon` [Identifier](<https://origins.readthedocs.io/en/latest/types/data_types/identifier/>) and a `condition` [Entity Condition Type](https://origins.readthedocs.io/en/latest/types/entity_condition_types/) object. The first icon with the condition on the list that holds true will be the icon used for the Elemental Skill. If no such icon exists, renders no Elemental Skill. |
|`disable_condition` |[Entity Condition Type](https://origins.readthedocs.io/en/latest/types/entity_condition_types/)|*optional*|If specified, the Elemental Skill will appear "disabled" when this provided condition holds true. This condition will **not** override the `"disable_condition"` field found in [Elemental Skill](./elemental_skill.md), but instead will be joined with the other condition using an or.|`

## Examples
```json
{
	"icon": "origins-genshin:skills/elemental_skill_enhanced.png",
	"condition": {
		"type": "origins:sneaking"
	}
}
```
This is an example of an Elemental Skill Icon using the `origins-genshin:skills/elemental_skill_enhanced.png` texture that is only shown when the player is sneaking.

## Images
![Elemental Skill](../img/elemental_skill.png)

*Anatomy of an Elemental Skill Icon.*


![Elemental Skill with Charges](../img/elemental_skill_charges.png)

*Anatomy of an Elemental Skill Icon using the Charge Render.*