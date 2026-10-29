# Image-Handling-and-Pixel-Transformations-Using-OpenCV 

## AIM:
Write a Python program using OpenCV that performs the following tasks:

1) Read and Display an Image.  
2) Adjust the brightness of an image.  
3) Modify the image contrast.  
4) Generate a third image using bitwise operations.

## Software Required:
- Anaconda - Python 3.7
- Jupyter Notebook (for interactive development and execution)

## Algorithm:
### Step 1:
Load an image from your local directory and display it.

### Step 2:
Create a matrix of ones (with data type float64) to adjust brightness.

### Step 3:
Create brighter and darker images by adding and subtracting the matrix from the original image.  
Display the original, brighter, and darker images.

### Step 4:
Modify the image contrast by creating two higher contrast images using scaling factors of 1.1 and 1.2 (without overflow fix).  
Display the original, lower contrast, and higher contrast images.

### Step 5:
Split the image (boy.jpg) into B, G, R components and display the channels

## Program Developed By:
- **Name:** [Your Name Here]  
- **Register Number:** [Your Register Number Here]

  ### Ex. No. 01

#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```python
# YOUR CODE 
import cv2
import numpy as np
import matplotlib.pyplot as plt
img = cv2.imread("Eagle_in_Flight.jpg", cv2.IMREAD_GRAYSCALE)
```

#### 2. Print the image width, height & Channel.
```python
img.shape
```

#### 3. Display the image using matplotlib imshow().
```python
plt.imshow(img,cmap='gray')
plt.title("Gray Scale Image")
plt.axis("OFF")
plt.show()

```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```python
cv2.imwrite("img.png", img)
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
img1=cv2.imread("Eagle_in_Flight.jpg")
C_image=cv2.cvtColor(img1,cv2.COLOR_BGR2RGB)
plt.imshow(C_image,cmap='gray')

```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```python
C_image.shape

```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```python
eagle = C_image[20:410, 200:550]
plt.imshow(eagle)
plt.axis('off')
plt.show()

```

#### 8. Resize the image up by a factor of 2x.
```
eagle_2x = cv2.resize(eagle, None, fx=2, fy=2, interpolation=cv2.INTER_LINEAR)
plt.imshow(eagle_2x)
plt.axis('off')
plt.show()
```

#### 9. Flip the cropped/resized image horizontally.
```python
eagle_flip = cv2.flip(eagle_2x, 1)
plt.imshow(eagle_flip)
plt.axis('off')
plt.show()

```

#### 10. Read in the image ('Apollo-11-launch.jpg').
```python
img = cv2.imread('Apollo-11-launch.jpg')
plt.imshow(img[:, :, ::-1])
plt.show

```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```python
text = 'Apollo-11-launch'
font_face = cv2.FONT_HERSHEY_PLAIN
font_scale = 2
thickness = 2

(text_width, text_height), _ = cv2.getTextSize(text, font_face, font_scale, thickness)

x = (img.shape[1] - text_width) // 2
y = 700

cv2.putText(img, text, (x, y), font_face, font_scale, (255, 255, 255), thickness)

plt.imshow(img, cmap='gray')
plt.show()

```

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```python
cv2.rectangle(img, (490, 65), (690, 635), (255, 0, 255), 3)

plt.imshow(img, cmap='gray')
plt.show()


```

#### 13. Display the final annotated image.
```python
plt.imshow(img, cmap='gray')
plt.axis('off')
plt.show()

```

#### 14. Read the image ('Boy.jpg').
```python
img = cv2.imread('boy.jpg')
```

#### 15. Adjust the brightness of the image.
```python
brightness = 50
bright_img = cv2.convertScaleAbs(img, alpha=1, beta=brightness)

plt.imshow(cv2.cvtColor(bright_img, cv2.COLOR_BGR2RGB))
plt.axis('off')
plt.show()

```

#### 16. Create brighter and darker images.
```python
brighter = cv2.convertScaleAbs(img, alpha=1, beta=50)
darker = cv2.convertScaleAbs(img, alpha=1, beta=-50)

plt.imshow(cv2.cvtColor(brighter, cv2.COLOR_BGR2RGB))
plt.axis('off')
plt.show()

plt.imshow(cv2.cvtColor(darker, cv2.COLOR_BGR2RGB))
plt.axis('off')
plt.show()
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```python
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.axis('off')
plt.show()

plt.imshow(cv2.cvtColor(darker, cv2.COLOR_BGR2RGB))
plt.axis('off')
plt.show()

plt.imshow(cv2.cvtColor(brighter, cv2.COLOR_BGR2RGB))
plt.axis('off')
plt.show()
```

#### 18. Modify the image contrast.
```python
matrix1 = np.ones(img.shape) * 1.1
matrix2 = np.ones(img.shape) * 1.2
img_higher1 = cv2.multiply(img, 1.1)
img_higher2 = cv2.multiply(img, 1.2)
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```python
lower_contrast = cv2.convertScaleAbs(img, alpha=0.5, beta=0)
higher_contrast = cv2.convertScaleAbs(img, alpha=1.5, beta=0)
plt.figure(figsize=(12, 4))
plt.subplot(1, 3, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')
plt.subplot(1, 3, 2)
plt.imshow(cv2.cvtColor(lower_contrast, cv2.COLOR_BGR2RGB))
plt.title('Lower Contrast')
plt.axis('off')
plt.subplot(1, 3, 3)
plt.imshow(cv2.cvtColor(higher_contrast, cv2.COLOR_BGR2RGB))
plt.title('Higher Contrast')
plt.axis('off')
plt.show()
```

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```python
B, G, R = cv2.split(img)
plt.figure(figsize=(12, 4))
plt.subplot(1, 3, 1)
plt.imshow(B, cmap='gray')
plt.title('Blue Channel')
plt.axis('off')
plt.subplot(1, 3, 2)
plt.imshow(G, cmap='gray')
plt.title('Green Channel')
plt.axis('off')
plt.subplot(1, 3, 3)
plt.imshow(R, cmap='gray')
plt.title('Red Channel')
plt.axis('off')
plt.show()
```

#### 21. Merged the R, G, B , displays along with the original image
```python
merged = cv2.merge([B, G, R])
plt.figure(figsize=(8, 4))
plt.subplot(1, 2, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')
plt.subplot(1, 2, 2)
plt.imshow(cv2.cvtColor(merged, cv2.COLOR_BGR2RGB))
plt.title('Merged Image')
plt.axis('off')
plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```python
hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
H, S, V = cv2.split(hsv)
plt.figure(figsize=(12, 4))
plt.subplot(1, 3, 1)
plt.imshow(H, cmap='gray')
plt.title('Hue Channel')
plt.axis('off')
plt.subplot(1, 3, 2)
plt.imshow(S, cmap='gray')
plt.title('Saturation Channel')
plt.axis('off')
plt.subplot(1, 3, 3)
plt.imshow(V, cmap='gray')
plt.title('Value Channel')
plt.axis('off')
plt.show()
```
#### 23. Merged the H, S, V, displays along with original image.
```python
merged_hsv = cv2.merge([H, S, V])
plt.figure(figsize=(8, 4))
plt.subplot(1, 2, 1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title('Original Image')
plt.axis('off')
plt.subplot(1, 2, 2)
plt.imshow(cv2.cvtColor(merged_hsv, cv2.COLOR_HSV2RGB))
plt.title('Merged HSV Image')
plt.axis('off')
plt.show()

```

## Output:
- **i)** Read and Display an Image.  
- **ii)** Adjust Image Brightness.  
- **iii)** Modify Image Contrast.  
- **iv)** Generate Third Image Using Bitwise Operations.

## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

