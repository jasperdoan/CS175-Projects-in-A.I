# Plotting images with MatpLotlib

Assume we have an image with PIL lib, and convert it to a numpy array

```py
imgplot = plt.figure()
```

Applying pseudocolor schemes to image plots

```py
# Shows pseudocolor scheme spectrum
lum_img = img[:, :, 0]
plt.imshow(lum_img)

# Shows Hot area of images
plt.imshow(lum_img, cmap="hot")
```

Full code:
```py
import matplotlib.pyplot as plt
from matplotlib.image import imread

###part1 - showing a color image with matplotlib
im = imread("robin.jpeg")
plt.imshow(im)
plt.title("My Little Bird")
plt.show()
print(im.shape)
print(im)

### part2 - sperating the channels and showing them in subplots
im = imread("robin.jpeg")
fig, axes = plt.subplots(1,3)
Rchannel = im[:,:,0]
Gchannel = im[:,:,1]
Bchannel = im[:,:,2]
axes[0].imshow(Rchannel,cmap='gray')
axes[0].set_title('Red Channel')
axes[1].imshow(Gchannel,cmap='gray')
axes[1].set_title('Green Channel')
axes[2].imshow(Bchannel,cmap='gray')
axes[2].set_title('Blue Channel')
plt.show()
```