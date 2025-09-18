# Bi-entity Action Types

Bi-entity Action Types operate on a `Pair<Entity, Entity>`; in simpler terms: an actor and a target. The actor and target is determined depending on the used power type, and can be swapped using [Invert](https://origins.readthedocs.io/en/latest/types/bientity_action_types/invert/). These are available to power/action types that provides a `bientity_action` object field.

As a rule of thumb, the actor is usually the entity that "triggers" the action (e.g. uses or attacks another entity), while the target is the entity that is being targeted (e.g. the entity that is being used or attacked).

### List
- [Elemental Damage](./bientity_action_types/elemental_damage.md)

### [Origins Bi-entity Action Types](https://origins.readthedocs.io/en/latest/types/bientity_action_types/)