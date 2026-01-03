---
type: Zettel
title: Defensive Programming
description: null
modificationDate: 2024-11-14 22:40
tags: [coding]
coverImage: null
---

[LINK](https://www.practicaldatascience.org/html/defensive_programming.html)

```python
# Make sure everyone's GDP per capita estimates are positive:
assert (world['gdppcap08'] > 0).all()
```

Check var that should have no missing has no missing.

```python
assert pd.notnull(world['country']).all()
```

Check my unique identifier is actually unique.

```python
assert not world['country'].duplicated().any()
```

Make sure values of GDP Per Capita have a reasonable value.

```python
assert ((100 < world.gdppcap08) & (world.gdppcap08 < 100000)).all()
```

