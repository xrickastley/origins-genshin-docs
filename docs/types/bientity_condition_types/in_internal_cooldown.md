---
title: In Internal Cooldown (Bi-entity Condition Type)
---

# In Internal Cooldown

[Bi-entity Condition Type](../bientity_condition_types.md)

Checks whether the provided [Internal Cooldown](../data_types/internal_cooldown.md) for the provided [Element](../data_types/element.md) is active on the **target** for the **actor**. 

Type ID: `origins-genshin:in_internal_cooldown`

### Fields

| Field				| Type | Default | Description
|-------------------|------|---------|------------
|`element`			| [Element](../data_types/element.md) | | The element to use for the provided `internal_cooldown`. |
|`internal_cooldown`| [Internal Cooldown](../data_types/internal_cooldown.md) | | The internal cooldown to check. |

### Examples

```json
"bientity_action": {
	"element": "PYRO",
	"internal_cooldown": {
		"tag": "origins-genshin:elemental_burst",
		"type": "origins-genshin:default"
	}
}
```

This example checks if the [Internal Cooldown](../../elements/internal_cooldown.md) with the tag: `origins-genshin:elemental_burst` and type: `origins-genshin:default` is active for the target's <span class="pyro">**Pyro**</span> element.

Note that an **active** Internal Cooldown means the element may **not** be applied, while an **inactive** Internal Cooldown means the element may be applied.	