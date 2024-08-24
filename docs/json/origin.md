# Origin JSON Format (Overwrite)
This is the format of a JSON file describing an origin. Origins are used to give players special abilities, which can alter the player's gameplay.

Origin JSON files need to be placed inside the `data/<namespace>/origins` folder of your datapack. The said files can be referenced as `namespace:path/to/origin` (`data/namespace/origins/path/to/origin.json`) in the origins field of an [Origin Layer (JSON)](https://origins.readthedocs.io/en/latest/json/origin_layer/) file.

!!! warning 
    This JSON object is originally an **Origins/Apoli** JSON field, but has been modified by **Origins: Genshin** to add extra functionality to it. You can find the new fields added along with the old fields below.

## Fields
| Field   | Type | Default    | Description |
|---------|------|------------|-------------|
|`powers`           |[Array](https://origins.readthedocs.io/en/latest/types/data_types/array/) of [Identifiers](https://origins.readthedocs.io/en/latest/types/data_types/identifier/)|*optional*|The namespace and IDs of the powers this origin should have.|
|`icon`             |[Item Stack](https://origins.readthedocs.io/en/latest/types/data_types/item_stack/)|*optional*|The item stack which is displayed as the icon for the origin in the top-left corner of the choose/view origin screen.|
|`unchoosable`      |[Boolean](https://origins.readthedocs.io/en/latest/types/data_types/boolean/)|`false`|If set to `true`, this origin will not show up in any origin layer to choose it, but it will still be able to be set for that layer with a command or via an origin upgrade.|
|`order`            |[Integer](<https://origins.readthedocs.io/en/latest/types/data_types/integer/>)|*optional*|Specifies the position of this origin in the choose origin screen among the other origins with the same impact in the layer. If not specified, will be a really large number - basically adding it in the end.|
|`impact`           |[Integer](<https://origins.readthedocs.io/en/latest/types/data_types/integer/>)|`0`|Specifies the impact of this origin with a number from 0 (none) to 3 (high).|
|`name`             |[Text Component](https://origins.readthedocs.io/en/latest/types/data_types/text_component/)|*optional*|The display name of the origin.|
|`description`      |[Text Component](https://origins.readthedocs.io/en/latest/types/data_types/text_component/)|*optional*|The description of the origin.|
|`upgrades`         |[Array](https://origins.readthedocs.io/en/latest/types/data_types/array/) of [Upgrades](https://origins.readthedocs.io/en/latest/json/upgrade/)|*optional*|A list of upgrades for this origin, specifying which advancements turn this origin into which other origin.|
|`loading_priority` |[Integer](<https://origins.readthedocs.io/en/latest/types/data_types/integer/>)|`0`|Specifies when this origin is loaded. Higher numbers mean it's loaded later, which means it will override those with lower loading priorities which share the same ID.|
|`elemental_skill`|[Identifier](https://origins.readthedocs.io/en/latest/types/data_types/identifier/)|*optional*|The namespace and ID of an [Active Self](../power_types/active_self.md) power that is declared as an [Elemental Skill](../data_types/elemental_skill.md).|
|`elemental_burst`|[Identifier](https://origins.readthedocs.io/en/latest/types/data_types/identifier/)|*optional*|The namespace and ID of an [Active Self](../power_types/active_self.md) power that is declared as an [Elemental Burst](../data_types/elemental_burst.md)|

## Examples
```json
{
    "powers": [],
    "icon": {
        "item": "minecraft:zombie_head"
    },
    "order": 3,
    "impact": 2,
    "name": "Zombie",
    "description": "Raah, brains..."
}
```
This example will add an origin that has a Zombie Head item as its icon.