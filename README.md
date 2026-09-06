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

  ### Ex. No. 01

#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
```python
import cv2
import matplotlib.pyplot as plt

img = cv2.imread("Eagle_in_Flight.jpg.jpg", cv2.IMREAD_GRAYSCALE)

if img is None:
    print("Image not found.")
else:
    plt.imshow(img, cmap="gray")
    plt.axis("off")
    plt.show()
```

#### 2. Print the image width, height & Channel.
```python
import cv2
img = cv2.imread("Eagle_in_Flight.jpg.jpg")
if img is None:
    print("Error: Unable to load the image.")
else:
    height, width, channels = img.shape
    print("Width :", width)
    print("Height:", height)
    print("Channels:", channels)
```

#### 3. Display the image using matplotlib imshow().
```python
import cv2
import matplotlib.pyplot as plt
img = cv2.imread("Eagle_in_Flight.jpg.jpg")
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
plt.imshow(img_rgb)
plt.title("Image Display")
plt.axis("off")  
plt.show()
```

#### 4. Save the image as a PNG file using OpenCV imwrite().
```python
import cv2
img = cv2.imread("Eagle_in_Flight.jpg.jpg")
if img is None:
    print("Error: Unable to load the image.")
else:
    cv2.imwrite("Eagle_in_Flight.png", img)
    print("Image saved successfully as 'Eagle_in_Flight.png'.")
```

#### 5. Read the saved image above as a color image using cv2.cvtColor().
```python
import cv2
import matplotlib.pyplot as plt
img = cv2.imread("Eagle_in_Flight.png", cv2.IMREAD_GRAYSCALE)
color_img = cv2.cvtColor(img, cv2.COLOR_GRAY2BGR)
plt.imshow(cv2.cvtColor(color_img, cv2.COLOR_BGR2RGB))
plt.title("Color Image")
plt.axis("off")
plt.show()
```

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
```python
import cv2
import matplotlib.pyplot as plt
img = cv2.imread("Eagle_in_Flight.png")
color_img = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
height, width, channels = img.shape
print("Width :", width)
print("Height:", height)
print("Channels:", channels)
plt.imshow(color_img)
plt.title("Eagle in Flight - Colour Image")
plt.axis("off")
plt.show()
```

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
```python
import cv2
import matplotlib.pyplot as plt
img = cv2.imread("Eagle_in_Flight.png")
cropped = img[100:600, 200:900]
cropped_rgb = cv2.cvtColor(cropped, cv2.COLOR_BGR2RGB)
plt.imshow(cropped_rgb)
plt.title("Cropped Eagle")
plt.axis("off")
plt.show()
```

#### 8. Resize the image up by a factor of 2x.
```python
import cv2
import matplotlib.pyplot as plt
img = cv2.imread("Eagle_in_Flight.png")
resized = cv2.resize(img, None, fx=2, fy=2, interpolation=cv2.INTER_LINEAR)
resized_rgb = cv2.cvtColor(resized, cv2.COLOR_BGR2RGB)
plt.imshow(resized_rgb)
plt.title("Resized Image (2x)")
plt.axis("off")
plt.show()
```

#### 9. Flip the cropped/resized image horizontally.
```python
import cv2
import matplotlib.pyplot as plt
img = cv2.imread("Eagle_in_Flight.jpg.jpg")
cropped = img[100:600, 200:900]
flipped = cv2.flip(cropped, 1)
flipped_rgb = cv2.cvtColor(flipped, cv2.COLOR_BGR2RGB)
plt.imshow(flipped_rgb)
plt.title("Flipped Cropped Eagle")
plt.axis("off")
plt.show()
```

