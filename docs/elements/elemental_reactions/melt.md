# Melt

[Elemental Reaction](../elemental_reactions.md)

Melt is the [Elemental Reaction](../elemental_reactions.md) triggered when <span class="pyro">**Pyro**</span> is applied onto an entity already affected by <span class="cryo">**Cryo**</span> or vice versa.

This reaction increases the damage of the <span class="pyro">**Pyro**</span> or <span class="cryo">**Cryo**</span> attack that triggered the reaction. If the reaction is triggered by a <span class="cryo">**Cryo**</span> attack, the damage is multiplied by **1.5**; If the reaction is triggered by a <span class="pyro">**Pyro**</span> attack, the damage is multiplied by **2**.

<div align="center">
	<video width="640" height="360" controls>
		<source src="../../../media/melt.mp4" type="video/mp4">
		Your browser does not support the video tag.
	</video>
</div>

### Internal Data
  
Reaction ID(s):

- `origins-genshin:melt_cryo` (triggered if <span class="cryo">**Cryo**</span> was applied on a <span class="pyro">**Pyro**</span> aura)
- `origins-genshin:melt_pyro-cryo` (triggered if <span class="pyro">**Pyro**</span> was applied on a <span class="cryo">**Cryo**</span> aura)
- `origins-genshin:melt_pyro-frozen` (triggered if <span class="pyro">**Pyro**</span> was applied on a <span class="cryo">**Freeze**</span> aura)