# Histogram MatPlotLib

This shows the histogram / intensity of a single cell image.

### Picking the cell image
```py
import pandas as pd
import matplotlib.pyplot as plt
from matplotlib.image import imread
import numpy as np

table = pd.read_csv("../User/train/meta.csv")
filePath = "../User/train/"

index = 200
fname = table.iloc[index].filename
img = imread(filePath + '/' + fname)

plt.imshow(img) # Shows the image
plt.show()
```

### Plot histogram
```py
# Create intensity histogram
minPp = np.min(img)
maxPp = np.max(img)


# plt.hist(img.ravel(), bins=256, range=(minPp, maxPp), fc='k', ec='k')
# Or
histogram, bin_edges = np.histogram(img, bins=256, range=(minPp, maxPp))

plt.figure()
plt.title("Grayscale Histogram")
plt.xlabel("Grayscale Value")
plt.ylabel("Pixels")
plt.xlim([minPp, maxPp])
plt.plot(bin_edges[0:-1], histogram, width = 1) #plt.bar(bin_edges[0:-1], histogram, width = 1)
plt.show()
```