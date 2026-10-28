# Geometric Transformations Using OpenCV

---

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

---

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  

---

##  Algorithm

### Step 1:
Import the required libraries: OpenCV, NumPy, and Matplotlib.

### Step 2:
Read the input image in color mode.

### Step 3: Image Translation
- Create a translation matrix to shift the image  
- Move the image 50 pixels to the right and 80 pixels down  
- Apply transformation using `cv2.warpAffine()`  
- Display original and translated images  

### Step 4: Image Scaling
- Resize the image to 0.5× (downscale)  
- Resize the image to 2× (upscale)  
- Use `cv2.resize()`  
- Display original, downscaled, and upscaled images  

### Step 5: Image Shearing
- Create transformation matrices for:
  - Horizontal shearing  
  - Vertical shearing  
- Apply transformations using `cv2.warpAffine()`  
- Display original and sheared images  

### Step 6: Image Reflection
- Perform flipping using `cv2.flip()`:
  - Horizontal reflection  
  - Vertical reflection  
  - Both axes  
- Display all reflected images  

### Step 7: Image Rotation
- Create rotation matrices for:
  - 45° rotation  
  - 90° rotation  
- Use `cv2.getRotationMatrix2D()` and `cv2.warpAffine()`  
- Display original and rotated images  

---

##  Program

### Developed By:
**Name:** Ratnapala P  

### Register No:
212225100037
```

import cv2
import numpy as np
import matplotlib.pyplot as plt

# Read the input image
img = cv2.imread("parrot.jpg")

if img is None:
    print("Error: parrot.jpg not found!")
    exit()

# Convert BGR to RGB
img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

height, width = img.shape[:2]


# 1. IMAGE TRANSLATION
translation_matrix = np.float32([
    [1, 0, 50],
    [0, 1, 80]
])

translated = cv2.warpAffine(
    img, translation_matrix, (width, height)
)

plt.figure(figsize=(10, 5))

plt.subplot(1, 2, 1)
plt.imshow(img)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 2, 2)
plt.imshow(translated)
plt.title("Translated Image")
plt.axis("off")

plt.suptitle("Image Translation")
plt.tight_layout()
plt.show()


# 2. IMAGE SCALING
downscaled = cv2.resize(
    img, None, fx=0.5, fy=0.5
)

upscaled = cv2.resize(
    img, None, fx=2, fy=2
)

plt.figure(figsize=(12, 5))

plt.subplot(1, 3, 1)
plt.imshow(img)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 3, 2)
plt.imshow(downscaled)
plt.title("Downscaled Image (0.5x)")
plt.axis("off")

plt.subplot(1, 3, 3)
plt.imshow(upscaled)
plt.title("Upscaled Image (2x)")
plt.axis("off")

plt.suptitle("Image Scaling")
plt.tight_layout()
plt.show()


# 3. IMAGE SHEARING
horizontal_matrix = np.float32([
    [1, 0.5, 0],
    [0, 1, 0]
])

vertical_matrix = np.float32([
    [1, 0, 0],
    [0.5, 1, 0]
])

horizontal_shear = cv2.warpAffine(
    img, horizontal_matrix, (width, height)
)

vertical_shear = cv2.warpAffine(
    img, vertical_matrix, (width, height)
)

plt.figure(figsize=(12, 5))

plt.subplot(1, 3, 1)
plt.imshow(img)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 3, 2)
plt.imshow(horizontal_shear)
plt.title("Horizontal Shearing")
plt.axis("off")

plt.subplot(1, 3, 3)
plt.imshow(vertical_shear)
plt.title("Vertical Shearing")
plt.axis("off")

plt.suptitle("Image Shearing")
plt.tight_layout()
plt.show()


# 4. IMAGE REFLECTION
horizontal_flip = cv2.flip(img, 1)
vertical_flip = cv2.flip(img, 0)
both_flip = cv2.flip(img, -1)

plt.figure(figsize=(12, 7))

plt.subplot(2, 2, 1)
plt.imshow(img)
plt.title("Original Image")
plt.axis("off")

plt.subplot(2, 2, 2)
plt.imshow(horizontal_flip)
plt.title("Horizontal Reflection")
plt.axis("off")

plt.subplot(2, 2, 3)
plt.imshow(vertical_flip)
plt.title("Vertical Reflection")
plt.axis("off")

plt.subplot(2, 2, 4)
plt.imshow(both_flip)
plt.title("Both Axes Reflection")
plt.axis("off")

plt.suptitle("Image Reflection")
plt.tight_layout()
plt.show()


# 5. IMAGE ROTATION
center = (width // 2, height // 2)

rotation_45_matrix = cv2.getRotationMatrix2D(
    center, 45, 1.0
)

rotation_90_matrix = cv2.getRotationMatrix2D(
    center, 90, 1.0
)

rotated_45 = cv2.warpAffine(
    img, rotation_45_matrix, (width, height)
)

rotated_90 = cv2.warpAffine(
    img, rotation_90_matrix, (width, height)
)

plt.figure(figsize=(12, 5))

plt.subplot(1, 3, 1)
plt.imshow(img)
plt.title("Original Image")
plt.axis("off")

plt.subplot(1, 3, 2)
plt.imshow(rotated_45)
plt.title("Rotation by 45 Degrees")
plt.axis("off")

plt.subplot(1, 3, 3)
plt.imshow(rotated_90)
plt.title("Rotation by 90 Degrees")
plt.axis("off")

plt.suptitle("Image Rotation")
plt.tight_layout()
plt.show()


```

---

##  Output

### Image Translation
<img width="1907" height="698" alt="image" src="https://github.com/user-attachments/assets/741c389c-ca0c-4af9-a6b1-25dfb136a716" />

- Original image is displayed  
- Translated image (shifted right and down) is displayed  

### Image Scaling
<img width="1492" height="702" alt="image" src="https://github.com/user-attachments/assets/2c820b30-f5c6-4227-9116-6e145692212f" />

- Original image is displayed  
- Downscaled image (0.5×) is displayed  
- Upscaled image (2×) is displayed  

### Image Shearing
<img width="1492" height="708" alt="image" src="https://github.com/user-attachments/assets/4553da03-2a51-45b2-9771-bae782d2421c" />

- Original image is displayed  
- Horizontally sheared image is displayed  
- Vertically sheared image is displayed  

### Image Reflection
<img width="1917" height="1015" alt="image" src="https://github.com/user-attachments/assets/0fd20643-007f-4e5c-b332-bb6c86ad5127" />

- Original image is displayed  
- Horizontally flipped image is displayed  
- Vertically flipped image is displayed  
- Both-axis flipped image is displayed  

### Image Rotation
<img width="1492" height="700" alt="image" src="https://github.com/user-attachments/assets/6ac97651-eb9f-4a03-aa26-2bbbd99c5dd5" />

- Original image is displayed  
- 45° rotated image is displayed  
- 90° rotated image is displayed  

---

##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
