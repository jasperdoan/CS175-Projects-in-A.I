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