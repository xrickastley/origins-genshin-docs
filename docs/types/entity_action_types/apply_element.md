---
title: Apply Element (Bi-entity Action Type)
---

# Apply Element

[Entity Action Type](../entity_action_types.md)

Applies an element to this entity.

Type IDs: `seven-elements:apply_element`, `origins-genshin:apply_element`

### Fields

| Field  | Type | Default | Description   |
| -------|------|---------|---------------|
|`element`			| [Elemental Application](../data_types/elemental_application.md) | | The elemental application to apply to the entity. |
|`internal_cooldown`| [Internal Cooldown](../data_types/internal_cooldown.md) | | The internal cooldown attributed to the elemental application. |

### Examples

```json
"entity_action": {
    "type": "seven-elements:apply_element",
	"element": {
		"element": "HYDRO",
		"gauge_units": 2.0
	},
	"internal_cooldown": {
		"tag": "origins-genshin:self_application"
	}
}
```

This example will apply 2 [gauge units ↗](https://xrickastley.github.io/SevenElements/wiki/guide/elements/elemental_gauge_theory) of <span class="pyro">**Pyro**</span>, so long as the [Internal Cooldown ↗](https://xrickastley.github.io/SevenElements/wiki/guide/elements/internal_cooldown) with the tag: `origins-genshin:self_application` and type: `seven-elements:default` is inactive.