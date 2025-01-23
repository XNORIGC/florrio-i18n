# Florr.io translation files

As a rough guide, doing `{#key}` will fetch another key in the translation files of the same language. It can be nested. `{0}` will get replaced by whatever argument that is. Some (like mob types, petal types) accept a separate argument to know what to fetch in that argument, or how to format it. For example, a petal argument 0 can print its rarity (common/unusual/etc) using `{0:rarity}`, or its internal name with `{0:base}` (cactus, rose, magic_stinger etc.)

An example of how rarities are done in English:
```
Rarities/rare/Name=Rare
[...]

UI/Petal/Rarity={#Rarities/{0:rarity}/Name}
```

In Portuguese, you'd need to take into account the gender:

```
Rarities/rare/Name/Female=Rara
Rarities/rare/Name/Male=Rara
[...]
Petals/rose/Gender=Female
[...]

UI/Petal/Rarity={#Rarities/{0:rarity}/Name/{#Petals/{0:base}/Gender}}
```

## Argument types

### Numbers
- `{0}` Will print raw
- `{0:tooltip}` Will be print in tooltip form (like 2.2k)
- `{0:timeLeft}` Will be print as a "time left" timestamp. Assumes number is in seconds. It'll transform into something like `in X seconds` or `in 3 hours` for larger numbers.

### String
- `{0}` Will print in escaped form (< will turn into &lt;, > will turn into &gt;, etc.). This is mostly used when printing player names or other user text, to prevent them from using colors
- `{0:raw}` Will print raw

### Mob Type
- `{0:base}` Will print the internal id (rock/cactus/wasp_hel)
- `{0:rarity}` Will print the rarity (common/unusual/rare/etc)

### Mob Base Type
- `{0}` Will print the internal id (rock/cactus/wasp_hel)

### Mob Rarity
- `{0}` Will print the rarity (common/unusual/rare/etc)

### Petal Type
- `{0:base}` Will print the internal id (rock/cactus/magic_stinger)
- `{0:rarity}` Will print the rarity (common/unusual/rare/etc)

### Petal Base Type
- `{0}` Will print the internal id (rock/cactus/magic_stinger)

### Petal Rarity
- `{0}` Will print the rarity (common/unusual/rare/etc)
