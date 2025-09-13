# Sturdy-Octo-Disco-Adding-Sunglasses-for-a-Cool-New-Look

Sturdy Octo Disco is a fun project that adds sunglasses to photos using image processing.

Welcome to Sturdy Octo Disco, a fun and creative project designed to overlay sunglasses on individual passport photos! This repository demonstrates how to use image processing techniques to create a playful transformation, making ordinary photos look extraordinary. Whether you're a beginner exploring computer vision or just looking for a quirky project to try, this is for you!

## Features:
- Detects the face in an image.
- Places a stylish sunglass overlay perfectly on the face.
- Works seamlessly with individual passport-size photos.
- Customizable for different sunglasses styles or photo types.

## Technologies Used:
- Python
- OpenCV for image processing
- Numpy for array manipulations

## How to Use:
1. Clone this repository.
2. Add your passport-sized photo to the `images` folder.
3. Run the script to see your "cool" transformation!

## Applications:
- Learning basic image processing techniques.
- Adding flair to your photos for fun.
- Practicing computer vision workflows.

  ## PROGRAM:
### Developed by: MUKESH KUMAR S
### Register Number: 212223240099

```
# Import libraries and Load the Face Image
import cv2
import numpy as np
import matplotlib.pyplot as plt
faceImage = cv2.imread('643.JPG')
plt.imshow(faceImage[:,:,::-1]);plt.title("Face")
```

<img width="469" height="601" alt="image" src="https://github.com/user-attachments/assets/cbd2d2f5-e85b-4465-a864-ece4336ed080" />



```
# Resize the image to fit over the eye region
glassPNG = cv2.resize(glassPNG,(190,70))
print("image Dimension ={}".format(glassPNG.shape))
```

<img width="731" height="616" alt="image" src="https://github.com/user-attachments/assets/d6ce0a0b-ad1b-4c94-9c00-596197889d75" />



```
# Resize the image to fit over the eye region
glassPNG = cv2.resize(glassPNG,(190,70))
print("image Dimension ={}".format(glassPNG.shape))

# Separate the Color and alpha channels
glassBGR = glassPNG[:,:,0:3]
glassMask1 = glassPNG[:,:,3]

# Display the images for clarity
plt.figure(figsize=[15,15])
plt.subplot(121);plt.imshow(glassBGR[:,:,::-1]);plt.title('Sunglass Color channels');
plt.subplot(122);plt.imshow(glassMask1,cmap='gray');plt.title('Sunglass Alpha channel');
```

<img width="1580" height="524" alt="image" src="https://github.com/user-attachments/assets/5bd4d845-20f1-4985-8c67-448d12e001fd" />



```
faceWithGlassesNaive = faceImage.copy()
# Replace the eye region with the sunglass image
faceWithGlassesNaive[150:220, 120:310]=glassBGR

plt.imshow(faceWithGlassesNaive[...,::-1])
```

<img width="484" height="597" alt="image" src="https://github.com/user-attachments/assets/8f628f25-d825-4f8a-8a5f-824d20539cc4" />



```
glassMask = cv2.merge((glassMask1,glassMask1,glassMask1))
glassMask = np.uint8(glassMask/255)
faceWithGlassesArithmetic = faceImage.copy()
eyeROI= faceWithGlassesArithmetic[150:220, 120:310]
maskedEye = cv2.multiply(eyeROI,(1-glassMask ))
maskedGlass = cv2.multiply(glassBGR,glassMask)
eyeRoiFinal = cv2.add(maskedEye, maskedGlass)
plt.figure(figsize=[20,20])
plt.subplot(131);plt.imshow(maskedEye[...,::-1]);plt.title("Masked Eye Region")
plt.subplot(132);plt.imshow(maskedGlass[...,::-1]);plt.title("Masked Sunglass Region")
plt.subplot(133);plt.imshow(eyeRoiFinal[...,::-1]);plt.title("Augmented Eye and Sunglass")
```

<img width="1748" height="438" alt="image" src="https://github.com/user-attachments/assets/4745f534-90a2-491b-b38e-ec0eeff2b1d3" />



```
faceWithGlassesArithmetic[150:220, 120:310]=eyeRoiFinal
plt.figure(figsize=[20,20]);
plt.subplot(121);plt.imshow(faceImage[:,:,::-1]); plt.title("Original Image");
plt.subplot(122);plt.imshow(faceWithGlassesArithmetic[:,:,::-1]);plt.title("With Sunglasses");
```

<img width="987" height="631" alt="image" src="https://github.com/user-attachments/assets/3dad6afb-9441-48ee-97ed-e5c006391794" />


 