#### 10. Read in the image ('Apollo-11-launch.jpg').
```python
import cv2
import matplotlib.pyplot as plt
img = cv2.imread("Apollo-11-launch.jpg")
if img is None:
    print("Error: Unable to load the image.")
else:
    print("Image read successfully.")
    img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
    plt.imshow(img_rgb)
    plt.title("Apollo-11 Launch")
    plt.axis("off")
    plt.show()
```

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
```python
import cv2
import matplotlib.pyplot as plt
img = cv2.imread("Apollo-11-launch.jpg")
text = "Apollo 11 Saturn V Launch, July 16, 1969"
height, width, _ = img.shape
font = cv2.FONT_HERSHEY_SIMPLEX
text_size = cv2.getTextSize(text, font, 1, 2)[0]
x = (width - text_size[0]) // 2
y = height - 50

cv2.putText(img, text, (x, y), font, 1, (255, 255, 255), 2)
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)

plt.imshow(img_rgb)
plt.axis("off")
plt.show()

cv2.imwrite("Apollo-11-launch_text.jpg", img)
```

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
```python
import cv2
import matplotlib.pyplot as plt
img = cv2.imread("Apollo-11-launch.jpg")
if img is None:
    print("Error: Unable to load image.")
else:
    cv2.rectangle(img, (250, 80), (550, 650), (255, 0, 255), 3)
    img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
    plt.figure(figsize=(8, 8))
    plt.imshow(img_rgb)
    plt.title("Apollo-11 Launch with Rocket Highlighted")
    plt.axis("off")
    plt.show()
    cv2.imwrite("Apollo-11-launch_rectangle.jpg", img)
```

#### 13. Display the final annotated image.
```python
import cv2
import matplotlib.pyplot as plt
img = cv2.imread("Apollo-11-launch.jpg")
img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
plt.figure(figsize=(8, 10))
plt.imshow(img_rgb)
plt.title("Final Annotated Apollo 11 Launch Image")
plt.axis("off")
plt.show()
```

#### 14. Read the image ('Boy.jpg').
```python
import cv2
import matplotlib.pyplot as plt
img = cv2.imread("Boy.jpg")
if img is None:
    print("Error: Unable to load the image.")
else:
    print("Image read successfully.")
    img_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
    plt.imshow(img_rgb)
    plt.title("Boy Image")
    plt.axis("off")
    plt.show()
```

#### 15. Adjust the brightness of the image.
```python
import cv2
import matplotlib.pyplot as plt
img = cv2.imread("Boy.jpg")
if img is None:
    print("Error: Unable to load the image.")
else:
    brightness_value = 50
    bright_img = cv2.convertScaleAbs(img, alpha=1, beta=brightness_value)
    img_rgb = cv2.cvtColor(bright_img, cv2.COLOR_BGR2RGB)
    plt.imshow(img_rgb)
    plt.title("Brightness Adjusted Image")
    plt.axis("off")
    plt.show()
    cv2.imwrite("Boy_bright.jpg", bright_img)
```

#### 16. Create brighter and darker images.
```python
import matplotlib.pyplot as plt
img = cv2.imread("Boy.jpg")
bright = cv2.convertScaleAbs(img, beta=50)
dark = cv2.convertScaleAbs(img, beta=-50)
plt.subplot(1,2,1)
plt.imshow(cv2.cvtColor(bright, cv2.COLOR_BGR2RGB))
plt.title("Brighter")
plt.axis("off")
plt.subplot(1,2,2)
plt.imshow(cv2.cvtColor(dark, cv2.COLOR_BGR2RGB))
plt.title("Darker")
plt.axis("off")
plt.show()
```

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
```python
import cv2
import matplotlib.pyplot as plt
img = cv2.imread("Boy.jpg")
if img is None:
    print("Error: Unable to load the image.")
else:
    brighter_img = cv2.convertScaleAbs(img, alpha=1, beta=50)
    darker_img = cv2.convertScaleAbs(img, alpha=1, beta=-50)
    cv2.imwrite("Boy_bright.jpg", brighter_img)
    cv2.imwrite("Boy_dark.jpg", darker_img)
    original_rgb = cv2.cvtColor(img, cv2.COLOR_BGR2RGB)
    bright_rgb = cv2.cvtColor(brighter_img, cv2.COLOR_BGR2RGB)
    dark_rgb = cv2.cvtColor(darker_img, cv2.COLOR_BGR2RGB)
    plt.figure(figsize=(12, 4))
    plt.subplot(1, 3, 1)
    plt.imshow(original_rgb)
    plt.title("Original Image")
    plt.axis("off")
    plt.subplot(1, 3, 2)
    plt.imshow(bright_rgb)
    plt.title("Brighter Image")
    plt.axis("off")
    plt.subplot(1, 3, 3)
    plt.imshow(dark_rgb)
    plt.title("Darker Image")
    plt.axis("off")
    plt.show()
```

