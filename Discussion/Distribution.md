# Distribution

This looks at the distribution of the whole dataset.

### Ratio based on radiation type
```py
import pandas as pd
import matplotlib.pyplot as plt
import numpy as np

### loading meta.csv table

table = pd.read_csv("../MiceNasa/train/meta.csv")

type1 = table[table['particle_type']=="X-ray"]
type2 = table[table['particle_type']=="Fe"]
count = [type1.size,type2.size]
mylabels = ["X-ray", "Fe"]
plt.pie(count,labels=mylabels)
plt.show()                      # Plot a pie chart ratio between Fe and X-ray
ratio = count/np.sum(count)
print(ratio)
```

### Distribution considering dose_Gy
```py
table.groupby('particle_type')['dose_Gy'].plot(kind='kde')
plt.xlabel('dose_Gy')
plt.legend(['Fe','X-ray'])
plt.show()
```

### Distribution considering hr_post_exposure
```py
# Grouping by particle_type
table.groupby('particle_type')['hr_post_exposure'].plot(kind='hist')
plt.xlabel('Hr Post Exposure')
plt.legend(['Fe','X-ray'])
plt.show()


# Don't group
table['hr_post_exposure'].plot(kind='hist')
plt.xlabel('Hr Post Exposure')
#plt.legend(['Fe','X-ray'])
plt.show()
```