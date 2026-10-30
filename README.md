# Experiment: 6 Edge-detection-opencv
## Aim
To perform edge detection using Sobel, Roberts, Prewitt, Laplacian, and Canny edge detectors.

## Software Required
* Anaconda – Python 3.7
* Jupyter Notebook / VS Code
* OpenCV (cv2)
* NumPy
* Matplotlib

## Algorithm
### Step 1:
Import all the necessary modules for the program.

### Step 2:
Load an image using cv2.imread().

### Step 3:
Convert the image to grayscale.

### Step 4:
Apply Sobel operator using OpenCV to detect edges.

### Step 5:
Apply Prewitt operator using custom kernels.

### Step 6:
Apply Roberts operator using custom kernels.

### Step 7:
Apply Laplacian operator using OpenCV.

### Step 8:
Apply Canny edge detector using OpenCV.

### Step 9:
Display all edge-detected images for comparison.

## Program
```python
'''
Developed By
Name: SUJITH A
Register No: 212224230278
'''
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread(r"C:\Users\ADMIN\Downloads\DSC_0469.jpg")  # Replace with your image path
gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)
# Original Image
plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')

sobel_x = cv2.Sobel(gray_image, cv2.CV_64F, 1, 0, ksize=5)  # Sobel in x direction
sobel_y = cv2.Sobel(gray_image, cv2.CV_64F, 0, 1, ksize=5)  # Sobel in y direction
sobel_combined = cv2.magnitude(sobel_x, sobel_y)  # Combine both directions
plt.imshow(sobel_combined, cmap='gray')
plt.title('Sobel Edge Detection')
plt.axis('off')

laplacian = cv2.Laplacian(gray_image, cv2.CV_64F)
plt.imshow(laplacian, cmap='gray')
plt.title('Laplacian Edge Detection')
plt.axis('off')

canny_edges = cv2.Canny(gray_image, 50, 150)
plt.imshow(canny_edges, cmap='gray')
plt.title('Canny Edge Detection')
plt.axis('off')


image = cv2.imread(r"C:\Users\ADMIN\Downloads\DSC_0469.jpg")

if image is None:
    print("Image not found. Check the image path.")
else:
    gray_image = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY)

    kernel_x = np.array([[1, 0],
                         [0, -1]])

    kernel_y = np.array([[0, 1],
                         [-1, 0]])

    roberts_x = cv2.filter2D(gray_image, cv2.CV_32F, kernel_x)
    roberts_y = cv2.filter2D(gray_image, cv2.CV_32F, kernel_y)

    roberts_edges = cv2.magnitude(roberts_x, roberts_y)

    plt.imshow(roberts_edges, cmap='gray')
    plt.title('Roberts Edge Detection')
    plt.axis('off')
    plt.show()
```
## Output
<img width="305" height="410" alt="download" src="https://github.com/user-attachments/assets/85dda24b-9bea-42ff-9bb5-944983eeb526" />

### Sobel Edge Detector

Detects edges in horizontal and vertical directions
Produces gradient-based edge map

<img width="305" height="410" alt="download" src="https://github.com/user-attachments/assets/de4fb2ec-def4-4bce-aedd-cfcb8329858e" />


### Roberts Edge Detector

Detects edges using diagonal gradients
Sensitive to noise

<img width="305" height="410" alt="download" src="https://github.com/user-attachments/assets/510c6440-d9cd-4186-9f08-eca778e17749" />

### Laplacian Edge Detector

Detects edges using second-order derivatives
Highlights rapid intensity changes

<img width="305" height="410" alt="download" src="https://github.com/user-attachments/assets/5a6553dc-7884-4cde-83dc-7074e700e633" />

### Canny Edge Detector

Multi-stage edge detection
Produces clean and thin edges

<img width="305" height="410" alt="download" src="https://github.com/user-attachments/assets/0fb5dd0b-d202-4f33-9bdd-ffbb301f18bb" />

## Result
Thus, edges are successfully detected using Sobel, Prewitt, Roberts, Laplacian, and Canny edge detection techniques. Each method highlights edges differently based on gradient and intensity variations, improving feature extraction and analysis.
