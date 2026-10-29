# Adding-Sunglasses-to-Your-Passport-Photo-Using-OpenCV

# NAME: YOGESH.S
# REG NO:212224230311

Adding-Sunglasses-to-Your-Passport-Photo-Using-OpenCV is a fun project that adds sunglasses to photos using image processing.

Welcome to Adding-Sunglasses-to-Your-Passport-Photo-Using-OpenCV , a fun and creative project designed to overlay sunglasses on individual passport photos! This repository demonstrates how to use image processing techniques to create a playful transformation, making ordinary photos look extraordinary. Whether you're a beginner exploring computer vision or just looking for a quirky project to try, this is for you!

# Features:

Detects the face in an image.

Places a stylish sunglass overlay perfectly on the face.

Works seamlessly with individual passport-size photos.

Customizable for different sunglasses styles or photo types.

# Technologies Used:

Python

OpenCV for image processing

Numpy for array manipulations

# How to Use:

Clone this repository.

Add your passport-sized photo to the images folder.

Run the script to see your "cool" transformation!

# Applications:

Learning basic image processing techniques.

Adding flair to your photos for fun.

Practicing computer vision workflows.

# Program:

```
import cv2
import numpy as np
import matplotlib.pyplot as plt
img=cv2.imread("blue background photo.jpg")
plt.imshow(img[:,:,::-1]);plt.title("Face");plt.axis("off")
```

<img width="552" height="575" alt="image" src="https://github.com/user-attachments/assets/03057fe7-8437-4e79-a918-a567d5993dcd" />



img.shape

<img width="200" height="82" alt="image" src="https://github.com/user-attachments/assets/5eddfe24-0355-49cb-a1b7-07f8fe52ee2a" />


```
glass = cv2.imread("sunglass.png",-1)
plt.imshow(glass[:,:,::-1]);plt.title("glass");plt.axis("on")
```

<img width="707" height="387" alt="image" src="https://github.com/user-attachments/assets/49e24734-dad5-4ecf-9952-1391f42577d9" />

```
glass = cv2.resize(glass,(190,50))
print("image Dimension ={}".format(glass.shape))
```

<img width="336" height="46" alt="image" src="https://github.com/user-attachments/assets/7738baf5-0e65-474e-a376-f5399776197c" />

```
glassBGR = glass[:,:,0:3]
glassMask = glass[:,:,3]
plt.figure(figsize=[15,15])
plt.subplot(121);plt.imshow(glassBGR[:,:,::-1]);plt.title('Sunglass Color channels');
plt.subplot(122);plt.imshow(glassMask,cmap='gray');plt.title('Sunglass Alpha channel');
```
<img width="1316" height="222" alt="image" src="https://github.com/user-attachments/assets/ccfe9872-24bb-43d9-8050-dc48af48f7ee" />

```
faceWithGlass = img.copy()
faceWithGlass[160:210,115:305]=glassBGR
plt.imshow(faceWithGlass[...,::-1])
```
<img width="527" height="566" alt="image" src="https://github.com/user-attachments/assets/e2fd257e-e213-4cff-aa06-bb89a261bbc2" />

```
glassM = cv2.merge((glassMask,glassMask,glassMask))
glassM = np.uint8(glassM/255)
faceWithGlassesArithmetic = img.copy()
eyeROI= faceWithGlassesArithmetic[160:210,115:305]
maskedEye = cv2.multiply(eyeROI,(1-  glassM ))
maskedGlass = cv2.multiply(glassBGR,glassM)
eyeRoiFinal = cv2.add(maskedEye, maskedGlass)
plt.figure(figsize=[20,20])
plt.subplot(131);plt.imshow(maskedEye[...,::-1]);plt.title("Masked Eye Region")
plt.subplot(132);plt.imshow(maskedGlass[...,::-1]);plt.title("Masked Sunglass Region")
plt.subplot(133);plt.imshow(eyeRoiFinal[...,::-1]);plt.title("Augmented Eye and Sunglass")
```
<img width="1305" height="242" alt="image" src="https://github.com/user-attachments/assets/37016312-4a5c-4e63-aadb-32da95bc52cb" />

```
faceWithGlassesArithmetic[160:210,115:305]=eyeRoiFinal
plt.figure(figsize=[20,20]);
plt.subplot(121);plt.imshow(img[:,:,::-1]); plt.title("Original Image");
plt.subplot(122);plt.imshow(faceWithGlassesArithmetic[:,:,::-1]);plt.title("With Sunglasses");
```
<img width="1436" height="848" alt="image" src="https://github.com/user-attachments/assets/68ee6851-c7c2-4667-a9af-9863e1267000" />


Output:

<img width="1436" height="848" alt="image" src="https://github.com/user-attachments/assets/8bfa4494-0309-4dd4-8824-c9bb6505fc5b" />


RESULT:
  
Thus Adding Sunglasses to Your Passport Photo Using OpenCV is done successfully.
