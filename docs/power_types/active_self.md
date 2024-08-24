# Active Self (Overwrite)

[Power Type](../types/power_types.md)

Executes an [Entity Action Type](https://origins.readthedocs.io/en/latest/types/entity_action_types/) on the entity that has the power upon pressing the specified [Key](https://origins.readthedocs.io/en/latest/types/data_types/key/).

Type ID: `origins:active_self`

!!! warning 
    This JSON object is originally an **Origins/Apoli** JSON field, but has been modified by **Origins: Genshin** to add extra functionality to it. You can find the new fields added along with the old fields below.

## Fields
| Field   | Type | Default    | Description |
|---------|------|------------|-------------|
|`entity_action`|[Entity Action Type](https://origins.readthedocs.io/en/latest/types/entity_action_types/)| |The action to execute on the player.
|`cooldown`|[Integer](<https://origins.readthedocs.io/en/latest/types/data_types/integer/>)|`1`|Interval of ticks this power needs to recharge before the power can be triggered again.|
|`hud_render`|[Hud Render](https://origins.readthedocs.io/en/latest/types/data_types/hud_render/)|`{"should_render": false}`|Determines how the cooldown of this power is visualized on the HUD.|
|`key`|[Key](https://origins.readthedocs.io/en/latest/types/data_types/key/)|`{"key": "key.origins.primary_active"}`|Which active key this power should respond to.|
|`elemental_skill`|[Elemental Skill](../data_types/elemental_skill.md)|*optional*|Declares this power as an Elemental Skill. If this power is also declared as an Elemental Burst, this declaration will be ignored.|
|`elemental_burst`|[Elemental Burst](../data_types/elemental_burst.md)|*optional*|Declares this power as an Elemental Burst.

## Examples
```json
{
    "type": "origins:active_self",
    "entity_action": {
        "type": "origins:if_else",
        "condition": {
            "type": "origins:on_fire"
        },
        "if_action": {
            "type": "origins:extinguish"
        },
        "else_action": {
            "type": "origins:set_on_fire",
            "duration": 8
        }
    },
    "cooldown": 20,
    "hud_render": {
        "should_render": false
    }
}
```
This example will set the player on fire for 8 seconds, or extinguish themselves if they're already on fire upon pressing the Primary ability key.

```json
{
    "type": "origins:active_self",
    "entity_action": {
        "type": "origins:and",
        "actions": [
            {
                "type": "origins:equipped_item_action",
                "equipment_slot": "mainhand",
                "action": {
                    "type": "origins:consume",
                    "amount": 1
                }
            },
            {
                "type": "origins:apply_effect",
                "effect": {
                    "effect": "minecraft:speed",
                    "duration": 100,
                    "amplifier": 1,
                    "is_ambient": true,
                    "show_particles": true,
                    "show_icon": true
                }
            }
        ]
    },
    "cooldown": 1,
    "hud_render": {
        "should_render": false
    },
    "key": {
        "key": "key.use",
        "continuous": true
    },
    "condition": {
        "type": "origins:equipped_item",
        "equipment_slot": "mainhand",
        "item_condition": {
            "type": "origins:ingredient",
            "ingredient": {
                "item": "minecraft:sugar"
            }
        }
    }
}
```
This example will allow the player that has the power to essentially consume a Sugar item if the player is holding a Sugar item, which would then apply a Speed II status effect that would last for 5 seconds upon pressing the `key.use` keybind. (The example is bound to the `key.use` keybind, as seen inside the [`key`](https://origins.readthedocs.io/en/latest/types/data_types/key/) object field.)