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

Or you can do the following:
```py
import numpy as np
import matplotlib.pyplot as plt
import imageio.v3 as iio
import skimage
import skimage.draw
from PIL import Image

fname = "bird.jpeg"

image = Image.open(fname).convert("L")

plant_seedling = np.asarray(image)

plt.imshow(plant_seedling, cmap="gray", vmin=0, vmax=255)
plt.show()

histogram, bin_edges = np.histogram(plant_seedling, bins=256)

plt.figure()
plt.title("Grayscale Histogram")
plt.xlabel("grayscale value")
plt.ylabel("pixel count")

plt.plot(bin_edges[0:-1], histogram)  # <- or here

plt.show()
```