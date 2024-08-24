# Defining an Elemental Burst for an Active Self power

**Origins: Genshin** only supports creating an Elemental Burst out of the [Active Self (Power Type)](../power_types/active_self.md). This is because in the [actual game](https://genshin-impact.fandom.com/wiki/Elemental_Burst), you can only use these when clicking `Q` (or whatever key you binded it to)!

An Elemental Burst, in Genshin, is considered as your most powerful ability. You may know this as an "Ultimate" in other games.

## Tutorial

**Important:** this example guides you through defining an Elemental Burst for the [Active Self (Power Type)](../power_types/active_self.md), as well as specific use cases that could be helpful in the future. It is required for you to have read and understood [Defining a Power in JSON](https://origins.readthedocs.io/en/latest/guides/data/define_power/) first, as well as looked through [Active Self (Power Type)](https://origins.readthedocs.io/en/latest/types/power_types/active_self/)!

To declare an [Active Self (Power Type)](../power_types/active_self.md) power as an [Elemental Burst](../data_types/elemental_burst.md), just add the `"elemental_burst"` field.

Let's create a power named `awesome_power.json` inside the `<namespace>/powers` folder. The `<namespace>` part is basically the namespace of your datapack (the ID that specifies your datapack from others). Since this is a tutorial, I'll use `tutorial`, however you may use any namespace you want. The full path for this power for me would be `data/tutorial/powers/awesome_power.json`.

```json
{
	"type": "origins:active_self",
	"name": "My Awesome Power!",
	"description": "A really amazing power!",
	"key": "key.origins.primary_active",
	"cooldown": 50,

	"elemental_burst": {

	},

	"entity_action": {
		// ...
	}
}
```

!!! warning 
	Do **not** add `// ...` into your JSON code! JSON does not support comments, so that would result in an error instead! `// ...` means "and more", which means that you could (and should!) create your own entity action for this! 

Now that you have that, we have declared this power as an Elemental Burst. However, it's missing a few key data, such as: What icon should it use? Should it render the cooldown? Should it appear as disabled? I will walk you through on how you can fill this [Object](https://origins.readthedocs.io/en/latest/types/data_types/object/).

### Displaying the cooldown text

Let's say you want the cooldown text of the Elemental Burst to be hidden. You can do so by using the `show_cooldown` field. For this example, we want the cooldown text of our Elemental Burst to be shown, so we use `true` as the value instead.

```json
{
	"elemental_burst": {
		"show_cooldown": true
	}
}
```

!!! warning 
	Please do **not** delete your previous code! I am just focusing on the `elemental_burst` field here, which is why it is isolated.

### "Disabling" the Elemental Burst

Let's say you want the Elemental Burst to appear "disabled", or grayed out. You can do so by using the `disable_condition` field, which takes in a [Entity Condition Type](https://origins.readthedocs.io/en/latest/types/entity_condition_types/) object. If this condition is `true`, then the Elemental Burst will appear disabled. However, having the Elemental Burst as disabled will not affect the actual power. This means that the power may still be used despite the Elemental Burst appearing as disabled, depending on the conditions.

For this example, we want to disable the Elemental Burst when they are sneaking. We can use the `origins:sneaking` condition type for this.

```json
{
	"elemental_burst": {
		"show_cooldown": true,
		"disable_condition": {
			"type": "origins:sneaking"
		}
	}
}
```

### Creating icons for the Elemental Burst

Now, you would want to have an icon for this Elemental Burst. Icons are textures, which means that they are supposed to be in a Resource Pack, not a Data Pack! When creating icons for an Elemental Burst, they should fit within a 100x100 circle in a 112x112 grid.

!!! tip
	If you don't want to create your own icon, **Origins: Genshin** also has predefined sprites that you may use. You can look them up in the [Sprites](../misc/sprites.md) page.

	If you do decide to use an existing icon instead of creating your own, then you may skip the creation part in this section.

For your convenience, I have created a template for you to use. You can also resize this image as well, so long as you don't change the original ratio (because that will mess up the precision).

![Elemental Burst Dimension](../img/burst_dimension.png)

*The blue circle is the guide where your icon fits inside the Elemental Burst.*

Now that you have done that, it's time to create a Resource Pack to store the texture in.

!!! tip
	If you're unfamiliar with creating a Resource Pack, you may refer to [Minecraft Wiki: Creating a resource pack](https://minecraft.wiki/w/Tutorials/Creating_a_resource_pack).

For this tutorial, let's store it inside the `assets/<namespace>/skills` folder, as `elemental_burst.png`. Again, `<namespace>` refers to the ID that seperates this resource pack from others. Since this is a tutorial, I will use `tutorial`, so the file path for me would be `assets/tutorial/skills/elemental_burst.png`.

Back to our data pack, you'd want to use the icon you just created. To do so, you can use the `icon_conditions` field.

```json
{
	"elemental_burst": {
		"show_cooldown": true,
		"disable_condition": {
			"type": "origins:sneaking"
		},
		"icon_conditions": [
			{
				"icon": "tutorial:skills/elemental_burst.png"
			}
		]
	}
}
```

Note that if the mod cannot find the texture you icon, a pink and black-checkered icon will appear instead! This makes it easier for you to know that your icon isn't working properly!

### Declaring an Elemental Burst power

Now that our Elemental Burst power is finished, we need to declare it in our Origin. This is similar to how you declare powers inside an Origin, but this time, for only one power.

Let's create an origin with the file name `test.json` inside the `<namespace>/origins` folder. Since this is a tutorial, I will use `tutorial` as the namespace.

```json
{
	"name": "Test",
	"description": "My amazing origin!",
	"impact": 1,
	"powers": [
		// ...
	]
}
```

!!! warning 
	Quick reminder to **not** add `// ...` into your JSON code! Again, `// ...` means "and more", which means that you could (and should!) create your own powers for this! 

Since we want to declare our `awesome_power.json` power as an Elemental Burst for this Origin, we should add an `elemental_burst` field to this Origin object, then add our `awesome_power.json` power to it.

```json
{
	"name": "Test",
	"description": "My amazing origin!",
	"icon": "minecraft:command_block",
	"impact": 1,
	"powers": [
		// ...
	],
	"elemental_burst": "tutorial:awesome_power"
}
```

And that's it! When you select the `Test` Origin, you should be able to see your new, shiny Elemental Burst icon on the lower left of the screen!

### Conditional Elemental Burst icons

Some Origins have "multi-power" abilities, which I consider to be powers that can do different things based on conditions. For example: you could have a normal Elemental Burst, and an "enhanced" Elemental Burst when a resource reaches a certain value or when you're sneaking.

Luckily, we can effortlessly do that here, using the `icon_condition` field. This is also the reason why icons could have conditions, for cases like these, allowing for more flexibility in rendering Elemental Burst icons for data pack creators!

Let's imagine a power named `"Fire and Ice"` that:

- Normally: deals damage to nearby entities.  
- When the player is on fire: would deal Fire DMG to nearby entities and set them on fire instead.  
- When the player is in a cold biome (temperature ≥ 0.5): would deal Freeze DMG to nearby entities and give them Slowness II for 10 seconds.

Let's create a power named `fire_and_ice.json` inside the `<namespace>/powers` folder. Again, `<namespace>` is the namespace of your datapack (the ID that specifies your datapack from others). Since this is a tutorial, I'll use `tutorial`, however you may use any namespace you want. The full path for this power for me would be `data/tutorial/powers/fire_and_ice.json`.

```json
{
	"type": "origins:active_self",
	"name": "Fire and Ice",
	"description": "With the balanced forces of Fire and Ice, deals damage to entities around you. If you are on fire, the force of Fire burns brighter, dealing Fire DMG instead. If you are in a cold biome, the force of Ice shines colder, dealing Freeze DMG and applying Slowness II instead.",
	"key": "key.origins.primary_active",
	"cooldown": 1200,

	"elemental_burst": {
		"show_cooldown": true,
		"should_render": true,
		"icon_conditions": [

		]
	},

	"entity_action": {
		"type": "origins:area_of_effect",
		"radius": 8,
		"bientity_action": {
			"type": "origins:if_else_list",
			"actions": [
				{
					"condition": {
						"type": "origins:actor_condition",
						"condition": {
							"type": "origins:on_fire"
						}
					},
					"action": {
						"type": "origins:target_action",
						"action": {
							"type": "origins:damage",
							"amount": 5,
							"damage_type": "minecraft:on_fire"
						}
					}
				},
				{
					"condition": {
						"type": "origins:actor_condition",
						"condition": {
							"type": "origins:biome",
							"condition": {
								"type": "origins:temperature",
								"comparison": "<=",
								"compare_to": 0.5
							}
						}
					},
					"action": {
						"type": "origins:target_action",
						"action": {
							"type": "origins:and",
							"actions": [
								{
									"type": "origins:damage",
									"amount": 5,
									"damage_type": "minecraft:freeze"
								},
								{
									"type": "origins:apply_effect",
									"effect": {
										"effect": "minecraft:slowness",
										"duration": 200,
										"amplifier": 1
									}
								}
							]
						}
					}
				},	
				{
					"action": {
						"type": "origins:target_action",
						"action": {
							"type": "origins:damage",
							"amount": 5,
							"damage_type": "minecraft:generic"
						}
					}
				}
			]
		}
	}
}
```

We would want a different icon per variation of the Elemental Burst: an icon for the Fire version, for the Ice version, and for the normal version. Since we already have our wanted conditions for these icons, all we need to do is add them and their respective icon to the `icon_conditions` field.

```json
{
	// ...	

	"elemental_burst": {
		"show_cooldown": true,
		"should_render": true,
		"icon_conditions": [
			{
				"icon": "tutorial:skills/elemental_burst_fire.png",
				"condition": {
					"type": "origins:on_fire"
				}
			},
			{
				"icon": "tutorial:skills/elemental_burst_ice.png",
				"condition": {
					"type": "origins:biome",
					"condition": {
						"type": "origins:temperature",
						"comparison": "<=",
						"compare_to": 0.5
					}
				}
			},
			{
				"icon": "tutorial:skills/elemental_burst.png"
			}
		]
	}

	// ...
}
```

Notice how the "normal" icon is at the bottom. This is because of the way icons inside `icon_conditions` are rendered. The **first** icon to have a condition that is true, or no condition at all, will be the selected icon. If we place our normal icon above our ice and fire icon, our normal icon would always be the rendered icon, regardless of whether the player is in a cold biome or on fire; because the normal icon is always the first icon that passes the test, so it will always be the selected icon.

This feature allows you to create priority between rendering your icons, with "higher" icons having more priority than "lower" icons. 

### Seperated cooldowns and reversal

Some origins may have "Ultimate" abilities that have a seperate cooldown than the one on the Active Self power. This may cause issues with rendering Elemental Bursts, as it will appear usable when it is actually on cooldown.

Now, you could use a `disable_condition` and make the Elemental Burst appear disabled, but the cooldown is still shown.

Luckily, **Origins: Genshin** has a solution for this problem too: the `cooldown` field. The `cooldown` field allows you to set a power to act as it's cooldown, which could either be a [Resource (Power Type)](https://origins.readthedocs.io/en/latest/types/power_types/resource/) or a power type with a built-in cooldown.

Now, what would happen when your cooldown is handled differently? Built-in cooldowns in Origins go from `0` to `max`, where `max` is the cooldown value, but some people prefer to handle their cooldowns going from `max` to `0`. That causes a new problem: the cooldown rendering in reverse. You'd see the cooldown number going up instead of down.

How do we solve it? Rewrite the cooldown? Well, you can, but that would be incredibly tedious. Instead, **Origins: Genshin** has a solution for this problem as well: the `reverse` field. Setting `reverse` to `true` allows for the renderer to know that the power's cooldown goes from `max` to `0` instead of `0` to `max`, so it will render your cooldown properly instead of reverse, given that your cooldown does indeed go from `max` to `0`.

### Displaying energy values

In Genshin, an Elemental Burst is gained through Energy. In Origins, this could be a resource, or a cooldown, if you want.

Some Origins may have an "energy/mana system", where casting a specific ability requires `X` of that resource. Of course, **Origins: Genshin** allows you to display that as well.

Lets imagine a power named `"Heavy Smash"`, that deals 10 DMG. This needs `5` of a resource named `"Heavy Strike"`, with `"Heavy Strike"` capping at `60`.

```json
{
	"type": "origins:active_self",
	"name": "Heavy Smash",
	"description": "Strikes heavily, dealing damage to your targetted enemy.",
	"key": "key.origins.primary_active",
	"cooldown": 6,
	"condition": {
		"type": "origins:resource",
		"resource": "tutorial:heavy_strike",
		"comparison": ">=",
		"compare_to": 5
	},

	"elemental_burst": {
		"show_cooldown": true,
		"should_render": true,
		"disable_condition": {
			"type": "origins:power_active",
			"power": "tutorial:heavy_smash",
			"inverted": true
		},
		"icon_conditions": [
			{
				"icon": "tutorial:skills/elemental_burst.png",
				"energy_resource": "tutorial:heavy_strike",
				"color": { "hex": "#32ae7a" },
				"outline_color": { "hex": "#97ffb7" }
			}
		]
	},

	"entity_action": {
		"type": "origins:if_else",
		"condition": {
			"type": "origins:raycast",
			"block": false,
			"entity": true,
			"hit_bientity_condition": {
				"type": "origins:target_condition",
				"condition": {
					"type": "origins:living"
				}
			}
		},
		"if_action": {
			"type": "origins:raycast",
			"block": false,
			"entity": true,
			"bientity_condition": {
				"type": "origins:target_condition",
				"condition": {
					"type": "origins:living"
				}
			},
			"bientity_action": {
				"type": "origins:damage",
				"amount": 10,
				"damage_type": "minecraft:generic"
			}
		}
	}
}
```

Here, we used the `resource` field to declare `tutorial:heavy_smash` as the resource to use when rendering Energy, along with adding the Elemental Burst's color and outline color.

Great! We have our Elemental Burst Icon, and now it can display Energy. There's just one problem: the max value. Here, our Elemental Burst only needs a total of `5` from the `tutorial:heavy_smash` resource, but it appears as unfilled since the max value of `tutorial:heavy_smash` is `60`. Luckily, there's a solution to this problem: the `new_max` field. This field allows you to set a pseudo-maximum value for a resource, which will be used as the max value when rendering energy.

```json
{
	// ...

	"elemental_burst": {
		"show_cooldown": true,
		"should_render": true,
		"disable_condition": {
			"type": "origins:power_active",
			"power": "tutorial:heavy_smash",
			"inverted": true
		},
		"icon_conditions": [
			{
				"icon": "tutorial:skills/elemental_burst.png",
				"energy_resource": "tutorial:heavy_strike",
				"color": { "hex": "#32ae7a" },
				"outline_color": { "hex": "#97ffb7" },
				"new_max": 5
			}
		]
	},

	// ...
}
```

Now, our Energy should appear full when it's greater than or equal to `5`.
