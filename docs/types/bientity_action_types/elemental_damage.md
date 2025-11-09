---
title: Elemental Damage (Bi-entity Action Type)
---

# Elemental Damage

[Bi-entity Action Type](../bientity_action_types.md)

Applies elemental damage to the target entity as if the actor entity has attacked it.

Type IDs: `seven-elements:elemental_damage`, `origins-genshin:elemental_damage`

!!! info
	The max health of the target entity will be used as the base value for the modifier(s).

!!! info
	See [Minecraft Wiki: Damage type](https://minecraft.wiki/w/Damage_type) and [Minecraft Wiki: Damage type tag (Java Edition)](https://minecraft.wiki/w/Damage_type_tag_(Java_Edition)) for more information about vanilla damage types and damage type tags.

### Fields

| Field				| Type | Default | Description
|-------------------|------|---------|------------
|`amount`			| [Float](https://origins.readthedocs.io/en/latest/types/data_types/float) | | The amount of damage to deal.
|`source`			| [Damage Source](https://origins.readthedocs.io/en/latest/types/data_types/damage_source) | <span style="color:darkred"><b>DEPRECATED</b></span> | Use `damage_type` instead. See [Damage Source (Data Type)](https://origins.readthedocs.io/en/latest/types/data_types/damage_source) for more details.
|`damage_type`		| [Identifier](https://origins.readthedocs.io/en/latest/types/data_types/identifier) | | Defines the properties of the damage source that will be dealt, such as part of its death message, and whether it can bypass armor, shield, etc. (via damage type tags.)
|`modifier`			| [Attribute Modifier](https://origins.readthedocs.io/en/latest/types/data_types/attribute_modifier) | _optional_ | If specified, this modifier will be applied to the damage taken by the '**target**' entity.
|`modifiers`		| [Array](https://origins.readthedocs.io/en/latest/types/data_types/array) of [Attribute Modifiers](https://origins.readthedocs.io/en/latest/types/data_types/attribute_modifier) | _optional_ | If specified, these modifiers will be applied to the damage taken by the '**target**' entity.
|`element`			| [Elemental Application](../data_types/elemental_application.md) | | The elemental application to apply to the target. |
|`internal_cooldown`| [Internal Cooldown](../data_types/internal_cooldown.md) | | The internal cooldown attributed to the elemental application. |

### Examples

```json
"bientity_action": {
	"type": "seven-elements:elemental_damage",
	"amount": 10,
	"damage_type": "minecraft:cramming",
	"element": {
		"element": "PYRO",
		"gauge_units": 1.0
	},
	"internal_cooldown": {
		"tag": "origins-genshin:crammed"
	}
}
```

This example will deal 5 hearts of `cramming` damage to the target as if the actor has hit them, and that, if killed, will display a *"`<targetName>` was squashed by `<actorName>`",* where `<targetName>` is the name of the target and `<actorName>` is the name of the actor.

This also applies 1 [gauge unit ↗](https://xrickastley.github.io/SevenElements/wiki/guide/elements/elemental_gauge_theory) of <span class="pyro">**Pyro**</span> to the target, so long as the [Internal Cooldown ↗](https://xrickastley.github.io/SevenElements/wiki/guide/elements/internal_cooldown) with the tag: `origins-genshin:crammed` and type: `seven-elements:default` is inactive.

<br>

```json
"bientity_action": {
	"type": "origins:damage",
	"damage_type": "minecraft:generic",
	"modifier": {
		"operation": "multiply_total_multiplicative",
		"value": -0.75
	},
	"element": {
		"element": "HYDRO",
		"gauge_units": 2.0
	},
	"internal_cooldown": {
		"tag": "origins-genshin:execute"
	}
}
```

This example will deal 25% `generic` damage to the target entity. If the max health of the target entity is 20, this will deal 5 (2 and a half hearts of) `generic` damage (`20 * 0.25 = 5`.)

This also applies 2 [gauge units ↗](https://xrickastley.github.io/SevenElements/wiki/guide/elements/elemental_gauge_theory) of <span class="hydro">**Hydro**</span> to the target, so long as the [Internal Cooldown ↗](https://xrickastley.github.io/SevenElements/wiki/guide/elements/internal_cooldown) with the tag: `origins-genshin:execute` and type: `seven-elements:default` is inactive.

<br>

```json
"bientity_action": {
	"type": "origins:damage",
	"damage_type": "minecraft:magic",
	"modifier": {
		"operation": "set_total",
		"resource": "example:magic_damage",
		"value": 0
	},
	"element": {
		"element": "CRYO",
		"gauge_units": 2.0
	},
	"internal_cooldown": {
		"tag": "origins-genshin:magical_hit",
		"type": "seven-elements:none"
	}
}
```

This example will deal `minecraft:magic` damage to the target entity, with its damage value depending on the value of the `example:magic_damage` (`data/example/powers/magic_damage.json`) power from the actor entity.

This also *always* applies 2 [gauge units ↗](https://xrickastley.github.io/SevenElements/wiki/guide/elements/elemental_gauge_theory) of <span class="hydro">**Hydro**</span> to the target as the [Internal Cooldown ↗](https://xrickastley.github.io/SevenElements/wiki/guide/elements/internal_cooldown)'s type: `seven-elements:none` is always inactive.