# Elemental Combat

The implementation of elements in **Origins: Genshin** aims to resemble that of Genshin Impact's while being inherently unique code-wise.

As a result, Elements and Reactions should behave as close as possible, if not exactly like in Genshin Impact.

P.S. If you just want to see what *quirks* **Origins: Genshin** has done to implement the Elements from Genshin Impact while keeping Minecraft in mind, you may skip to the [Implementation](#implementation) section.

## The Seven Elements

In Genshin Impact *and* **Origins: Genshin**, there exists the seven Elements: <span class="pyro">**Pyro**</span>, <span class="hydro">**Hydro**</span>, <span class="anemo">**Anemo**</span>, <span class="electro">**Electro**</span>, <span class="dendro">**Dendro**</span>, <span class="cryo">**Cryo**</span>, and <span class="geo">**Geo**</span>. Non-elemental damage is considered **Physical**.

By combining specific elements together, you're able to trigger [Elemental Reactions](./elemental_reactions.md)!

When applying an element to an entity, it will decay over time, so there isn't any "infinite elemental application"!

!!! tip
	If you wish to disable elements ("I want to just use this mod for cool power rendering"), you may disable them with a gamerule! Simply do `/gamerule doElements false` and Elements will simply serve as colored DMG!

	This gamerule doesn't nullify Elemental RES% and Elemental DMG Bonus% though, as they still apply even when elements is disabled!

## Elemental Gauge Theory

!!! tip
	You **technically** don't need to read all of this! This section dives deep into the inner workings of Genshin's Elemental Combat system, which has been applied to **Origins: Genshin**. If you wish to see the various Minecraft *compats* that have been made, you may skip to the [Implementation](#implementation) section instead. 

### Introduction

In Genshin Impact, when you apply an element through an attack, most people think that the element is applied as-is; thinking of applied elements as two states of *applied* and *not applied*. In reality, there is a system beneath the simple application of elements that allows you to take advantage of certain characters over the others.

When you apply an element through an attack, a certain amount of **Gauge Units** corresponding to that element are applied to the target. Each attack has a certain amount of **Gauge Units** that it can apply, which can differ across attacks. Simply put, this can be thought of as the amount of the applied element.

When an Element is applied to an enemy that isn't inflicted with an Element, the Element is considered an **Aura Element** or an **Elemental Aura**. When a reaction is triggered against an enemy **already** afflicted with an **Aura Element**, the element that *sparked* the reaction is the **Triggering Element**. **Geo** and **Anemo** cannot apply any Auras, and as such, cannot be **Aura Elements** (unless otherwise specified, i.e. Anemo Hypostasis, Geo Hypostasis).

### Elemental Auras and the Aura Tax

In the **Elemental Gauge Theory**, elements are represented as **gauges**, hence the name **Elemental Gauge Theory**/**Gauge Unit Theory**. This *gauge* represents how *much* of an Element is currently applied, and when referred to, are called **1-unit**, or **1U** for short.

The values for each gauge are dependent on the attack that inflicted the Element. For instance, Furina's Elemental Skill: [Salon Solitare](https://genshin-impact.fandom.com/wiki/Salon_Solitaire), is a **1U** Hydro Attack. 

When an Element is applied as an **Elemental Aura**, it is *taxed* due to the **Aura Tax**, which states that if an elemental attack is being used to **apply** an **Elemental Aura**, the amount of Gauge Units it has is reduced by **20%**. For example, if a Hydro **Aura** is created by Furina's Elemental Skill: [Salon Solitare](https://genshin-impact.fandom.com/wiki/Salon_Solitaire), a **1U** Hydro Attack, the applied Gauge Units onto the attacked target will be **0.8U** due to the **Aura Tax**.

It is also important to note that when Elemental Auras are applied from multiple sources, they **do not** stack on top of each other. Instead, the Elemental Aura is simply *refreshed*. When an Elemental Aura is *refreshed*, the Elemental Application with the **highest Gauge Units** is used as the new Gauge Unit value. Additionally, *refreshing* an Elemental Aura will **not exempt** it from the **Aura Tax**.

For instance, if a target currently has a **1U** Hydro Aura and they are attacked with a **2U** Hydro Attack, the Hydro Aura will now be a **2U** Hydro Aura with it's current Gauge Units being **1.6U** due to the **Aura Tax**.

### Triggering Elements and Elemental Reactions

When a valid **Triggering Element** is applied to a target that has an **Elemental Aura**, an **Elemental Reaction** is triggered and a portion of the **Elemental Aura**'s gauge is consumed.

The amount of Gauge Units consumed are dependent on the attack that triggered the **Elemental Reaction**. For example, if a **1U** Electro Attack is applied onto an entity with the **Pyro** aura to trigger the **Overloaded** reaction, the **Pyro** aura is reduced by **1** Gauge Unit.

Each Reaction has its own **Reaction Cost**, also known as the **Reaction Coefficient**. The **Reaction Coefficient** is a factor that amplifies how much Gauge Units are consumed from the **Elemental Aura** when a reaction is triggered. For example, if Furina's Elemental Burst: Let the People Rejoice, a **1U** Hydro Attack, reacts with a **1U** Pyro Aura, Hydro Vaporize (also known as Forward Vaporize) is triggered, which has a **Reaction Coefficient** of **2**. This means that **2U** of the Pyro aura are consumed, consuming all of the Pyro aura.

### Aura Decay Rate and Decay Rate Inheritance
An **Elemental Aura** decays over time until it is depleted, with the decay rate in (s/GU) being:
$$
D(x) = \frac{\text{Base Duration}}{\text{Initial Gauge}} = \frac{35}{4x} + \frac{25}{8}
$$
where, \(x = \text{Gauge}_\text{Elemental Attack}\).

When an Elemental Attack with **higher** initial Gauge Units is applied on top of an Elemental Aura with a lower amount of initial Gauge Units, the resulting aura will **inherit** the decay rate of the previous Elemental Aura.

However, **Decay Rate Inheritance** does not apply to the Pyro aura.

## Advanced Mechanics, Simultaneous and Underlying Auras

!!! tip
	This section is a follow-up and assumes you have read and know the concepts from the [Elemental Gauge Theory](#elemental-gauge-theory) section. 

This section contains the more *special* cases of elements that aren't handled by the standard system of **Aura Elements** and **Triggering Elements**.

### Simultaneous Auras

Normally, a target is only afflicted with a single Elemental Aura. However, there are instances where this may change and multiple simultaneous Elemental Auras may coexist with one another. The best example of this is the **Cryo** and **Dendro** auras, both of which do not react with each other, resulting in both coexisting as Elemental Auras.

This concept applies to only a couple of elements and reactions, being Hydro and Electro (Electro-Charged), Burning, Quicken and Frozen, with some of these using the **Underlying Aura** subsystem.

### Underlying Auras

An **Underlying Aura** is a special type of [Simultaneous Aura](#simultaneous-auras), having it's element "lying under" another aura. This allows Elemental Auras of higher priority to effectively *hide* Elemental Auras with lower priority. As such, when the Aura that *hides* these Underlying Auras is fully consumed, the Underlying Auras are *exposed*, allowing for them to be triggered with.

### Hydro and Electro (Electro-Charged)

Unlike standard Elemental Reactions where the **Elemental Aura** being consumed by the **Triggering Reaction**, when Electro-Charged is triggered, it allows **both** Electro and Hydro to coexist as Elemental Auras. While both of these elements exist on a target, Electro-Charged deals one tick of DMG per second, consuming **0.4** GU from both auras. Additionally, both auras will still continue to decay naturally while Electro-Charged is being triggered.

When a third Element is introduced, it can react with both Electro and Hydro at the same time, allowing you to trigger two reactions at once. For instance, applying the **Pyro** aura on a target with both the **Hydro** and **Electro** aura allows both **Overloaded** and **Vaporize** to be triggered at the same time/

### Burning

When Burning is triggered, much like **Electro-Charged**, both Pyro and Dendro auras coexist with one another. However, the Dendro aura will now decay at a special rate, while the Pyro aura decays naturally. In addition to this, a Burning aura is created on the target, which coexists with both Pyro and Dendro auras.

The special Dendro consumption rate (gauge units/second) is:
$$
D(x) = \text{max}(0.4, \text{ Natural Decay Rate}_\text{Dendro Aura} × 2)
$$

Do note that this Dendro consumption rate is applied per-tick while the Burning aura is active, not per "reaction" like the Electro-Charged reaction.

Burning also applies 1 GU of Pyro (2 sec ICD) per tick. The Burning aura coexists with the Pyro and Dendro auras, but also has a higher priority over them, allowing them to be [Underlying Auras](#underlying-auras). In addition to this, the Burning aura and the Dendro aura maintain the Burning state, and as such, will end if either aura is depleted.

### Quicken

Quicken is triggered like a normal reaction, the only exception being it's ability to generate a new Elemental Aura: the **Quicken** aura. This Quicken aura can trigger most Dendro reactions, except another Quicken reaction. 

For instance, if **Hydro** is applied onto a Quicken aura, it triggers **Bloom** and it also **may** trigger **Electro-Charged**.

Applying **Electro** onto a **Quicken** Aura triggers **Aggravate**, but this Electro aura is allowed to co-exist with the Quicken aura as an Underlying Aura. Likewise, applying **Dendro** onto a **Quicken** aura triggers **Spread**, and this Dendro aura is also allowed to co-exist with the Quicken aura as an Underlying Aura.

### Hydro-Freeze Double Aura

**Hydro** may coexist with the **Freeze** aura. This Double-aura interaction is only achieved if a Cryo attack (the Triggering element) **doesn't** consume the currently applied **Hydro** aura (the Aura element). This interaction **cannot** happen in the reverse order.

This specific interaction creates a Freeze aura that **coexists** alongside the Hydro aura. However, you may **only** trigger Swirl against this Double aura, as explained [here](https://genshin-impact.fandom.com/wiki/Elemental_Gauge_Theory/Simultaneous_Reaction_Priority#Freeze_+_Hydro). Applying **Pyro** or **Electro** will only trigger their associated **Freeze** reaction, while **Geo** will trigger **Shatter** before triggering **Hydro** Crystallize.

### Cryo-Dendro Double Aura

Unlike all the other Double aura interactions mentioned up to this point, the Cryo-Dendro Double aura is unique, as it is caused by Cryo and Dendro not having a reaction with each other.

When triggering reactions against this Double aura, the Cryo reaction is prioritized over the Dendro one, allowing you to trigger the Dendro reactions with a lesser gauge consumption.

This is the mechanic that allows the "Fridge" mechanic to work, which takes advantage of the Frozen > Bloom Reaction priority to trigger more Bloom reactions with the same Dendro aura.

## Implementation

As much as possible, **Origins: Genshin** wishes a one-to-one recreation of the Elemental system from Genshin Impact. As such, all *quirks* above are expected to work in the same way in **Origins: Genshin**.

However, there are *some* changes upon *transposing* the Elemental system into Minecraft, ensuring a proper integration with Minecraft rather than a "I made Minecraft into Genshin" moment.

### Damage Type Tags

**All** DMG dealt from reactions:

- Bypasses Minecraft's DMG cooldown ([`#minecraft:bypasses_cooldown`](https://minecraft.wiki/w/Damage_type_tag_(Java_Edition)#bypasses_cooldown))
- Bypasses Shields ([`#minecraft:bypasses_shields`](https://minecraft.wiki/w/Damage_type_tag_(Java_Edition)#bypasses_shields))
- Has no impact ([`#minecraft:no_impact`](https://minecraft.wiki/w/Damage_type_tag_(Java_Edition)#no_impact))
- Does no knockback ([`#minecraft:no_knockback`](https://minecraft.wiki/w/Damage_type_tag_(Java_Edition)#no_knockback))
- Doesn't trigger the DMG cooldown (`#origins-genshin:prevents_cooldown_trigger`)

Unlike **Genshin Impact**, Transformative Reactions (e.g. Overloaded, Superconduct) may also be affected by DMG-amplifying effects such as Protection and Resistance (DMG% Down) or [Modify Damage Dealt (Power Type)](https://origins.readthedocs.io/en/latest/types/power_types/modify_damage_dealt/) from Origins.

**Overloaded** and **Burning** are considered "Fire" DMG ([`#minecraft:is_fire`](https://minecraft.wiki/w/Damage_type_tag_(Java_Edition)#is_fire)). This means that disabling `fireDamage` or having the [Fire Resistance](https://minecraft.wiki/w/Fire_Resistance) effect will nullify both **Overloaded** and **Burning** DMG. Likewise, the [Fire Protection](https://minecraft.wiki/w/Fire_Protection) enchantment also reduces the DMG received from these reactions.

**Overloaded** is also considered "Explosion" DMG ([`#minecraft:is_explosion`](https://minecraft.wiki/w/Damage_type_tag_(Java_Edition)#is_explosion)). This means that the [Blast Protection](https://minecraft.wiki/w/Blast_Protection) enchantment reduces the DMG received from the **Overloaded** reaction.

**Electro-Charged** is considered "Lightning" DMG ([`#minecraft:is_lightning`](https://minecraft.wiki/w/Damage_type_tag_(Java_Edition)#is_lightning)). However, this will not "transform" mobs upon being hit (e.g. Villager to Witch), as this Damage type tag only dictates if turtles drop bowls upon being killed, as described by the [Minecraft Wiki](https://minecraft.wiki/w/Damage_type_tag_(Java_Edition)#is_lightning:~:text=Used%20to%20make%20turtles%20drop%20bowls%20when%20killed%20by%20lightning.).

The **Shatter** reaction is now triggered **if** the target receives **any** form of Geo DMG **or** when they are hit with an **Axe** or **Pickaxe**, as no concept of "Blunt Attacks" (a.k.a "Heavy Attacks") and "Poise" exists in Minecraft and are not easily addable with respect to other mods.

Unlike **Genshin Impact**, Dendro DMG is **not limited** to **2** per **0.5s**. This means that an entity can take multiple amounts of Dendro DMG in a short timeframe without the other's being ignored.

### Natural Element Sources

In **Origins: Genshin**, there are a couple of ways you can be applied with an element **naturally**!

When in or on fire, <span class="pyro">**Pyro**</span> is automatically applied on you!

This can be toggled with the `pyroFromFire` gamerule!

<div align="center">
	<video width="640" height="360" controls>
		<source src="../../../media/pyro_from_fire.mp4" type="video/mp4">
		Your browser does not support the video tag.
	</video>
</div>

<br>

When in water, <span class="hydro">**Hydro**</span> is automatically applied on you!

This can be toggled with the `hydroFromWater` gamerule!

<div align="center">
	<video width="640" height="360" controls>
		<source src="../../../media/hydro_from_water.mp4" type="video/mp4">
		Your browser does not support the video tag.
	</video>
</div>

<br>

When struck by lightning, <span class="electro">**Electro**</span> is automatically applied on you!

This can be toggled with the `electroFromThunder` gamerule!

<div align="center">
	<video width="640" height="360" controls>
		<source src="../../../media/electro_from_thunder.mp4" type="video/mp4">
		Your browser does not support the video tag.
	</video>
</div>