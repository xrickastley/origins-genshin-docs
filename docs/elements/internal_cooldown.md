# Internal Cooldown

**Internal Cooldown**, commonly abbreviated as **ICD**, is a game mechanic that regulates how often an ability can apply an element onto an entity.

## Overview

Internal Cooldown is handled by two properties: the **reset interval** and the **gauge sequence**, commonly denoted as: **(ResetInterval)s/(GaugeSequence) hits**.

For an Element to be applied by the same ability, either:  

- The time from the previous Elemental Application to this Elemental Application exceeds the Internal Cooldown's **reset interval**, or
- The amount of "hits" from this ability that attempted to apply an Element exceeds the Internal Cooldown's **gauge sequence**.

If any of these conditions are fulfilled, the Internal Cooldown is considered to be inactive, allowing the Element to be applied.

It is also important to note that:

- The first hit after the **gauge sequence** applies an element, but does **not** clear the timer given by the **reset interval**.
- The first hit after the **reset interval** applies an element **and** clears both the timer given by the **reset interval** and the **gauge sequence**.

In simpler terms, clearing the **gauge sequence** allows you to apply an element without clearing the **reset interval**, effectively "sneaking in" an Elemental application, rewarding fast attackers. Slower attackers unable to clear the **gauge sequence** in time rely instead on the **reset interval**.

Most abilities in Genshin Impact follow the standard ICD of **2.5s**/**3** hits, represented in Origins: Genshin as `origins-genshin:default`. Elemental Attacks that have a cooldown may also choose to have no ICD, represnted in Origins: Genshin as `origins-genshin:none`.

Internal Cooldown is based on the attack's **tag** and **type**, as well as the **entity** that dealt the damage. Attacks from the same entity that share the same **tag** and **type** will share ICD.