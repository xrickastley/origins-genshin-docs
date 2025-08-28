---
title: /element (Command)
---

# `/element`

The `/element` command can be used to check, add, remove and modify elements for an living entity.

### Syntax:

```mcfunction
element apply <target> <element> <gaugeUnits>
```

```mcfunction
element apply <target> <element> <gaugeUnits> gaugeUnit [isAura]
```

Applies the specified element to the specified target with the specified amount of [gauge units](../../elements/elements.md#elemental-gauge-theory).

- `<target>` being a target selector, username, or UUID; can only select one at a time.
    - (e.g: `@a[limit = 1]`, `@p`, `_xRickAstley`, `b1b981b6-4081-4abe-afd8-e79269c6a339`)
- `<element>` being the name of an element.
    - (e.g: `pyro`, `HYDRO`, `eLeCtRo`)
- `<gaugeUnits>` being a double (a decimal or whole number)
    - (e.g: `1`, `1.5`, `4`)
- `[isAura]` being a boolean that determines if the Elemental Application is considered an Aura Element. Elements that cannot be Aura Elements will ignore `true`, defaults to `true`.
	- (e.g: `true`, `false`)

<br>

```mcfunction
element apply <target> <element> <gaugeUnits> duration <duration>
```

Applies the specified element to the specified target with the specified amount of [gauge units](../../elements/elements.md#elemental-gauge-theory) that lasts for a maximum of the specified duration, in ticks.

- `<target>` being a target selector, username, or UUID; can only select one at a time.
    - (e.g: `@a[limit = 1]`, `@p`, `_xRickAstley`, `b1b981b6-4081-4abe-afd8-e79269c6a339`)
- `<element>` being the name of an element.
    - (e.g: `pyro`, `HYDRO`, `eLeCtRo`)
- `<gaugeUnits>` being a double (a decimal or whole number)
    - (e.g: `1`, `1.5`, `4`)
- `<duration>` being a integer (a whole number)	

<br>

```mcfunction
element remove <target> <element>
```

Removes the specified element from the specified target.

- `<target>` being a target selector, username, or UUID; can only select one at a time.
    - (e.g: `@a[limit = 1]`, `@p`, `_xRickAstley`, `b1b981b6-4081-4abe-afd8-e79269c6a339`)
- `<element>` being the name of an element.
    - (e.g: `pyro`, `HYDRO`, `eLeCtRo`)

<br>

```mcfunction
element reduce <target> <element> <gaugeUnits>
```

Reduces the specified element of the specified target with the specified amount of [gauge units](../../elements/elements.md#elemental-gauge-theory).

- `<target>` being a target selector, username, or UUID; can only select one at a time.
    - (e.g: `@a[limit = 1]`, `@p`, `_xRickAstley`, `b1b981b6-4081-4abe-afd8-e79269c6a339`)
- `<element>` being the name of an element.
    - (e.g: `pyro`, `HYDRO`, `eLeCtRo`)
- `<gaugeUnits>` being a double (a decimal or whole number)
    - (e.g: `1`, `1.5`, `4`)

<br>

```mcfunction
element query <target>
```

Queries the elements currently on specified target.

- `<target>` being a target selector, username, or UUID; can only select one at a time.
    - (e.g: `@a[limit = 1]`, `@p`, `_xRickAstley`, `b1b981b6-4081-4abe-afd8-e79269c6a339`)

<br>

```mcfunction
element query <target> [element]
```

Queries the specified element of the specified target.

- `<target>` being a target selector, username, or UUID; can only select one at a time.
    - (e.g: `@a[limit = 1]`, `@p`, `_xRickAstley`, `b1b981b6-4081-4abe-afd8-e79269c6a339`)
- `[element]` being the name of an element.
    - (e.g: `pyro`, `HYDRO`, `eLeCtRo`)