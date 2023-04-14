# AWS Data set

### [Dataset](https://registry.opendata.aws/bps_microscopy/)

### [Installation](https://aws.amazon.com/cli/)

### Access
```bash
aws s3 ls --no-sign-request s3://nasa-bps-training-data/Microscopy/
```

### Code
```py
import pandas as pd
import matplotlib.pyplot as plt
from matplotlib.image import imread

# Loading meta.csv table

table = pd.read_csv("../MiceNasa/train/meta.csv")

print(table.head())

# Accessing different colomns in pandas, find the 
#   location of the row file based on the index
i = 100
print(table.iloc[i].filename)
print(table.iloc[i].dose_Gy)            # Dose in Gy (For example, 0.5 Gy)
print(table.iloc[i].particle_type)      # Particle type (For example, Fe, X-ray, etc.)
print(table.iloc[i].hr_post_exposure)   # Hours post exposure (For example, 0, 1, 2, 3, etc...)


# Showing sample images with matplotlib and cmaps
filepath = "../MiceNasa/train"
fname = table.iloc[i].filename

im = imread(filepath + "/" + fname)
plt.imshow(im,cmap='gray')
#plt.imshow(im,cmap='hot')

plt.show()      # Shows the image
print(im.shape) # Prints the shape of the image
```

Filter out data based on dose_Gy for example, 0.5 Gy
```py
# Filter out data based on dose_Gy for example, 0.5 Gy
table = table[table.dose_Gy == 0.5]
print(table.head())
```

Get data based on some requirements
```py
exp = table[table['hr_post_exposure'] >= 24]
print(exp)

part = table[table['particle_type'] == 'Fe']
print(part)
```
