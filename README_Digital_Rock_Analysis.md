# Digital Rock Analysis

This repository contains a collection of Jupyter notebooks for **digital rock image analysis**, with emphasis on pore-space segmentation, pore-property extraction, connectivity analysis, tortuosity estimation, clustering methods, image filtering, and synthetic sample generation.

The notebooks were developed as experimental workflows for analyzing 2D and 3D rock images, especially micro-CT or segmented porous-media images. The repository combines classical image processing, machine learning, deep learning, and numerical approaches for extracting quantitative pore-network information.

---

## Main Objectives

The main goals of this project are to:

- Segment pore and grain regions from digital rock images.
- Estimate petrophysical and geometrical properties such as porosity, pore area, grain area, grain fraction, and pore-size-related descriptors.
- Analyze pore connectivity using clustering and graph-based approaches.
- Estimate tortuosity from pore pathways and connectivity structures.
- Test clustering methods such as K-Means, Gaussian Mixture Models, and DBSCAN for pore-region separation.
- Validate pore-property extraction using threshold-based segmentation, CNN-based segmentation, and CNN/U-Net-based segmentation.
- Generate and test synthetic 2D and 3D porous samples using deep learning and image-processing workflows.
- Explore filtering and reconstruction methods such as Radon transform, filtered back projection, Gaussian filters, Laplacian filters, and signal-to-noise analysis.

---

## Repository Structure

| File | Description |
|---|---|
| `Cluster_to_ratio_of_aspect.ipynb` | Initial workflow for loading rock images, segmenting regions, applying K-Means clustering, and calculating aspect ratios. |
| `Cluster_to_ratio_of_aspect_final.ipynb` | Extended version including clustering, aspect-ratio analysis, and CNN-based pore classification experiments. |
| `Connectivity_Network_tests.ipynb` | Tests for pore connectivity using clustering methods, shape criteria, contour analysis, and connectivity algorithms. |
| `Filter_Back_projection-checkpoint.ipynb` | Experiments with Radon transform, inverse Radon transform, filtering, reconstruction, and SNR analysis. |
| `Generate_2d_and_3d_Samples.ipynb` | Workflows for generating synthetic porous samples using diffusion-like processes, DCGAN, CGAN, and denoising models. |
| `Pore_DL_extraction_properties - validation CNN.ipynb` | Validation of pore-property extraction using CNN-based segmentation. |
| `Pore_DL_extraction_properties - validation CNN-U_net.ipynb` | Validation of pore-property extraction using CNN/U-Net-based segmentation. |
| `Pore_DL_extraction_properties - validation-Thresold.ipynb` | Validation of pore-property extraction using threshold-based segmentation. |
| `Pore_connectivity_cluster.ipynb` | Analysis of pore connectivity, clustering, aspect ratio, pore area, number of connections, and tortuosity. |
| `Pore_image_connectivity_analysis_1.ipynb` | Basic pore-image connectivity analysis using clustering and pore-property descriptors. |
| `Pore_tortuosity.ipynb` | Tortuosity estimation from synthetic and real pore images using path-based methods and BFS. |
| `Testing.ipynb` | Development and testing notebook for connectivity, clustering, watershed, graph construction, and path analysis. |
| `Testing_tortuosity_code.ipynb` | Testing notebook focused on tortuosity and connectivity algorithms. |
| `Tortuosity_with_cluster.ipynb` | Tortuosity estimation based on clustered pore regions and void-space path analysis. |

---

## General Workflow

A typical workflow in this repository follows these steps:

1. **Load a rock image**
   - Read grayscale or binary images using OpenCV, PIL, or scikit-image.

2. **Preprocess the image**
   - Convert to grayscale.
   - Normalize pixel values.
   - Apply thresholding or binary conversion.
   - Optionally apply filters or morphological operations.

3. **Segment pore and grain regions**
   - Use threshold-based segmentation, CNN-based segmentation, or CNN/U-Net segmentation.

4. **Extract pore properties**
   - Calculate porosity, grain fraction, pore area, grain area, and volume-related properties.

5. **Apply clustering**
   - Use K-Means, Gaussian Mixture Models, or DBSCAN to separate pore regions and analyze pore structures.

6. **Analyze connectivity**
   - Identify connected regions, contours, cluster centers, and possible pore pathways.

7. **Estimate tortuosity**
   - Calculate path length between connected pore regions and compare it with the straight-line distance.
   - Some notebooks use Breadth-First Search and `route_through_array` from scikit-image.

