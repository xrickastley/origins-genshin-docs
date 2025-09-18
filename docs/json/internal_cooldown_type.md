# Internal Cooldown Type JSON Format

This is the format of a JSON file describing an **Internal Cooldown Type**. An **Internal Cooldown Type** handles the rate at which Elements can be applied.

!!! tip
	Before you create one, consider trying `origins-genshin:default` for your use case. After all, elements should be applied strategically, not "spammingly".

Internal Cooldown Type JSON files need to be placed inside the `data/<namespace>/internal_cooldowns` folder of your datapack. The said files can be referenced as `namespace:path/to/internal_cooldown_type` (`data/namespace/internal_cooldowns/path/to/internal_cooldown_type.json`).

### Default Values

- `origins-genshin:default` (2.5s/3 hits)
- `origins-genshin:none` (0s/0 hits)

### Fields
| Field				| Type | Default    | Description |
|-------------------|------|------------|-------------|
|`gauge_sequence`	|[Integer](<https://origins.readthedocs.io/en/latest/types/data_types/integer/>)| | The amount of hits needed before an Element can be applied **within** the reset interval's timer. |
|`reset_interval`	|[Integer](<https://origins.readthedocs.io/en/latest/types/data_types/integer/>)| | The amount of time in ticks before an Element can be applied again. |

### Examples

```json
{
	"gauge_sequence": 3,
	"reset_interval": 50
}
```
This example creates an Internal Cooldown Type with a `gauge_sequence` of `3` hits and a `reset_interval` of `50` ticks.