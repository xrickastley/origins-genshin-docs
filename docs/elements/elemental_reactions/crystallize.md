# Crystallize

[Elemental Reaction](../elemental_reactions.md)

Crystallize is the [Elemental Reaction](../elemental_reactions.md) triggered when <span class="geo">**Geo**</span> is applied onto an entity already affected by <span class="pyro">**Pyro**</span>/<span class="electro">**Electro**</span>/<span class="hydro">**Hydro**</span>/<span class="cryo">**Cryo**</span>.

Crystallize deals **no damage**. Instead, it generates a matching <span class="pyro">**Pyro**</span>, <span class="electro">**Electro**</span>, <span class="hydro">**Hydro**</span>, or <span class="cryo">**Cryo**</span> [Elemental Shard](#elemental-shard) in front of the entity that can be picked up to gain an Crystallize Shield of the corresponding element.

*<del>NOTE: Elemental Shards are still on the TODO list, and as such, do not exist in the mod yet. You can get a Crystallize Shield by using the `/eval <target> <element>` command</del>*

The newest alpha has now added a Crystallize Shard entity, meaning that Crystallize Shields now generate with the reaction!

<div align="center">
	<video width="95%" height="auto" controls>
		<source src="../../../media/crystallize.mp4" type="video/mp4">
		Your browser does not support the video tag.
	</video>
</div>

## Elemental Shard

Elemental Shards last on the field for 15 seconds, and can be picked up to gain an Crystallize Shield of the corresponding element.

![Crystallize Shield](../../media/crystallize_shield.png)

Elemental Shards can only be picked up by the entity that triggered Crystallize for 7.5 seconds. After this duration, the Elemental Shard can be picked up by any entity, including the entity Crystallize was triggered on.

## Crystallize Shield

When taking damage, the Crystallize Shield nullifies DMG received and prevents you from taking knockback while it still has *health* left. Once it expires or is broken, you will receive DMG and knockback normally again.

If a Crystallize shield doesn't have enough health to nullify the DMG received, the excess DMG left is dealt to you. Excess DMG wil **not** apply knockback.

Shields made from the other elements (<span class="pyro">**Pyro**</span>, <span class="hydro">**Hydro**</span>, <span class="electro">**Electro**</span>, etc.) all have **250%** "effectiveness" against DMG from their corresponding element.

<span class="geo">**Geo**</span> Shields have **150%** "effectiveness" against DMG from their corresponding element.

For sister elements (<span class="cryo">**Frozen**</span>, <span class="quicken">**Quicken**</span>, <span class="pyro">**Burning**</span>), they also have **250%** "effectiveness" against DMG from their corresponding element. However, this does not apply to their correspoding parent elements, i.e. <span class="cryo">**Frozen**</span> only has **100%** effectiveness against <span class="cryo">**Cryo DMG**</span>, and likewise vice versa, i.e. <span class="cryo">**Cryo**</span> only has **100%** effectiveness against <span class="cryo">**Frozen DMG**</span>.

It is also important to note that you, under any circumstance, should **never** be taking DMG from sister elements in a normal playthrough.

A shield's "effectiveness" determines how well it absorbs DMG from that element. The DMG Crystallize Shields take is given by the formula below:

$$
\text{DMG Taken}_\text{Crystallize Shield} = \frac{\text{DMG Incoming}}{\text{% Element Bonus}}
$$

where \(\text{% Element Bonus} = \frac{\text{Effectiveness %}}{100}\).

For instance, when an <span class="electro">**Electro**</span> Crystallize Shield receives <span class="electro">**Electro DMG**</span>, it's only damaged by **40%** of the original <span class="electro">**Electro DMG**</span> \((\frac{1}{2.5} = 0.4)\). If it instead receives <span class="pyro">**Pyro DMG**</span>, it takes **100%** of the original <span class="pyro">**Pyro DMG**</span> \((\frac{1}{1} = 1)\).

If the damage exceeds the Crystallize Shield's health, the excess DMG is dealt to you, which is given by the formula below:

$$
\text{DMG Taken} = \text{DMG Taken}_\text{Excess} \times \text{% Element Bonus}
$$

The Crystallize Shield **does not** apply it's effectiveness on the excess DMG.

### Internal Data

Reaction Multiplier (Crystallize Shield Health): **6**  
Reaction ID(s): 

- `origins-genshin:crystallize_pyro` (triggered on the <span class="pyro">**Pyro**</span> aura)
- `origins-genshin:crystallize_hydro` (triggered on the <span class="hydro">**Hydro**</span> aura)
- `origins-genshin:crystallize_electro` (triggered on the <span class="electro">**Electro**</span> aura)
- `origins-genshin:crystallize_cryo` (triggered on the <span class="cryo">**Cryo**</span> aura)
- `origins-genshin:crystallize_frozen` (triggered on the <span class="cryo">**Freeze**</span> aura) 