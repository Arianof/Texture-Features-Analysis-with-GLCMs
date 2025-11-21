# GLCM and Texture Feature Extraction

## Overview

This project analyzes image textures using the **Gray Level Co-occurrence Matrix (GLCM)**. GLCM is a statistical method for examining texture patterns by computing how frequently pairs of pixel intensities occur in an image. The extracted texture features help differentiate between different surface types.

## Features

- **Image Acquisition**: Downloads images from Google Drive.
- **Image Preprocessing**: Converts images to grayscale for analysis.
- **GLCM Computation**: Generates co-occurrence matrices for different textures.
- **Texture Feature Extraction**: Computes statistical properties such as contrast, homogeneity, energy, and correlation.
- **Comparative Analysis**: Groups images into categories and evaluates their texture characteristics.

## Dataset

The project analyzes five types of textures:

1. **Smooth**
2. **Rough**
3. **Circuit (Mixed)**
4. **Periodic**
5. **Random**

These images are retrieved from Google Drive and processed in Python.

## Results & Observations

- **Smooth textures** show high homogeneity and low contrast.
- **Rough and Random textures** have high contrast values, indicating more variations.
- **Periodic textures** exhibit structured repetition, leading to distinct correlation values.
- **Circuit (Mixed) textures** have features that blend characteristics of multiple categories.


