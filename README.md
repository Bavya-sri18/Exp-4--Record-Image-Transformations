# Exp-4--Record-Image-Transformations

## Aim

To write a Python program using OpenCV to perform various geometric transformations on an image.

The program performs the following operations:

- Image Translation  
- Image Scaling (Resizing)  
- Image Shearing  
- Image Reflection (Flipping)  
- Image Rotation  

##  Software Used

- Anaconda – Python 3.7  
- Jupyter Notebook / VS Code  
- OpenCV (`cv2`)  
- NumPy  
- Matplotlib  


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

### Developed By: BAVYA SRI B 
### Register No: 212224230034

```python
import cv2
import numpy as np
import matplotlib.pyplot as plt

image = cv2.imread(r"D:\Screenshots\Bavya.jpeg")

plt.imshow(cv2.cvtColor(image, cv2.COLOR_BGR2RGB))  
plt.title("Original Image")  
plt.axis('off')

tx, ty = 100, 50  
M_translation = np.float32([[1, 0, tx], [0, 1, ty]])  
translated_image = cv2.warpAffine(image, M_translation, (image.shape[1], image.shape[0]))

plt.imshow(cv2.cvtColor(translated_image, cv2.COLOR_BGR2RGB))  
plt.title("Translated Image")  
plt.axis('off')

fx, fy = 5.0, 2.0  
scaled_image = cv2.resize(image, None, fx=fx, fy=fy, interpolation=cv2.INTER_LINEAR)

plt.imshow(cv2.cvtColor(scaled_image, cv2.COLOR_BGR2RGB))
plt.title("Scaled Image")  
plt.axis('off')

shear_matrix = np.float32([[1, 0.5, 0], [0.5, 1, 0]])  
sheared_image = cv2.warpAffine(image, shear_matrix, (image.shape[1], image.shape[0]))

plt.imshow(cv2.cvtColor(sheared_image, cv2.COLOR_BGR2RGB))  
plt.title("Sheared Image") 
plt.axis('off')

reflected_image = cv2.flip(image, 2)

plt.imshow(cv2.cvtColor(reflected_image, cv2.COLOR_BGR2RGB)) 
plt.title("Reflected Image")  
plt.axis('off')

(height, width) = image.shape[:2] 
angle = 45  
center = (width // 2, height // 2)  
M_rotation = cv2.getRotationMatrix2D(center, angle, 1)  
rotated_image = cv2.warpAffine(image, M_rotation, (width, height))  

plt.imshow(cv2.cvtColor(rotated_image, cv2.COLOR_BGR2RGB))  
plt.title("Rotated Image")  
plt.axis('off')

x, y, w, h = 100, 100, 200, 150
cropped_image = image[y:y+h, x:x+w]

plt.imshow(cv2.cvtColor(cropped_image, cv2.COLOR_BGR2RGB)) 
plt.title("Cropped Image")  
plt.axis('off')

```
---

##  Output:

### Original Image

<img width="336" height="462" alt="image" src="https://github.com/user-attachments/assets/917bed77-99f8-4d8b-b891-4b9617798d45" />

### Image Translation

<img width="337" height="461" alt="image" src="https://github.com/user-attachments/assets/13a41c2c-55f4-4428-b9c1-8185f5449424" />

### Image Scaling

<img width="576" height="337" alt="image" src="https://github.com/user-attachments/assets/1a14d321-2c32-4b34-9438-aa3d6172ba85" />

### Image Shearing

<img width="327" height="455" alt="image" src="https://github.com/user-attachments/assets/bf47523f-189e-4229-a0d2-7254acc39f61" />

### Image Reflection

<img width="335" height="457" alt="image" src="https://github.com/user-attachments/assets/501cf6ae-a104-4689-bc7e-0d29b46a3696" />

### Image Rotation

<img width="325" height="450" alt="image" src="https://github.com/user-attachments/assets/870724f6-57c0-4457-b22d-46a1f5c4aab6" />

### Cropped Image

<img width="560" height="451" alt="image" src="https://github.com/user-attachments/assets/2e62a674-b2a3-4fc2-a270-7ee8ca75e52e" />


---

##  Result

Thus, various geometric transformations such as translation, scaling, shearing, reflection, and rotation are successfully performed using OpenCV. These transformations demonstrate how images can be spatially manipulated for different computer vision applications.
