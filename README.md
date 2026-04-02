# BBBC018 Cell Segmentation

A comprehensive cell segmentation project using pre-trained Cellpose models on the BBBC018 dataset. This repository demonstrates cell nuclei and actin segmentation from microscopy images with detailed performance metrics and comparative analysis.

## Overview

This project provides a complete pipeline for segmenting cells in microscopy images using the Cellpose deep learning framework. It includes:

- **Image preprocessing** with normalization and CLAHE enhancement
- **Multiple model comparison** (cyto and nuclei models)
- **Segmentation metrics** including IoU, AP, AR, and F1 scores
- **Detailed performance analysis** across different image modalities (DNA and actin)

## Dataset

- **Dataset**: BBBC018 - A publicly available benchmark dataset
- **Content**: Microscopy images with corresponding ground-truth segmentation masks
- **Image Types**: 
  - DNA images (nuclei staining)
  - Actin images (cytoplasm/filament staining)

## Features

### Image Preprocessing
- **Normalization**: Applied to all images for consistent intensity ranges
- **CLAHE (Contrast Limited Adaptive Histogram Equalization)**: Applied only to actin images to enhance contrast
- **Note**: CLAHE is intentionally excluded from DNA images as it enhances cytoplasm signals, which negatively impacts nuclei segmentation accuracy

### Model Evaluation
- Implements custom segmentation metrics computation
- Outlines are converted to masks for accurate metric calculation
- Evaluated metrics @  IoU threshold 0.5:
  - Average Precision (AP) 
  - Average Recall (AR) 
  - F1 Score

### Comparative Analysis
- Performance comparison across multiple Cellpose models
- Side-by-side visualization of results
- Metric comparison charts for DNA and actin segmentation

## Requirements

### Environment Setup

This project requires **two separate virtual environments** due to dependency conflicts:

#### Environment 1: Cellpose SAM (Latest Version)
For the latest Cellpose SAM models:
```bash
conda create -n cellpose-sam python=3.10
conda activate cellpose-sam
pip install cellpose torch torchvision
```

#### Environment 2: Cellpose Standard (Slightly Older Version)
For cyto and nuclei models:
```bash
conda create -n cellpose-standard python=3.10
conda activate cellpose-standard
pip install cellpose==3.1.1.2 torch torchvision
```

### Dependencies

Common dependencies (install in both environments):
- NumPy
- Pandas
- Matplotlib
- OpenCV (cv2)
- PyTorch/CUDA (for GPU acceleration)

## Usage

### 1. Prepare Data
Organize your microscopy images and corresponding ground-truth masks in the following structure:
```
data/
├── images/
│   ├── dna/
│   └── actin/
└── labels/
    ├── dna/
    └── actin/
```

### 2. Run the Notebook
```bash
# Activate the appropriate environment
conda activate cellpose-sam

# Launch Jupyter
jupyter notebook sample.ipynb
```

### 3. Execute Cells in Order
The notebook is organized into logical sections:
- Setup & Imports
- Image preprocessing
- Model inference
- Metric calculation
- Result visualization

## Results

The notebook generates:
- Segmentation visualizations for both DNA and actin images
- Performance metrics for each model
- Comparative bar charts showing:
  - Average Precision (AP)
  - Average Recall (AR)
  - F1 Scores
- Per-image and per-model statistics

## Model Comparison

The project evaluates multiple Cellpose models:
- **Nuclei Model**: Optimized for DNA/nuclei segmentation
- **Cyto Model**: Optimized for cytoplasm and actin filament segmentation
- **SAM-based Models**: Latest Segment Anything Model variants

## Citation

If you use this work, please cite:
- Cellpose: [Stringer et al., 2021](https://www.nature.com/articles/s41592-020-01018-z)
- BBBC018 Dataset: [Broad Bioimage Benchmark Collection](https://bbbc.broadinstitute.org/)

## References

- [Cellpose GitHub Repository](https://github.com/MouseLand/cellpose)
- [BBBC018 Dataset](https://bbbc.broadinstitute.org/BBBC018)
- [Broad Bioimage Benchmark Collection](https://bbbc.broadinstitute.org/)


## Author

Marouane Barati

## Contributing

Contributions are welcome! Please feel free to submit issues or pull requests.


### Virtual Environment Conflicts
If models fail to load, ensure you're using the correct environment for the model type:
- SAM models → `cellpose-sam` environment
- Cyto/Nuclei models → `cellpose-standard` environment

### Memory Issues
If you encounter out-of-memory errors, try:
- Reducing batch size
- Using smaller image patches
- Closing other GPU-consuming applications

## Contact

For questions or issues, please open an issue on GitHub or contact marwanbrt12@gmail.com.