8. **Validate results**
   - Compare threshold, CNN, and CNN/U-Net results using porosity curves, area measurements, and similarity metrics.

---

## Installation

Clone the repository:

```bash
git clone https://github.com/your-username/Digital-Rock-Analysis.git
cd Digital-Rock-Analysis
```

Create and activate a Python environment:

```bash
python -m venv .venv
source .venv/bin/activate      # Linux/macOS
# .venv\Scripts\activate     # Windows
```

Install the main dependencies:

```bash
pip install numpy scipy matplotlib opencv-python pillow scikit-image scikit-learn tensorflow imageio tifffile porespy jupyter
```

Then open Jupyter Notebook:

```bash
jupyter notebook
```

---

## Main Dependencies

The notebooks use the following Python libraries:

- `numpy`
- `scipy`
- `matplotlib`
- `opencv-python`
- `Pillow`
- `scikit-image`
- `scikit-learn`
- `tensorflow`
- `porespy`
- `imageio`
- `tifffile`
- `jupyter`

Some notebooks may require additional libraries depending on the specific experiment.

---

## Input Data

Some notebooks expect local image files such as:

- `PirabasB_2 - Copy.tif`
- `porous_material.tiff`
- `porous_material (1).tiff`
- `slice0330.tif`

These files are not necessarily included in the repository. Before running the notebooks, place your own rock-image data in the working directory or update the image paths inside each notebook.

Recommended data organization:

```text
Digital-Rock-Analysis/
│
├── data/
│   ├── raw/
│   ├── processed/
│   └── synthetic/
│
├── results/
│   ├── figures/
│   ├── metrics/
│   └── segmented_images/
│
└── notebooks/
```

At the moment, the repository is organized mainly as standalone notebooks. Future versions can be reorganized into `data/`, `notebooks/`, `src/`, and `results/` folders.

---

## Example Usage

Open one of the notebooks, for example:

```bash
jupyter notebook Pore_tortuosity.ipynb
```

Then follow the notebook cells to:

1. Load an image.
2. Convert it to a binary pore/grain image.
3. Cluster pore regions.
4. Identify pore pathways.
5. Estimate tortuosity.
6. Plot and analyze the results.

For deep learning workflows, start with the validation notebooks:

```text
Pore_DL_extraction_properties - validation CNN.ipynb
Pore_DL_extraction_properties - validation CNN-U_net.ipynb
Pore_DL_extraction_properties - validation-Thresold.ipynb
```

---

## Methods Included

This repository includes experiments with:

- Threshold-based segmentation
- CNN segmentation
- CNN/U-Net segmentation
- K-Means clustering
- Gaussian Mixture Models
- DBSCAN clustering
- Pore aspect-ratio analysis
- Pore and grain area estimation
- Porosity estimation
- Riemann-sum-based volume estimation
- Pore connectivity analysis
- Tortuosity estimation
- Breadth-First Search path analysis
- Radon transform and inverse Radon transform
- Filtered back projection
- Deep Convolutional GANs
- Conditional GANs
- Synthetic porous-media generation

---

## Notes on Reproducibility

Some notebooks include random processes, especially those related to clustering, synthetic image generation, and deep learning. For reproducible results, set random seeds before running the workflows.

Example:

```python
import random
import numpy as np
import tensorflow as tf

seed = 42
random.seed(seed)
np.random.seed(seed)
tf.random.set_seed(seed)
```

Results may vary depending on image resolution, segmentation quality, clustering parameters, and the selected pore-connectivity criteria.

---

## Suggested Future Improvements

Possible improvements for future versions include:

- Reorganize the repository into `src/`, `notebooks/`, `data/`, and `results/` folders.
- Add a `requirements.txt` or `environment.yml` file.
- Convert repeated functions into reusable Python modules.
- Add example input images or small synthetic datasets.
- Add documentation for each notebook workflow.
- Add unit tests for pore-property and tortuosity functions.
- Add comparison tables for threshold, CNN, and CNN/U-Net results.
- Include citation information for datasets and methods used.

---

## Author

Developed for research and experimentation in digital rock physics, pore-network characterization, image processing, and machine learning applied to geosciences.

---

## License

No license file is currently included. If this repository will be shared publicly, consider adding an open-source license such as MIT, Apache-2.0, or GPL-3.0.
