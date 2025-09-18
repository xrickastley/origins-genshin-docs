# Elemental Application Type

[Data Type](../data_types.md)

A [String](<https://origins.readthedocs.io/en/latest/types/data_types/string/>) that represents an [Elemental Application](./elemental_application.md) Type.

## Values

| Value         | Description                                                  |
|---------------|--------------------------------------------------------------|
|`GAUGE_UNITS`	| Elemental Applications will have a specified amount of [gauge units](../../elements/elements.md#elemental-gauge-theory) that **decay** over time, removed when the gauge is depleted. |
|`DURATION`		| Elemental Applications will have a specified duration and an amount of [gauge units](../../elements/elements.md#elemental-gauge-theory), removed when the duration is over or when the gauge is depleted. |