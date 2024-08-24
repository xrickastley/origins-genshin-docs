# Defining an Elemental Skill for an Active Self power

**Origins: Genshin** only supports creating an Elemental Skill out of the [Active Self (Power Type)](../power_types/active_self.md). This is because in the [actual game](https://genshin-impact.fandom.com/wiki/Elemental_Skill), you can only use these when clicking `E` (or whatever key you binded it to)!

An Elemental Skill, in Genshin, is one of your character's "active" abilities/talents. You may know this as just "Skill" in other games.

## Tutorial

**Important:** this example guides you through defining an Elemental Skill for the [Active Self (Power Type)](../power_types/active_self.md), as well as specific use cases that could be helpful in the future. It is required for you to have read and understood [Defining a Power in JSON](https://origins.readthedocs.io/en/latest/guides/data/define_power/) first, as well as looked through [Active Self (Power Type)](https://origins.readthedocs.io/en/latest/types/power_types/active_self/)!

!!! tip
	Declaring an [Elemental Skill](../data_types/elemental_skill.md) is similar to declaring an [Elemental Burst](../data_types/elemental_burst.md)! If you have read that page, then you may skip to [Displaying charges](#displaying_charges). Of course, you may choose to read or skim the content here as well.

To declare an [Active Self (Power Type)](../power_types/active_self.md) power as an [Elemental Skill](../data_types/elemental_skill.md), just add the `"elemental_skill"` field.

Let's create a power named `cool_power.json` inside the `<namespace>/powers` folder. The `<namespace>` part is basically the namespace of your datapack (the ID that specifies your datapack from others). Since this is a tutorial, I'll use `tutorial`, however you may use any namespace you want. The full path for this power for me would be `data/tutorial/powers/cool_power.json`.

```json
{
	"type": "origins:active_self",
	"name": "My Cool Power!",
	"description": "A really cool power!",
	"key": "key.origins.secondary_active",
	"cooldown": 50,

	"elemental_skill": {

	},

	"entity_action": {
		// ...
	}
}
```

!!! warning 
	Do **not** add `// ...` into your JSON code! JSON does not support comments, so that would result in an error instead! `// ...` means "and more", which means that you could (and should!) create your own entity action for this! 

Now that you have that, we have declared this power as an Elemental Skill. However, it's missing a few key data, such as: What icon should it use? Should it render the cooldown? Should it appear as disabled? I will walk you through on how you can fill this [Object](https://origins.readthedocs.io/en/latest/types/data_types/object/).

### Displaying the cooldown text

Let's say you want the cooldown text of the Elemental Skill to be hidden. You can do so by using the `show_cooldown` field. For this example, we want the cooldown text of our Elemental Skill to be shown, so we use `true` as the value instead.

```json
{
	"elemental_skill": {
		"show_cooldown": true
	}
}
```

!!! warning 
	Please do **not** delete your previous code! I am just focusing on the `elemental_skill` field here, which is why it is isolated.

### "Disabling" the Elemental Skill

Let's say you want the Elemental Skill to appear "disabled", or grayed out. You can do so by using the `disable_condition` field, which takes in a [Entity Condition Type](https://origins.readthedocs.io/en/latest/types/entity_condition_types/) object. If this condition is `true`, then the Elemental Skill will appear disabled. However, having the Elemental Skill as disabled will not affect the actual power. This means that the power may still be used despite the Elemental Skill appearing as disabled, depending on the conditions.

For this example, we want to disable the Elemental Skill when they are sneaking. We can use the `origins:sneaking` condition type for this.

```json
{
	"elemental_skill": {
		"show_cooldown": true,
		"disable_condition": {
			"type": "origins:sneaking"
		}
	}
}
```

### Creating icons for the Elemental Skill

Now, you would want to have an icon for this Elemental Skill. Icons are textures, which means that they are supposed to be in a Resource Pack, not a Data Pack! Unlike icons for an Elemental Burst, icons for an Elemental Skill are much simpler, fitting within a 76x76 circle in a 76x76 grid.

!!! tip
	If you don't want to create your own icon, **Origins: Genshin** also has predefined sprites that you may use. You can look them up in the [Sprites](../misc/sprites.md) page.

	If you do decide to use an existing icon instead of creating your own, then you may skip the creation part in this section.

For your convenience, I have created a template for you to use. You can also resize this image as well, so long as you don't change the original ratio (because that will mess up the precision).

![Elemental Skill Dimension](../img/skill_dimension.png)

*The blue circle is the guide where your icon fits inside the Elemental Skill.*

Now that you have done that, it's time to create a Resource Pack to store the texture in.

!!! tip
	If you're unfamiliar with creating a Resource Pack, you may refer to [Minecraft Wiki: Creating a resource pack](https://minecraft.wiki/w/Tutorials/Creating_a_resource_pack).

For this tutorial, let's store it inside the `assets/<namespace>/skills` folder, as `elemental_skill.png`. Again, `<namespace>` refers to the ID that seperates this resource pack from others. Since this is a tutorial, I will use `tutorial`, so the file path for me would be `assets/tutorial/skills/elemental_skill.png`.

Back to our data pack, you'd want to use the icon you just created. To do so, you can use the `icon_conditions` field.

```json
{
	"elemental_skill": {
		"show_cooldown": true,
		"disable_condition": {
			"type": "origins:sneaking"
		},
		"icon_conditions": [
			{
				"icon": "tutorial:skills/elemental_skill.png"
			}
		]
	}
}
```

Note that if the mod cannot find the icon you supplied, a pink and black-checkered icon will appear instead! This makes it easier for you to know that your icon isn't working properly!

### Declaring an Elemental Skill power

Now that our Elemental Skill power is finished, we need to declare it in our Origin. This is similar to how you declare powers inside an Origin, but this time, for only one power.

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

Since we want to declare our `cool_power.json` power as an Elemental Skill for this Origin, we should add an `elemental_skill` field to this Origin object, then add our `cool_power.json` power to it.

```json
{
	"name": "Test",
	"description": "My amazing origin!",
	"icon": "minecraft:command_block",
	"impact": 1,
	"powers": [
		// ...
	],
	"elemental_skill": "tutorial:cool_power"
}
```

And that's it! When you select the `Test` Origin, you should be able to see your new, shiny Elemental Skill icon on the lower left of the screen! It should be beside the Elemental Burst icon, if you have one.

!!! warning
	When your Active Self power is inside an `origins:multiple` power, you must declare the full path to that sub power. For example, if I have an `origins:multiple` power named `awesome_powers.json`, and the Active Self power declared as an Elemental Skill is inside a subpower named `"cool_power"`, the Elemental Skill has to be declared as `tutorial:awesome_powers_cool_power` instead of just `tutorial:awesome_powers`

### Conditional Elemental Skill icons

Some Origins have "multi-power" abilities, which I consider to be powers that can do different things based on conditions. For example: you could have a normal Elemental Skill, and an "enhanced" Elemental Skill when a resource reaches a certain value or when you're sneaking.

Luckily, we can effortlessly do that here, using the `icon_condition` field. This is also the reason why icons could have conditions, for cases like these, allowing for more flexibility in rendering Elemental Skill icons for data pack creators!

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
	"key": "key.origins.secondary_active",
	"cooldown": 1200,

	"elemental_skill": {
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

We would want a different icon per variation of the Elemental Skill: an icon for the Fire version, for the Ice version, and for the normal version. Since we already have our wanted conditions for these icons, all we need to do is add them and their respective icon to the `icon_conditions` field.

```json
{
	// ...	

	"elemental_skill": {
		"show_cooldown": true,
		"should_render": true,
		"icon_conditions": [
			{
				"icon": "tutorial:skills/elemental_skill_fire.png",
				"condition": {
					"type": "origins:on_fire"
				}
			},
			{
				"icon": "tutorial:skills/elemental_skill_ice.png",
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
				"icon": "tutorial:skills/elemental_skill.png"
			}
		]
	}

	// ...
}
```

Notice how the "normal" icon is at the bottom. This is because of the way icons inside `icon_conditions` are rendered. The **first** icon to have a condition that is true, or no condition at all, will be the selected icon. If we place our normal icon above our ice and fire icon, our normal icon would always be the rendered icon, regardless of whether the player is in a cold biome or on fire; because the normal icon is always the first icon that passes the test, so it will always be the selected icon.

This feature allows you to create priority between rendering your icons, with "higher" icons having more priority than "lower" icons. 

### Seperated cooldowns and reversal

Some origins may have abilities that have a seperate cooldown than the one on the Active Self power. This may cause issues with rendering Elemental Skills, as it will appear usable when it is actually on cooldown.

Now, you could use a `disable_condition` and make the Elemental Skill appear disabled, but the cooldown is still shown.

Luckily, **Origins: Genshin** has a solution for this problem too: the `cooldown` field. The `cooldown` field allows you to set a power to act as it's cooldown, which could either be a [Resource (Power Type)](https://origins.readthedocs.io/en/latest/types/power_types/resource/) or a power type with a built-in cooldown.

Now, what would happen when your cooldown is handled differently? Built-in cooldowns in Origins go from `0` to `max`, where `max` is the cooldown value, but some people prefer to handle their cooldowns going from `max` to `0`. That causes a new problem: the cooldown rendering in reverse. You'd see the cooldown number going up instead of down.

How do we solve it? Rewrite the cooldown? Well, you can, but that would be incredibly tedious. Instead, **Origins: Genshin** has a solution for this problem as well: the `reverse` field. Setting `reverse` to `true` allows for the renderer to know that the power's cooldown goes from `max` to `0` instead of `0` to `max`, so it will render your cooldown properly instead of reverse, given that your cooldown does indeed go from `max` to `0`.

### Displaying charges

In Genshin, an Elemental Skill can have charges, which is the number of times an Elemental Skill can be used in rapid succession without waiting for the cooldown. Additionally, the cooldown for each charge is seperate, and only one charge can be refilled after the cooldown period.

Some Origins have powers that use the concept of charges, where you gain one of *something* every *cooldown*, and you use *something* to keep using your power.

Sadly, **Origins: Genshin** only allows a charge count up to `3`. This is to keep parity between the maximum charge count in **Origins: Genshin** with **Genshin Impact** itself, with [Yae Miko](https://genshin-impact.fandom.com/wiki/Yae_Miko) having the highest charge count of **3**.

A filled charge will be visualized with a blue diamond ![Filled Charge](../img/charge.png), while a used charge will be denoted with a gray diamond ![Empty Charge](../img/charge_empty.png). Do note that if your `charges` is `1`, then no charges are rendered.

Let's imagine a power named `"Leap"` that, allows you to leap forward. We would want this skill to have `2` charges, and each charge would have a cooldown of `200`, or 10 seconds. Our cooldown would be in a sub-power.

```json	
{
	"type": "origins:multiple",
	"name": "Leap",
	"description": "Leaps forward. great for mobility!",
	
	"handler": {
		"type": "origins:active_self",
		"key": "key.origins.primary_active",
		"cooldown": 1,
		"condition": {
			"type": "origins:resource",
			"resource": "tutorial:leap_cooldown",
			"comparison": ">=",
			"compare_to": 200
		},
	
		"elemental_skill": {
			"show_cooldown": true,
			"should_render": true,
			"icon_conditions": [
				{
					"icon": "tutorial:skills/elemental_skill.png"
				}
			]
		},
	
		"entity_action": {
			"type": "origins:and",
			"actions": [
				{
					"type": "origins:add_velocity",
					"y": 1,
					"space": "local",
					"client": true,
					"server": false
				},
				{
					"type": "origins:add_velocity",
					"z": 1.5,
					"space": "local",
					"client": true,
					"server": false
				},
				{
					"type": "origins:change_resource",
					"resource": "tutorial:leap_cooldown",
					"change": -200,
					"operation": "add"
				}
			]
		}
	},

	"cooldown": {
		"type": "origins:resource",
		"min": 0,
		"max": 400,
		"start_value": 400
	},

	"adder": {
		"type": "origins:action_over_time",
		"interval": 1,
		"condition": {
			"type": "origins:resource",
			"resource": "tutorial:leap_cooldown",
			"comparison": "<",
			"compare_to": 400
		},
		"entity_action": {
			"type": "origins:change_resource",
			"resource": "tutorial:leap_cooldown",
			"change": 1,
			"operation": "add"
		}
	}
}
```

To declare an amount of charges, we can use the `charges` field. Since we want to have `2` charges, then we should use `2`.
```json
{
	// ...

	"elemental_skill": {
		"show_cooldown": true,
		"should_render": true,
		"icon_conditions": [
			{
				"icon": "tutorial:skills/elemental_skill.png",
				"charges": 2,
				"charge_render": {
					"type": "SPLIT"
				}
			}
		]
	},

	// ...
}
```

!!!note
	Here, we also used the `charge_render` field. It is an *optional* field, and it also dictates how charges are rendered. The default way is `"SPLIT"`, meaning to split the cooldown evenly to the charges. The other method is `"CONDITIONAL"`, where the specified amount of charges is shown when a specific condition is `true`. You can find more information on **Charge Render Methods** [here](../data_types/charge_render_method.md)

When you load it up in game, it does show as `2` charges. However, when you use the skill, you may see that the charges are being added immediately! This is because it's using the power's cooldown value, which is `5`. Let's make the Elemental Skill use our `"cooldown"` sub-power instead. Here, we don't need to set `reverse` to `true`, because our cooldown goes from `0` to `max`.

```json
{
	// ...

	"elemental_skill": {
		"show_cooldown": true,
		"should_render": true,
		"icon_conditions": [
			{
				"icon": "tutorial:skills/elemental_skill.png",
				"cooldown": "tutorial:leap_cooldown",
				"charges": 2,
			}
		]
	},

	// ...
}
```

Now, your `"Leap"` ability should have `2` charges, along with a proper cooldown!

!!! warning
	Charges uses the `cooldown` field when rendering charges, which means that it is also affected by the `reverse` field!