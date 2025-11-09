---
title: Elemental Damage (Entity Action Type)
---

# Damage

[Entity Action Type](../entity_action_types.md)

Applies damage to an entity.

Type IDs: `seven-elements:elemental_damage`, `origins-genshin:elemental_damage`

!!! info
    The max health of the entity will be used as the base value for the modifier(s).

!!! info
    See [Minecraft Wiki: Damage type](https://minecraft.wiki/w/Damage_type) and [Minecraft Wiki: Damage type tag (Java Edition)](https://minecraft.wiki/w/Damage_type_tag_(Java_Edition)) for more information about vanilla damage types and damage type tags.

### Fields

| Field  | Type | Default | Description
| -------|------|---------|-------------
| `amount` | [Float](https://origins.readthedocs.io/en/latest/types/data_types/float.md) |  | The amount of damage to deal.
| `source` | [Damage Source](https://origins.readthedocs.io/en/latest/types/data_types/damage_source.md) | <span style="color:darkred"><b>DEPRECATED</b></span> | Use `damage_type` instead. See [Damage Source (Data Type)](https://origins.readthedocs.io/en/latest/types/data_types/damage_source.md) for more details.
| `damage_type` | [Identifier](https://origins.readthedocs.io/en/latest/types/data_types/identifier.md) | | Defines the properties of the damage source that will be dealt, such as part of its death message, and whether it can bypass armor, shield, etc. (via damage type tags.)
| `modifier` | [Attribute Modifier](https://origins.readthedocs.io/en/latest/types/data_types/attribute_modifier.md) | _optional_ | If specified, this modifier will be applied to the damage taken by the entity.
| `modifiers` | [Array](https://origins.readthedocs.io/en/latest/types/data_types/array.md) of [Attribute Modifiers](https://origins.readthedocs.io/en/latest/types/data_types/attribute_modifier.md) | _optional_ | If specified, these modifiers will be applied to the damage taken by the entity.
|`element`			| [Elemental Application](../data_types/elemental_application.md) | | The elemental application to apply to the entity. |
|`internal_cooldown`| [Internal Cooldown](../data_types/internal_cooldown.md) | | The internal cooldown attributed to the elemental application. |

### Examples

```json
"entity_action": {
    "type": "seven-elements:elemental_damage",
    "amount": 4,
    "damage_type": "minecraft:on_fire",
	"element": {
		"element": "PYRO",
		"gauge_units": 1.0
	},
	"internal_cooldown": {
		"tag": "origins-genshin:fire_ability"
	}
}
```

This example will deal 2 hearts of `on_fire` damage, which by its tags in vanilla is considered fire damage and bypasses armor.

This also applies 1 [gauge unit ↗](https://xrickastley.github.io/SevenElements/wiki/guide/elements/elemental_gauge_theory) of <span class="pyro">**Pyro**</span>, so long as the [Internal Cooldown ↗](https://xrickastley.github.io/SevenElements/wiki/guide/elements/internal_cooldown) with the tag: `origins-genshin:fire_ability` and type: `seven-elements:default` is inactive.