# Charge Render

[Data Type](../types/data_types.md)

An [Object](<https://origins.readthedocs.io/en/latest/types/data_types/object/>) used to define how "Charges" for an [Elemental Skill](./elemental_skill.md) should be rendered.

## Fields
| Field   | Type | Default    | Description |
|---------|------|------------|-------------|
|`type`       |[Charge Render Method](./charge_render_method.md)|`"SPLIT"`|The method to use for rendering charges. |
|`conditions` |[Array](<https://origins.readthedocs.io/en/latest/types/data_types/array/>) of [Objects](<https://origins.readthedocs.io/en/latest/types/data_types/object/>)|*optional*|Optional if the `type` field has it's [Charge Render Method](./charge_render_method.md) as `"SPLIT"`. Each object has to have a `charge` [Integer](<https://origins.readthedocs.io/en/latest/types/data_types/integer/>) and a `condition` [Entity Condition Type](https://origins.readthedocs.io/en/latest/types/entity_condition_types/) object. The first `charge` value with the condition on the list that holds true will be the value for the current amount of charges the [Elemental Skill](./elemental_skill.md) has. If no such value exists, defaults to `0`.|


## Examples
```json
{
	"icon": "origins-genshin:skills/elemental_skill.png",
	"resource": "origins-genshin:my_awesome_resource",
	"charges": 2,
	"charge_render": {
		"type": "SPLIT"
	}
}
```
The example above will render an Elemental Skill Icon with the `origins-genshin:skills/elemental_skill.png` icon. It will have `2` charges using an even split from `origins-genshin:my_awesome_resource`. This means that if `origins-genshin:my_awesome_resource` has a maximum value of `50`, then each charge will take `25`.

If `origins-genshin:my_awesome_resource` has a current value of `30`, then a single "usable" charge is rendered, with the last charge having a cooldown of `20` or 1 second. 

If `origins-genshin:my_awesome_resource` has a current value of `20`, then no "usable" charges are rendered, with the first charge having a cooldown of `5` or 0.25 seconds.