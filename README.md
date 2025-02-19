# Thresholding of Images
## Aim
To segment the image using global thresholding, adaptive thresholding and Otsu's thresholding using python and OpenCV.

## Software Required
1. Anaconda - Python 3.7
2. OpenCV

## Algorithm

Step 1: Load the image and convert the image to Grayscale.

Step 2: Smoothen the image using Gaussian Method.

Step 3: Apply thresholding cv2.THRESH_BINARY on the image.

Step 4: Apply thresholding cv2.THRESH_BINARY_INC on the image.

Step 5: Apply thresholding cv2.THRESH_TRUNC on the image.

Step 6: Apply thresholding cv2.THRESH_TOZERO on the image.

Step 7: Apply thresholding cv2.THRESH_TOZERO_INC on the image.

## Program
Developed by: Palamakula Deepika</br>
RegisterNumber:  212221240035
```python
import cv2
import matplotlib.pyplot as plt
image = cv2.imread("car1.jpg")

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

### Original Image
![de1](https://user-images.githubusercontent.com/94154679/171162646-b37fd364-4acf-49a4-86ee-3a99b5970d70.png)

![de2](https://user-images.githubusercontent.com/94154679/171162632-633c48dc-d8b6-46a5-b3f2-4781ae7d6f99.png)


### Global Thresholding
![de5](https://user-images.githubusercontent.com/94154679/171162743-ccacd33d-8cac-4e83-8075-6a9382364934.png)
![de4](https://user-images.githubusercontent.com/94154679/171162748-eb82e95c-cf02-4e4a-a7c5-0c535f6bb682.png)
![de3](https://user-images.githubusercontent.com/94154679/171162751-40dc3350-d8cb-4a48-b46d-74629f4ebc35.png)

### Adaptive Thresholding
![de6](https://user-images.githubusercontent.com/94154679/171162873-5dee5faa-f548-456a-b1af-5815a6950757.png)


### Optimum Global Thesholding using Otsu's Method
![de7](https://user-images.githubusercontent.com/94154679/171162928-03a7b4bd-fade-4a6f-8f1c-f095e2ef6677.png)


## Result
Thus the images are segmented using global thresholding, adaptive thresholding and optimum global thresholding using python and OpenCV.

