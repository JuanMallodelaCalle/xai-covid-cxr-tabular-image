# Data

This repository does **not** redistribute the original COVID-19 chest X-ray dataset.

Download the dataset from the original source:

- <https://github.com/ieee8023/covid-chestxray-dataset>
- <https://www.kaggle.com/datasets/awsaf49/covid19-xray-dataset>

Recommended local structure:

```text
data/
└── covid-chestxray-dataset/
    ├── metadata.csv
    └── images/
```

The notebook may generate or expect a preprocessed image folder:

```text
data/covid-chestxray-dataset/images_preproc/
```

## Included files

### `artifact_annotations.csv`

Small manually created annotation file used during the project to flag non-lung artifacts such as:

- visible text overlays;
- medical devices.

This file is included because it was created as part of the project analysis and is not part of the original image dataset.

## Why the dataset is not included

The original dataset repository indicates that image-level licenses vary by image and are specified in `metadata.csv`. To avoid redistribution issues, this repository only provides code, documentation, and project-specific annotations.

Raw chest X-ray images, preprocessed X-ray images, and Grad-CAM overlays are not included in this repository.
