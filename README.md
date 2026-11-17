# Record-Implementation-of-Filters-Image-Smoothing-and-Sharpening-Using-OpenCV-

## Aim

To write a Python program using OpenCV to apply different smoothing filters (Averaging, Weighted Averaging, Gaussian, Median) and sharpening filters (Laplacian Kernel and Laplacian Operator) for image enhancement, and display each result separately along with the original image for comparison.

---

## The program performs the following operations:

- Read and display an input image  
- Apply Averaging filter  
- Apply Weighted Averaging filter  
- Apply Gaussian filter  
- Apply Median filter  
- Apply Laplacian sharpening using kernel  
- Apply Laplacian operator  
- Display all outputs for comparison  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (cv2)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image (e.g., `parrot.jpg`).

### Step 3:
Convert the image from BGR to RGB format for display.

### Step 4:
Apply Averaging Filter using `cv2.blur()`.

### Step 5:
Apply Weighted Averaging Filter using a custom kernel with `cv2.filter2D()`.

### Step 6:
Apply Gaussian Filter using `cv2.GaussianBlur()`.

### Step 7:
Apply Median Filter using `cv2.medianBlur()`.

### Step 8:
Apply Laplacian Sharpening using Kernel with `cv2.filter2D()`.

### Step 9:
Convert image to grayscale and apply Laplacian Operator using `cv2.Laplacian()`.

### Step 10:
Display all filtered images using a grid layout for comparison.

---
## Program
```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read Image
img = cv2.imread("parrot.jpg")

if img is None:
    print("Image not found!")
    exit()

# Convert to RGB
rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

# Averaging Filter
average = cv2.blur(rgb, (5,5))

# Weighted Averaging Filter
kernel = np.array([[1,2,1],
                   [2,4,2],
                   [1,2,1]], dtype=np.float32)
kernel = kernel / kernel.sum()
weighted = cv2.filter2D(rgb, -1, kernel)

# Gaussian Filter
gaussian = cv2.GaussianBlur(rgb, (5,5), 0)

# Median Filter
median = cv2.medianBlur(rgb, 5)

# Laplacian Sharpening Kernel
sharp_kernel = np.array([[0,-1,0],
                         [-1,5,-1],
                         [0,-1,0]])
lap_kernel = cv2.filter2D(rgb, -1, sharp_kernel)

# Laplacian Operator
gray = cv2.cvtColor(rgb, cv2.COLOR_RGB2GRAY)
lap_operator = cv2.Laplacian(gray, cv2.CV_64F)
lap_operator = np.uint8(np.absolute(lap_operator))

# Display Images
plt.figure(figsize=(15,10))

plt.subplot(2,4,1)
plt.imshow(rgb)
plt.title("Original")
plt.axis("off")

plt.subplot(2,4,2)
plt.imshow(average)
plt.title("Average Filter")
plt.axis("off")

plt.subplot(2,4,3)
plt.imshow(weighted)
plt.title("Weighted Average")
plt.axis("off")

plt.subplot(2,4,4)
plt.imshow(gaussian)
plt.title("Gaussian Filter")
plt.axis("off")

plt.subplot(2,4,5)
plt.imshow(median)
plt.title("Median Filter")
plt.axis("off")

plt.subplot(2,4,6)
plt.imshow(lap_kernel)
plt.title("Laplacian Kernel")
plt.axis("off")

plt.subplot(2,4,7)
plt.imshow(lap_operator, cmap="gray")
plt.title("Laplacian Operator")
plt.axis("off")

plt.tight_layout()
plt.show()
```

##  Developed By

- **Name: SIVANTH T** 
- **Register No: 212225240150** 

---

##  Output
<img width="392" height="300" alt="image" src="https://github.com/user-attachments/assets/c76971a6-1b75-4e2b-a60b-121a787c6e5a" />


### Smoothing Filters

- Averaging filter produces blurred image
<img width="390" height="287" alt="image" src="https://github.com/user-attachments/assets/8005ec73-7694-48aa-ae77-f9b3c7b1bae2" />


- Weighted averaging provides smoother result with less distortion
<img width="388" height="286" alt="image" src="https://github.com/user-attachments/assets/3fc82e05-6044-4828-8d06-2dbaf59b305c" />


- Gaussian filter preserves edges better while reducing noise
<img width="391" height="292" alt="image" src="https://github.com/user-attachments/assets/3ed7509b-34df-41a0-bdd3-b0ea522e6025" />


- Median filter removes salt-and-pepper noise effectively
<img width="383" height="277" alt="image" src="https://github.com/user-attachments/assets/65fedd3f-1ada-4226-afc5-8c47609a1d9e" />



###  Sharpening Filters

- Laplacian kernel enhances edges and fine details
<img width="385" height="276" alt="image" src="https://github.com/user-attachments/assets/a71d5aab-03fc-4fd2-841d-b6b4f60b60c3" />


- Laplacian operator detects edges clearly in grayscale  
<img width="390" height="290" alt="image" src="https://github.com/user-attachments/assets/f68f9a8a-c5a4-43da-8594-167e2b13a896" />


---

##  Result

Thus, smoothing filters and sharpening filters are successfully implemented using OpenCV.

The smoothing filters reduce noise and improve image quality, while sharpening filters enhance edges and details for better feature extraction.