#### 18. Modify the image contrast.
```python
import cv2
import matplotlib.pyplot as plt
img = cv2.imread("Boy.jpg")
contrast_img = cv2.convertScaleAbs(img, alpha=2, beta=0)
plt.imshow(cv2.cvtColor(contrast_img, cv2.COLOR_BGR2RGB))
plt.title("Contrast Adjusted Image")
plt.axis("off")
plt.show()
```

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
```python
import cv2
import matplotlib.pyplot as plt
img = cv2.imread("Boy.jpg")
low_contrast = cv2.convertScaleAbs(img, alpha=0.5, beta=0)
high_contrast = cv2.convertScaleAbs(img, alpha=2, beta=0)
plt.figure(figsize=(12,4))
plt.subplot(1,3,1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis("off")
plt.subplot(1,3,2)
plt.imshow(cv2.cvtColor(low_contrast, cv2.COLOR_BGR2RGB))
plt.title("Lower Contrast")
plt.axis("off")
plt.subplot(1,3,3)
plt.imshow(cv2.cvtColor(high_contrast, cv2.COLOR_BGR2RGB))
plt.title("Higher Contrast")
plt.axis("off")
plt.show()
```

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
```python
import cv2
import matplotlib.pyplot as plt
img = cv2.imread("Boy.jpg")
B, G, R = cv2.split(img)
plt.figure(figsize=(12,4))
plt.subplot(1,3,1)
plt.imshow(B, cmap="gray")
plt.title("Blue Channel")
plt.axis("off")
plt.subplot(1,3,2)
plt.imshow(G, cmap="gray")
plt.title("Green Channel")
plt.axis("off")
plt.subplot(1,3,3)
plt.imshow(R, cmap="gray")
plt.title("Red Channel")
plt.axis("off")
plt.show()
```

#### 21. Merged the R, G, B , displays along with the original image
```python
import cv2
import matplotlib.pyplot as plt
img = cv2.imread("Boy.jpg")
B, G, R = cv2.split(img)
merged = cv2.merge([B, G, R])
plt.figure(figsize=(12,4))
plt.subplot(1,2,1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis("off")
plt.subplot(1,2,2)
plt.imshow(cv2.cvtColor(merged, cv2.COLOR_BGR2RGB))
plt.title("Merged RGB Image")
plt.axis("off")
plt.show()
```

#### 22. Split the image into the H, S, V components & Display the channels.
```python
import cv2
import matplotlib.pyplot as plt
img = cv2.imread("Boy.jpg")
hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
H, S, V = cv2.split(hsv)
plt.figure(figsize=(12,4))
plt.subplot(1,3,1)
plt.imshow(H, cmap="gray")
plt.title("Hue Channel")
plt.axis("off")
plt.subplot(1,3,2)
plt.imshow(S, cmap="gray")
plt.title("Saturation Channel")
plt.axis("off")
plt.subplot(1,3,3)
plt.imshow(V, cmap="gray")
plt.title("Value Channel")
plt.axis("off")
plt.show()
```
#### 23. Merged the H, S, V, displays along with original image.
```python
import cv2
import matplotlib.pyplot as plt
img = cv2.imread("Boy.jpg")
hsv = cv2.cvtColor(img, cv2.COLOR_BGR2HSV)
H, S, V = cv2.split(hsv)
merged_hsv = cv2.merge([H, S, V])
merged_img = cv2.cvtColor(merged_hsv, cv2.COLOR_HSV2BGR)
plt.figure(figsize=(10,4))
plt.subplot(1,2,1)
plt.imshow(cv2.cvtColor(img, cv2.COLOR_BGR2RGB))
plt.title("Original Image")
plt.axis("off")
plt.subplot(1,2,2)
plt.imshow(cv2.cvtColor(merged_img, cv2.COLOR_BGR2RGB))
plt.title("Merged HSV Image")
plt.axis("off")
plt.show()
```

## Output:
#### 1. Read the image ('Eagle_in_Flight.jpg') using OpenCV imread() as a grayscale image.
<img width="566" height="437" alt="image" src="https://github.com/user-attachments/assets/a873a780-4114-4661-83d1-63685f0879ed" />

#### 2. Print the image width, height & Channel.
<img width="241" height="67" alt="image" src="https://github.com/user-attachments/assets/e2da5a10-b3d4-4c88-9a2b-8f3ac2730454" />

#### 3. Display the image using matplotlib imshow().
<img width="577" height="452" alt="image" src="https://github.com/user-attachments/assets/1b9db03b-942e-4fb7-9ccb-1719b60a0371" />

