## Bash scripting cheat sheet

### Pandas DataFrame + Hatches
```python
import matplotlib.pyplot as plt
import pandas as pd

HATCHES = ['/', '//', '///', '*', 'o']
data = {
    'key1': {
        'sub-key1': 10,
        'sub-key2': 10
    },
    'key2': {
        'sub-key1': 10,
        'sub-key2': 10
    },
}
fig, ax = plt.subplots()

data_df = pd.DataFrame(data).T

# Draw bar
data_df.plot(ax=ax, kind='bar', rot=0, edgecolor='black' colormap='Greys', legend=False)

# Draw hatches
bars = ax.patches
hatches = [p for p in HATCHES for i in range(len(data_df))]
for bar, hatch in zip(bars, hatches):
    bar.set_hatch(hatch)

# Update legend
ax.legend()
```