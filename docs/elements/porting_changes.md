# Porting Changes

Due to the Elemental Combat in Origins: Genshin being split off as a seperate mod: [Seven Elements](https://modrinth.com/mod/seven-elements), there are a lot of changes that have been made and ones that you need to make to your origin powers.

## Wiki Split

The Origins: Genshin Documentation will now **only** cover the necessary additions it creates, and all references to the Elemental Combat system, as well as data pack guides have been moved and linked to the [Seven Elements Documentation](https://xrickastley.github.io/SevenElements/wiki/). 

Hyperlinks to the Seven Elements Documentation are marked with an *external link indicator*: "↗"

There is also a quick "Seven Elements Docs" section under the "Elements" group you can click in order to access the Seven Elements Documentation quickly.

## Identifiers

The mod split also changed a lot of IDs, putting emphasis on features from Seven Elements and features from Origins: Genshin.

### Origins Types

For Origins Types, such as Action Types, Condition Types and [Power Types](../types/power_types.md), both the `seven-elements` and `origins-genshin` namespace are accepted.

However, you are encouraged to use the `seven-elements` namespace over the `origins-genshin` namespace, especially when using this mod with [Origins: Math](https://modrinth.com/mod/origins-math), as the created [Resource-backed Factory](https://origins-math.readthedocs.io/en/latest/notes/resource_backed_fields/) will have an ID of the form `origins-math:seven-elements/` instead of both `origins-math:seven-elements/` and `origins-math:origins-genshin/`.

### Minecraft Types

For Minecraft Types such as Damage Types, Entity Types, and tags, all entries now use the `seven-elements` namespace instead of the `origins-genshin` namespace. 

!!! warning
	Some entries under the `origins-genshin` namespace will still exist to keep pseudo-backwards compatibility. However, these types will **not** have the same functionality as their `seven-elements` counterparts, and will be removed in a future update.

### Seven Elements Types

For Seven Elements Types such as Elemental Reactions, Internal Cooldown Types and Tags, all entries will undoubtedly use the `seven-elements` namespace instead of the `origins-genshin` namespace. 

It is also important to note that for Internal Cooldown Tags specifically, powers may still opt for the `origins-genshin` namespace. However, these tags are considered different from their `seven-elements` counterpart, as these two are different strings, and as a result, will **not** share ICD.

### Origins: Genshin Types

For Origins: Genshin Types such as [Sprites](../misc/sprites.md), Elemental Skill and Elemental Burst Definitions, all entries will undoubtedly still use the the `origins-genshin` namespace. 