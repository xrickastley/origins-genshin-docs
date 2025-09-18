---
title: Element (Damage Condition Type)
---

# Element

[Damage Condition Type](../damage_condition_types.md)

Checks if the provided `DamageSource` has the specified [Element](../data_types/element.md).

Type ID: `origins-genshin:element`

### Fields

| Field				| Type | Default | Description
|-------------------|------|---------|------------
|`elements`			| [Element](../data_types/element.md) or Array of [Element](../data_types/element.md) | | The element to check for. |

### Examples

```json
"damage_condition": {
	"type": "origins-genshin:element",
	"element": "HYDRO"
}
```

This example checks if the damage is of the <span class="hydro">**Hydro**</span> element.

```json
"damage_condition": {
	"type": "origins-genshin:element",
	"element": [
		"PYRO",
		"CRYO"
	]
}
```

This example checks if the damage is of the <span class="pyro">**Pyro**</span> or <span class="cryo">**Cryo**</span> element.