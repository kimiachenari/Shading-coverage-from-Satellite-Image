

# 🌳 Urban Shading Analysis from Satellite Imagery

This project analyzes shading coverage in urban environments using satellite imagery and OpenCV in Python. The goal is to quantify shaded areas—typically from trees or tall structures—based on pixel intensity, and visualize both the binary shading map and the histogram of shading distribution.

## 🛰 Overview

The process involves:

* Reading a grayscale satellite image.
* Converting pixel values into a histogram to observe brightness and shading patterns.
* Applying a thresholding method to extract shaded regions.
* Plotting histograms and cumulative distribution functions (CDF) for comparison.

The code is suitable for:

* Urban climate analysis
* Urban heat island studies
* Public space thermal comfort analysis
* Environmental and sustainability research

### 📊 Sample Output
![light abstract](https://github.com/user-attachments/assets/89d1c45a-cc43-41ff-a0d2-4cc285366045)

## 🧰 Installation

Run this in Google Colab or your Python environment with the following libraries:

```python
pip install numpy opencv-python matplotlib
```

## 🧪 Code Usage

```python
import numpy as np
import cv2 as cv
from matplotlib import pyplot as plt

# Load grayscale satellite image
img1 = cv.imread('path/to/satellite_image.tif', 0)

# Plot histogram
plt.hist(img1.ravel(), bins=256, range=(5, 250), fc='k', ec='k')

# Vertical threshold line (example at pixel value 135)
plt.vlines(x=135, ymin=0, ymax=70000, colors='r')
plt.title("Mashhad, Iran")
plt.show()
```

### (Optional) Plot CDF and Histogram Together:

```python
hist, bins = np.histogram(img1.flatten(), 256, [0,256])
cdf = hist.cumsum()
cdf_normalized = cdf * float(hist.max()) / cdf.max()

plt.plot(cdf_normalized, color='b')
plt.hist(img1.flatten(), 256, [0,256], color='r')
plt.xlim([0,256])
plt.legend(('cdf','histogram'), loc='upper left')
plt.show()
```

