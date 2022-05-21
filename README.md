# Thresholding of Images
## Aim
To segment the image using global thresholding, adaptive thresholding and Otsu's thresholding using python and OpenCV.

## Software Required
1. Anaconda - Python 3.7
2. OpenCV

## Algorithm

### Step 1:
Load the image and convert the image to Grayscale.

### Step 2:
Smoothen the image using Gaussian Method.

### Step 3:
Apply thresholding cv2.THRESH_BINARY on the image.

### Step 4:
Apply thresholding cv2.THRESH_BINARY_INC on the image.

### Step 5:
Apply thresholding cv2.THRESH_TRUNC on the image.

### Step 6:
Apply thresholding cv2.THRESH_TOZERO on the image.

### Step 7:
Apply thresholding cv2.THRESH_TOZERO_INC on the image.
</br>
## Program
Developrd by: G Venkata Pavan
Registration Number: 212221240013
```python
import cv2
import matplotlib.pyplot as plt
image = cv2.imread("jerry.jpeg")

# Read the Image and convert to grayscale

grayImage = cv2.cvtColor(image,cv2.COLOR_BGR2GRAY)

# Use Global thresholding to segment the image

ret,thresh = cv2.threshold(grayImage,100,200,cv2.THRESH_BINARY)
ret1,thresh1 = cv2.threshold(grayImage,100,200,cv2.THRESH_BINARY_INV)
ret2, thresh2 = cv2.threshold(grayImage,100,200,cv2.THRESH_TRUNC)
ret3, thresh3 = cv2.threshold(grayImage,100,200,cv2.THRESH_TOZERO)
ret4, thresh4 = cv2.threshold(grayImage,100,200,cv2.THRESH_TOZERO_INV)

# Use Adaptive thresholding to segment the image

th1 = cv2.adaptiveThreshold(grayImage,255,cv2.ADAPTIVE_THRESH_MEAN_C,cv2.THRESH_BINARY,11,2)
th2 = cv2.adaptiveThreshold(grayImage,255,cv2.ADAPTIVE_THRESH_GAUSSIAN_C,cv2.THRESH_BINARY,11,2)
titles = ["Original Image","Adaptive Mean Thresholding","Adaptive Gaussian Thresholding"]
imgs = [grayImage,th1,th2]

# Use Otsu's method to segment the image 
ret5,th3 = cv2.threshold(grayImage,0,255,cv2.THRESH_BINARY+cv2.THRESH_OTSU)

# Display the results

cv2.imshow("Original Image",image)
cv2.imshow("Gray Image",grayImage)
cv2.imshow("THRESH_BINARY",thresh)
cv2.imshow("THRESH_BINARY_INV",thresh1)
cv2.imshow("THRESH_TRUNC",thresh2)
cv2.imshow("THRESH_TOZERO",thresh3)
cv2.imshow("THRESH_TOZERO_INV",thresh4)

for i in range(3):
    plt.subplot(3,1,i+1)
    plt.imshow(imgs[i],'gray')
    plt.title(titles[i])
    plt.xticks([]),plt.yticks([])
plt.show()


cv2.imshow("Otsu method",th3)
cv2.waitKey(0)



```
## Output

### Original Image andGray Image:
![DIPex9gray](https://user-images.githubusercontent.com/94827772/169654240-3fa130db-4831-425f-b3eb-d8fabf700d71.png)
![DIPex9ori](https://user-images.githubusercontent.com/94827772/169654242-4baa15f9-c7f2-4f89-91d4-90a8c1d56085.png)

### Global Thresholding:
![DIPex9bin](https://user-images.githubusercontent.com/94827772/169654563-325e48bb-67d9-4269-b0bc-17d2c2c642da.png)
![DIPex9toz](https://user-images.githubusercontent.com/94827772/169654565-d7d20e86-6309-4e69-a839-518c8c981cd9.png)</br>
![DIPex9trunc](https://user-images.githubusercontent.com/94827772/169654566-e0631d90-7064-4cff-aabd-24076eaaa8c2.png)

### Adaptive Thresholding:
![DIPOAA](https://user-images.githubusercontent.com/94827772/169654578-f3cd0c5c-c0da-4676-a421-d983dd025216.png)

### Optimum Global Thesholding using Otsu's Method:
![DIPex9otsu](https://user-images.githubusercontent.com/94827772/169654591-11e2fcb3-b9cc-455e-a97a-7c232b37610c.png)


## Result
Thus the images are segmented using global thresholding, adaptive thresholding and optimum global thresholding using python and OpenCV.

