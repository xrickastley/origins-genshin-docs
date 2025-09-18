# Frozen

[Elemental Reaction](../elemental_reactions.md)

Frozen is the [Elemental Reaction](../elemental_reactions.md) triggered when <span class="cryo">**Cryo**</span> is applied onto an entity already affected by <span class="hydro">**Hydro**</span> or vice versa.

Frozen by itself deals **no damage**. Instead, it applies a <span class="cryo">**Freeze**</span> aura and the "Frozen" Status Effect onto the target for a certain period of time.

When an entity with the <span class="cryo">**Freeze**</span> aura receives <span class="geo">**Geo DMG**</span> or is hit by an [Axe](https://minecraft.wiki/w/Axe) or [Pickaxe](https://minecraft.wiki/w/Pickaxe), the [**Shatter**](#shatter) reaction is triggered.

Inflicting <span class="pyro">**Pyro**</span>/<span class="electro">**Electro**</span>/<span class="hydro">**Anemo**</span> on a Freeze aura will consume it to trigger [Melt](./melt.md)/[Superconduct](./superconduct.md)/[Swirl](./swirl.md) respectively.

<div align="center">
	<video width="95%" height="auto" controls>
		<source src="../../../media/frozen.mp4" type="video/mp4">
		Your browser does not support the video tag.
	</video>
</div>

### Internal Data

Reaction ID: `origins-genshin:frozen`

## Shatter

Shatter is the [Elemental Reaction](../elemental_reactions.md) triggered when an entity affected by <span class="cryo">**Freeze**</span> receives <span class="geo">**Geo DMG**</span> or is hit by an [Axe](https://minecraft.wiki/w/Axe) or [Pickaxe](https://minecraft.wiki/w/Pickaxe).

Upon triggering Shatter, the <span class="cryo">**Freeze**</span> aura is removed. If Shatter was triggered by dealing <span class="geo">**Geo DMG**</span>, the <span class="geo">**Geo**</span> attack that dealt the damage will sustain no gauge deduction.	

Unlike **Genshin Impact**, Shatter has it's own *reaction text*!

<div align="center">
	<video width="95%" height="auto" controls>
		<source src="../../../media/shatter.mp4" type="video/mp4">
		Your browser does not support the video tag.
	</video>
</div>

### Internal Data

Reaction Multiplier: **3**  
Reaction ID(s):

- `origins-genshin:shatter` (triggered by being hit with an [Axe](https://minecraft.wiki/w/Axe) or [Pickaxe](https://minecraft.wiki/w/Pickaxe))
- `origins-genshin:shatter_geo` (triggered by receiving <span class="geo">**Geo DMG**</span>)

