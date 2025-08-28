# Crystallize

[Elemental Reaction](../elemental_reactions.md)

Crystallize is the [Elemental Reaction](../elemental_reactions.md) triggered when <span class="geo">**Geo**</span> is applied onto an entity already affected by <span class="pyro">**Pyro**</span>/<span class="electro">**Electro**</span>/<span class="hydro">**Hydro**</span>/<span class="cryo">**Cryo**</span>.

Crystallize deals **no damage**. Instead, it generates a matching <span class="pyro">**Pyro**</span>, <span class="electro">**Electro**</span>, <span class="hydro">**Hydro**</span>, or <span class="cryo">**Cryo**</span> [Elemental Shard](#elemental-shard) in front of the entity that can be picked up to gain an elemental shield of the corresponding element.

*NOTE: Elemental Shards are still on the TODO list, and as such, do not exist in the mod yet. You can get a Crystallize Shield by using the `/eval <target> <element>` command*

<div align="center">
	<video width="640" height="360" controls>
		<source src="../../../media/crystallize.mp4" type="video/mp4">
		Your browser does not support the video tag.
	</video>
</div>

## Elemental Shard

Elemental Shards last on the field for 15 seconds, and can be picked up to gain an elemental shield of the corresponding element.

![Crystallize Shield](../../media/crystallize_shield.png)

Elemental Shards can only be picked up by the entity that triggered Crystallize for 7.5 seconds. After this duration, the Elemental Shard can be picked up by any entity, including the entity Crystallize was triggered on.

### Internal Data

Reaction ID(s): 

- `origins-genshin:crystallize_pyro` (triggered on the <span class="pyro">**Pyro**</span> aura)
- `origins-genshin:crystallize_hydro` (triggered on the <span class="hydro">**Hydro**</span> aura)
- `origins-genshin:crystallize_electro` (triggered on the <span class="electro">**Electro**</span> aura)
- `origins-genshin:crystallize_cryo` (triggered on the <span class="cryo">**Cryo**</span> aura)
- `origins-genshin:crystallize_frozen` (triggered on the <span class="cryo">**Freeze**</span> aura) 