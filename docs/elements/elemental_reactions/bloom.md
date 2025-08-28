# Bloom

[Elemental Reaction](../elemental_reactions.md)

Bloom is the [Elemental Reaction](../elemental_reactions.md) triggered when <span class="dendro">**Dendro**</span> is applied onto an entity already affected by <span class="hydro">**Hydro**</span> or vice versa.

This reaction produces a Dendro Core, which stays on the field for up to 6 seconds. Only 5 Dendro Cores can exist at a time in a **64m** radius, and producing more than 5 Dendro Cores will cause the oldest one to explode immediately.

## Dendro Core

Once a Dendro Core's duration expires, it explodes, dealing <span class="dendro">**AoE Dendro DMG**</span> in a **5m** radius to all entities.

<div align="center">
	<video width="640" height="360" controls>
		<source src="../../../media/bloom.mp4" type="video/mp4">
		Your browser does not support the video tag.
	</video>
</div>

When it receives <span class="pyro">**Pyro DMG**</span> or <span class="electro">**Electro DMG**</span>, the [Hyperbloom](#hyperbloom) and [Burgeon](#burgeon) Elemental Reactions can be triggered on the Dendro Core.

DMG dealt to the "owners" of all Bloom-related reactions are **5%** of the original DMG dealt. An entity is considered to have "owned" the core if they: triggered the **Bloom** reaction responsible for the Dendro Core or, if they triggered the secondary **Hyperbloom**/**Burgeon** reaction. A Dendro Core may have multiple entities as it's owner, where the DMG is attributed to the most recent owner.

### Internal Data

Reaction Multiplier: **2**  
Reaction ID(s): 

- `origins-genshin:bloom_dendro` (triggered if <span class="dendro">**Dendro**</span> was applied on a <span class="hydro">**Hydro**</span> aura)
- `origins-genshin:bloom_hydro` (triggered if <span class="hydro">**Hydro**</span> was applied on a <span class="dendro">**Dendro**</span> aura)
- `origins-genshin:bloom_quicken` (triggered if <span class="hydro">**Hydro**</span> was applied on a <span class="quicken">**Quicken**</span> aura)

## Hyperbloom

[Elemental Reaction](../elemental_reactions.md)

Hyperbloom is the [Elemental Reaction](../elemental_reactions.md) triggered on a [Dendro Core](#dendro-core) when it receives <span class="electro">**Electro DMG**</span>.

This reaction transforms the Dendro Core into a Sprawling Shot that homes in on the closest enemy within a **24m** radius, dealing increased <span class="dendro">**AoE Dendro DMG**</span> in a **1m** radius. If no enemy can be found, it shoots up and disappears shortly after.

<div align="center">
	<video width="640" height="360" controls>
		<source src="../../../media/hyperbloom.mp4" type="video/mp4">
		Your browser does not support the video tag.
	</video>
</div>

### Internal Data

Reaction Multiplier: **3**  
Reaction ID: `origins-genshin:hyperbloom`

## Burgeon

[Elemental Reaction](../elemental_reactions.md)

Burgeon is the [Elemental Reaction](../elemental_reactions.md) triggered on a [Dendro Core](#dendro-core) when it receives <span class="pyro">**Pyro DMG**</span>.

This reaction prematurely explodes the Dendro Core, dealing increased <span class="dendro">**AoE Dendro DMG**</span> in a **5m** radius.

<div align="center">
	<video width="640" height="360" controls>
		<source src="../../../media/burgeon.mp4" type="video/mp4">
		Your browser does not support the video tag.
	</video>
</div>

### Internal Data

Reaction Multiplier: **3**  
Reaction ID: `origins-genshin:burgeon`