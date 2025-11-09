# Power

To easily get started with the Elemental Combat system, you can use this power, which allows you to easily cycle through the seven Elements!

```json
{
	"type": "apoli:multiple",
	"name": "Attunement of Elements",
	"description": "Cycle through the seven Elements and deal massive DMG with reactions!",

	"cycle": {
		"type": "apoli:resource",
		"hud_render": {
			"should_render": true,
			"sprite_location": "origins-genshin:textures/resource_bar.png",
			"bar_index": 0,
			"icon_index": 0
		},
		"min": 0,
		"max": 7,
		"start_value": 1,
		"min_action": {
			"type": "apoli:change_resource",
			"resource": "*:*_cycle",
			"operation": "set",
			"change": 1
		}
	},

	"pyro_infusion": {
		"type": "seven-elements:elemental_infusion",
		"condition": {
			"type": "apoli:resource",
			"resource": "*:*_cycle",
			"comparison": "==",
			"compare_to": 1
		},
		"element": {
			"type": "gauge_unit",
			"element": "pyro",
			"gauge_units": 2.0
		},
		"internal_cooldown": {
			"tag": "seven-elements:attune/normal_attack",
			"type": "seven-elements:default"
		},
		"priority": 1
	},

	"hydro_infusion": {
		"type": "seven-elements:elemental_infusion",
		"condition": {
			"type": "apoli:resource",
			"resource": "*:*_cycle",
			"comparison": "==",
			"compare_to": 2
		},
		"element": {
			"type": "gauge_unit",
			"element": "hydro",
			"gauge_units": 2.0
		},
		"internal_cooldown": {
			"tag": "seven-elements:attune/normal_attack",
			"type": "seven-elements:default"
		},
		"priority": 1
	},

	"anemo_infusion": {
		"type": "seven-elements:elemental_infusion",
		"condition": {
			"type": "apoli:resource",
			"resource": "*:*_cycle",
			"comparison": "==",
			"compare_to": 3
		},
		"element": {
			"type": "gauge_unit",
			"element": "anemo",
			"gauge_units": 2.0
		},
		"internal_cooldown": {
			"tag": "seven-elements:attune/normal_attack",
			"type": "seven-elements:default"
		},
		"priority": 1
	},

	"electro_infusion": {
		"type": "seven-elements:elemental_infusion",
		"condition": {
			"type": "apoli:resource",
			"resource": "*:*_cycle",
			"comparison": "==",
			"compare_to": 4
		},
		"element": {
			"type": "gauge_unit",
			"element": "electro",
			"gauge_units": 2.0
		},
		"internal_cooldown": {
			"tag": "seven-elements:attune/normal_attack",
			"type": "seven-elements:default"
		},
		"priority": 1
	},

	"dendro_infusion": {
		"type": "seven-elements:elemental_infusion",
		"condition": {
			"type": "apoli:resource",
			"resource": "*:*_cycle",
			"comparison": "==",
			"compare_to": 5
		},
		"element": {
			"type": "gauge_unit",
			"element": "dendro",
			"gauge_units": 2.0
		},
		"internal_cooldown": {
			"tag": "seven-elements:attune/normal_attack",
			"type": "seven-elements:default"
		},
		"priority": 1
	},

	"cryo_infusion": {
		"type": "seven-elements:elemental_infusion",
		"condition": {
			"type": "apoli:resource",
			"resource": "*:*_cycle",
			"comparison": "==",
			"compare_to": 6
		},
		"element": {
			"type": "gauge_unit",
			"element": "cryo",
			"gauge_units": 2.0
		},
		"internal_cooldown": {
			"tag": "seven-elements:attune/normal_attack",
			"type": "seven-elements:default"
		},
		"priority": 1
	},

	"geo_infusion": {
		"type": "seven-elements:elemental_infusion",
		"condition": {
			"type": "apoli:resource",
			"resource": "*:*_cycle",
			"comparison": "==",
			"compare_to": 7
		},
		"element": {
			"type": "gauge_unit",
			"element": "geo",
			"gauge_units": 2.0
		},
		"internal_cooldown": {
			"tag": "seven-elements:attune/normal_attack",
			"type": "seven-elements:default"
		},
		"priority": 1
	},

	"cycle_handler_forward": {
		"type": "apoli:active_self",
		"key": "key.origins.secondary_active",
		"condition": {
			"type": "apoli:sneaking",
			"inverted": true
		},
		"entity_action": {
			"type": "origins:and",
			"actions": [
				{
					"type": "apoli:if_else",
					"condition": {
						"type": "apoli:resource",
						"resource": "*:*_cycle",
						"comparison": "==",
						"compare_to": 7
					},
					"if_action": {
						"type": "apoli:change_resource",
						"resource": "*:*_cycle",
						"operation": "set",
						"change": 1
					},
					"else_action": {
						"type": "origins:change_resource",
						"resource": "*:*_cycle",
						"operation": "add",
						"change": 1
					}
				}
			]
		}
	},

	"cycle_handler_backward": {
		"type": "apoli:active_self",
		"key": "key.origins.secondary_active",
		"condition": {
			"type": "apoli:sneaking"
		},
		"entity_action": {
			"type": "origins:and",
			"actions": [
				{
					"type": "apoli:if_else",
					"condition": {
						"type": "apoli:resource",
						"resource": "*:*_cycle",
						"comparison": "==",
						"compare_to": 1
					},
					"if_action": {
						"type": "apoli:change_resource",
						"resource": "*:*_cycle",
						"operation": "set",
						"change": 7
					},
					"else_action": {
						"type": "origins:change_resource",
						"resource": "*:*_cycle",
						"operation": "add",
						"change": -1
					}
				}
			]
		}
	},

	"display": {
		"type": "apoli:action_over_time",
		"interval": 1,
		"entity_action": {
			"type": "apoli:if_else_list",
			"actions": [
				{
					"condition": {
						"type": "apoli:resource",
						"resource": "*:*_cycle",
						"comparison": "==",
						"compare_to": 1
					},
					"action": {
						"type": "origins:execute_command",
						"command": "/title @s actionbar [\"Current Attunement: \", { \"text\": \"Pyro\", \"color\": \"#fda96f\" }]"
					}
				},		
				{
					"condition": {
						"type": "apoli:resource",
						"resource": "*:*_cycle",
						"comparison": "==",
						"compare_to": 2
					},
					"action": {
						"type": "origins:execute_command",
						"command": "/title @s actionbar [\"Current Attunement: \", { \"text\": \"Hydro\", \"color\": \"#0ae5ff\" }]"
					}
				},
				{
					"condition": {
						"type": "apoli:resource",
						"resource": "*:*_cycle",
						"comparison": "==",
						"compare_to": 3
					},
					"action": {
						"type": "origins:execute_command",
						"command": "/title @s actionbar [\"Current Attunement: \", { \"text\": \"Anemo\", \"color\": \"#a7f4ce\" }]"
					}
				},
				{
					"condition": {
						"type": "apoli:resource",
						"resource": "*:*_cycle",
						"comparison": "==",
						"compare_to": 4
					},
					"action": {
						"type": "origins:execute_command",
						"command": "/title @s actionbar [\"Current Attunement: \", { \"text\": \"Electro\", \"color\": \"#e2b9ff\" }]"
					}
				},
				{
					"condition": {
						"type": "apoli:resource",
						"resource": "*:*_cycle",
						"comparison": "==",
						"compare_to": 5
					},
					"action": {
						"type": "origins:execute_command",
						"command": "/title @s actionbar [\"Current Attunement: \", { \"text\": \"Dendro\", \"color\": \"#b2ec2b\" }]"
					}
				},
				{
					"condition": {
						"type": "apoli:resource",
						"resource": "*:*_cycle",
						"comparison": "==",
						"compare_to": 6
					},
					"action": {
						"type": "origins:execute_command",
						"command": "/title @s actionbar [\"Current Attunement: \", { \"text\": \"Cryo\", \"color\": \"#d0fdfe\" }]"
					}
				},
				{
					"condition": {
						"type": "apoli:resource",
						"resource": "*:*_cycle",
						"comparison": "==",
						"compare_to": 7
					},
					"action": {
						"type": "origins:execute_command",
						"command": "/title @s actionbar [\"Current Attunement: \", { \"text\": \"Geo\", \"color\": \"#f3d862\" }]"
					}
				}
			]
		}
	}
}
```