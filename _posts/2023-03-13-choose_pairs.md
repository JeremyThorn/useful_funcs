---
title: "choose_pairs"
date: 2021-03-13
---

```python
def pick_pairs(a, n):
    I = np.arange(0, len(a),dtype=int)
    available_partners = [[False if j == i else True for j in I] for i in I]
    pairs = np.empty(shape=(n,2),dtype=int)
    available_I = [True for i in I]
    for ni in range(n):
        p1 = rng.choice(I[available_I])
        p2 = rng.choice(I[available_partners[p1]])
        available_partners[p1][p2] = False
        available_I[p1] = np.any(available_partners[p1])
        available_partners[p2][p1] = False
        available_I[p2] = np.any(available_partners[p2])
        pairs[ni,:] = [p1, p2]
    return np.array([a[pair] for pair in pairs])
```
