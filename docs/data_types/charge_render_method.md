# Charge Render Method

[Data Type](../types/data_types.md)

A [String](<https://origins.readthedocs.io/en/latest/types/data_types/string/>) that represents a [Charge Render](./charge_render.md) Method.

## Values

| Value         | Description                                                  |
|---------------|--------------------------------------------------------------|
|`SPLIT`        | Charges will have their cooldown split evenly based on the max value of `resource`. |
|`CONDITIONAL`  | The current charge count will be given by the `conditions` field. Using this [Charge Render Method](charge_render_method.md) will fully disable rendering the cooldown, and will only render the skill icon. This is because the code is not able to identify when another charge will be added, so a cooldown can't be rendered. |

!!! warning 
    If you are using the `CONDITIONAL` Charge Render Method, the cooldown will no longer be rendered. This is because the code is not able to identify when another charge will be added, so a proper cooldown can't be rendered.