## BPS Mouse Data
- `meta.csv` format:
    + `P242_73665006707-A6_003_013_proj.tif , 0.82 , Fe, 4`
    + `P242_73665006707-A6_008_034_proj.tif , 0.82 , Fe, 4`
    + `P242_73665006707-A6_009_007_proj.tif , 0.82 , X-ray, 4`
- Microscopy and Medical Imaging
    + Files are usually in `.FITC` format
    + Our files has been cimpressed to `TIFF`
    + `uint16`: each pixel is represented by 16 bits or 2 bytes
        + Provides wider pixel range for finer details
        + Requires scaling following download `float32` and values between `0` and `1` for model
    + Microscopy images have been cropped to different sized

## Deep Learning Framework
- Provides high-level interface to build and train neural network
- Optimized to run computtations on GPUs or TPUS which can speed up training
- Faster training = faster experimentation
    + model architecture
    + hyperparameters
- Reproducibility
    + Randomness
    + Deterministic

## PyTorch
### Step 1
- You need to def how data is loaded --> has `__getitem__` and `__len__` methods
    + `__getitem__` returns a sample from the dataset given an index
        + Constructor associated with the data and label (or data alone if using unsupervised techniques)
    + `__len__` returns the size of the dataset
        + `dataset[idx]` will give you the *idx-th* image and its label
        + Returns a sample as a dictionary or returns 2 items as a tuple

### Step 2
- The Custom Dataset class instantiate:
    + Training Dataset
    + Validation Dataset
    + Test Dataset

### Step 3
- DataLoader class will instantiate:
    + Train dataloader
    + Validation dataloader
    + Test dataloader


### Overview
- Define:
    + shuffling
    + batch size
    + num_workers
```
Data class          DataLoader class
    |                       |
    | inits                 | inits
    |                       |
    v                       v
Training Data   --> Train dataloader
Validation Data --> Validation dataloader
Test Data       --> Test dataloader
```

### Library
- `torchAudio`: Audio Data
- `torchtext`: Text Data
- `torchvision`: Image Data
- etc...

### Formatting
- Efficiency
- Standardization
- Preprocessing


## The Pytorch `torch.utils.data.DataLoader` class
### Defining
- Customizes data loading order
- Performs automatic batching
- Can configure single and multi-process data loading
- Automatic memory pinning
- The most important argument of the Dartaloader constructor is the **dataset object** --> Key-Value *\<pair>* (`map`)

### Structuring
```
------------------------
torch.utils.data.Dataset
------------------------
{abstract} + __init__()
{abstract} + __getitem__()
{abstract} + __len__()
------------------------
            |
            |
            |
            v
------------------------
      CustomDataset
------------------------
+/- label_dir   : str
+/- label_fname : str
+/- image_dir   : str
+/- image_fname : str
+/- image       : np.ndarray
+/- transform   : torchvision.transforms 
                  (CALLABLE)
+ __init__()
+ __getitem__()
+ __len__()
------------------------
```

### Transforming
- Increase more data/examples of our data --> Increase robustness to variations in the data

- By specifying our image augmentations with transforms implemented as a callable class. Taking advantage of `torchvision.transforms.Compose`, stringing each of these transformations in a sequence using a list of Transforms objects
```py
transforms.Compose([Transf_1(), Transf_2(), ... ])
```

