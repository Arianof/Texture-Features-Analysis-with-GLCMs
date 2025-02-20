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

## Installation & Requirements

Ensure you have the required dependencies installed:

```bash
pip install numpy scikit-image matplotlib pillow requests
```

## Usage

Run the script in a Jupyter Notebook or Google Colab to execute the following steps:

### 1. Import Libraries

```python
from PIL import Image
import numpy as np
from skimage.feature import graycomatrix, graycoprops
from skimage.color import rgb2gray, rgba2rgb
import requests
import matplotlib.pyplot as plt
import matplotlib.image as mpimg
```

### 2. Download Images from Google Drive

Images are retrieved using Google Drive file IDs and saved locally.

```python
def get_file(url, name, format):
  response = requests.get(url)
  if response.status_code == 200:
      with open(f'{name}.{format}', 'wb') as f:
          f.write(response.content)
```

### 3. Display Images

Images are displayed using Matplotlib for visualization.

```python
fig, axs = plt.subplots(1, 3, figsize=(15, 5))
for ax, img, title in zip(axs, [circuit, periodic, random], ['Mixed', 'Periodic', 'Random']):
    ax.imshow(img)
    ax.set_title(title)
    ax.axis('off')
plt.show()
```

### 4. Generate GLCM Matrices

Convert images to grayscale and compute their **GLCM matrices**.

```python
smooth_gray = (255*rgb2gray(rgba2rgb(smooth))).astype(np.uint8)
glcm_smooth = graycomatrix(smooth_gray, distances=[2], angles=[0], levels=256, symmetric=True, normed=True)
```

### 5. Extract Texture Features

Statistical properties like contrast, homogeneity, energy, and correlation are extracted from the GLCM matrices.

```python
def run_graycoprops(glcm):
    stats = {}
    for prop in ['contrast', 'dissimilarity', 'homogeneity', 'energy', 'correlation']:
        stats[prop] = graycoprops(glcm, prop)[0, 0]
    return stats
```

### 6. Compare Textures

Extracted features are used to compare texture groups.

```python
print("Texture Comparison:")
print("Periodic Texture:", run_graycoprops(glcm_periodic))
print("Random Texture:", run_graycoprops(glcm_random))
```

## Results & Observations

- **Smooth textures** show high homogeneity and low contrast.
- **Rough and Random textures** have high contrast values, indicating more variations.
- **Periodic textures** exhibit structured repetition, leading to distinct correlation values.
- **Circuit (Mixed) textures** have features that blend characteristics of multiple categories.

## Future Improvements

- Implement different distance and angle values for GLCM computation.
- Apply machine learning models to classify textures based on extracted features.
- Extend the dataset to include more texture variations.

## Contributing

Feel free to fork this repository and improve upon the project! If you have suggestions or find issues, open an issue or submit a pull request.

## License

This project is open-source under the **MIT License**.

---

📌 **Author:** [Your Name]\
📌 **Contact:** [Your Email or GitHub Profile]\
📌 **Keywords:** Texture Analysis, GLCM, Image Processing, Python, skimage, Matplotlib



