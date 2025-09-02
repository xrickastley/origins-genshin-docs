# Burning

[Elemental Reaction](../elemental_reactions.md)

Burning is the [Elemental Reaction](../elemental_reactions.md) triggered when <span class="pyro">**Pyro**</span> is applied onto an entity already affected by <span class="dendro">**Dendro**</span> or vice versa.

This reaction deals <span class="pyro">**AoE Pyro DMG**</span> and applies 1 [gauge unit](../elements.md#elemental-auras-and-the-aura-tax) of <span class="pyro">**Pyro**</span> to all entities in a **1m** radius. This Pyro application has an [Internal Cooldown](../internal_cooldown.md) of 2 seconds. 

<div align="center">
	<video width="95%" height="auto" controls>
		<source src="../../../media/burning.mp4" type="video/mp4">
		Your browser does not support the video tag.
	</video>
</div>

### Internal Data

Reaction Multiplier: **0.25**  
Reaction ID(s): 

- `origins-genshin:burning`
- `origins-genshin:burning_quicken` (triggered on the <span class="quicken">**Quicken**</span> aura)