#### 4. Save the image as a PNG file using OpenCV imwrite().
<img width="466" height="35" alt="image" src="https://github.com/user-attachments/assets/359824ec-f0ce-4b4a-80c4-720330f1e6ab" />

#### 5. Read the saved image above as a color image using cv2.cvtColor().
<img width="567" height="457" alt="image" src="https://github.com/user-attachments/assets/167a4a4c-7039-43d9-a931-050de93c35a6" />

#### 6. Display the Colour image using matplotlib imshow() & Print the image width, height & channel.
<img width="607" height="518" alt="image" src="https://github.com/user-attachments/assets/b9114520-ac20-4ae3-a013-05a41d5eac41" />

#### 7. Crop the image to extract any specific (Eagle alone) object from the image.
<img width="492" height="453" alt="image" src="https://github.com/user-attachments/assets/5559face-ab8f-48f5-b225-e6902a691f91" />

#### 8. Resize the image up by a factor of 2x.
<img width="547" height="455" alt="image" src="https://github.com/user-attachments/assets/fcde819e-6b61-40e3-899c-a1ed6cca0891" />

#### 9. Flip the cropped/resized image horizontally.
<img width="545" height="465" alt="image" src="https://github.com/user-attachments/assets/98785f11-eb88-492b-a353-c6632c7e452b" />

#### 10. Read in the image ('Apollo-11-launch.jpg').
<img width="575" height="378" alt="image" src="https://github.com/user-attachments/assets/e0585e3d-0b1b-4b71-8608-8322f90c8d68" />

#### 11. Add the following text to the dark area at the bottom of the image (centered on the image):
<img width="575" height="327" alt="image" src="https://github.com/user-attachments/assets/e7ee86f8-567e-42cf-ba81-fd7519ef1bb3" />

#### 12. Draw a magenta rectangle that encompasses the launch tower and the rocket.
<img width="722" height="442" alt="image" src="https://github.com/user-attachments/assets/7f2bb607-ad26-4f9f-8d10-93f6302d0eb7" />

#### 13. Display the final annotated image.
<img width="712" height="440" alt="image" src="https://github.com/user-attachments/assets/60b41a0a-600c-4cd5-b666-be5c9ddf5eb5" />

#### 14. Read the image ('Boy.jpg').
<img width="578" height="487" alt="image" src="https://github.com/user-attachments/assets/0c189635-4a42-4108-8719-431e3ba052f0" />

#### 15. Adjust the brightness of the image.
<img width="558" height="476" alt="image" src="https://github.com/user-attachments/assets/e495cde4-2676-448a-b39b-44f3f4351e75" />

#### 16. Create brighter and darker images.
<img width="611" height="240" alt="image" src="https://github.com/user-attachments/assets/a10a7544-67da-491f-9071-6e9ae4d6ec56" />

#### 17. Display the images (Original Image, Darker Image, Brighter Image).
<img width="1067" height="281" alt="image" src="https://github.com/user-attachments/assets/8a3fb9d0-23e0-4ffa-9698-cfe2c7a74f08" />

#### 18. Modify the image contrast.
<img width="592" height="440" alt="image" src="https://github.com/user-attachments/assets/ec39f300-c451-4047-a935-dd96ab8e857f" />

#### 19. Display the images (Original, Lower Contrast, Higher Contrast).
<img width="1088" height="282" alt="image" src="https://github.com/user-attachments/assets/3ba66162-f569-4bca-b4fc-cef3aea1dcd2" />

#### 20. Split the image (boy.jpg) into the B,G,R components & Display the channels.
<img width="1110" height="280" alt="image" src="https://github.com/user-attachments/assets/b0452f1b-6dc7-473e-961c-ba7b4cce73e6" />

#### 21. Merged the R, G, B , displays along with the original image
<img width="1057" height="397" alt="image" src="https://github.com/user-attachments/assets/8af563c7-f863-4212-a5fc-65878459f8a0" />

#### 22. Split the image into the H, S, V components & Display the channels.
<img width="1102" height="267" alt="image" src="https://github.com/user-attachments/assets/28815303-4234-4e6c-97c1-dea1fbbf115e" />

#### 23. Merged the H, S, V, displays along with original image.
<img width="915" height="367" alt="image" src="https://github.com/user-attachments/assets/f6238044-b2dd-4177-90c4-db09c95d086f" />


## Result:
Thus, the images were read, displayed, brightness and contrast adjustments were made, and bitwise operations were performed successfully using the Python program.

