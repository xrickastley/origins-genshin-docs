# Elemental Application

[Data Type](../data_types.md)

An [Object](<https://origins.readthedocs.io/en/latest/types/data_types/object/>) used to specify an Elemental Application.

### Fields
| Field			| Type | Default    | Description |
|---------------|------|------------|-------------|
|`type`			|[Elemental Application Type](./elemental_application_type.md)|`GAUGE_UNIT`| The type of this elemental application. |
|`element`		|[Element](./element.md)| | The element to apply. |
|`aura`			|[Boolean](https://origins.readthedocs.io/en/latest/types/data_types/boolean/)|`true`| Whether or not this elemental application is prioritized as an Aura element. |
|`gauge_units`	|[Float](<https://origins.readthedocs.io/en/latest/types/data_types/float/>)| | The amount of gauge units in this elemental application. |
|`duration`		|[Float](<https://origins.readthedocs.io/en/latest/types/data_types/float/>)|`-1.0`| How long, in ticks, will this elemental application last for. This should have a value if `type` is `DURATION`. |