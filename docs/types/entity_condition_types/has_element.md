---
title: Has Element (Entity Condition Type)
---

# Has Element

[Entity Condition Type](../entity_condition_types.md)

Checks if the entity has the specified [Element](../data_types/element.md).

Type IDs: `seven-elements:has_element`, `origins-genshin:has_element`

### Fields

| Field				| Type | Default | Description
|-------------------|------|---------|------------
|`elements`			| [Element](../data_types/element.md) or Array of [Element](../data_types/element.md) | | The element to check for. |

### Examples

```json
"entity_condition": {
	"type": "seven-elements:has_element",
	"element": "HYDRO"
}
```

This example checks if the entity has the <span class="hydro">**Hydro**</span> element.

```json
"entity_condition": {
	"type": "seven-elements:has_element",
	"element": [
		"PYRO",
		"CRYO"
	]
}
```

This example checks if the entity has either the <span class="pyro">**Pyro**</span> or <span class="cryo">**Cryo**</span> element.