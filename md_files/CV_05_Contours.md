## Contour detection

Contours - They are the curves that join continuous points along the boundary of an object in an image. They are a useful tool for image segmentation, shape analysis, and object recognition


```python
import cv2 as cv
import numpy as np
```


```python
# create a function to close image with d key
def close_image():
    # wait for a key event
    while True:
        key = cv.waitKey(0)

        # if the key event is the 'd' key, break out of the loop
        if key == ord('d'):
            break

    # close the window
    cv.destroyAllWindows()
```

## Read an image


```python
img = cv.imread('images/virat_1.jpg')
cv.imshow('virat', img)
close_image()
```

## Greyscale


```python
# converting bgr to greyscale
gray = cv.cvtColor(img, cv.COLOR_BGR2GRAY)
cv.imshow('Gray', gray)
close_image()
```

## Edge detection


```python
# edge detection
canny = cv.Canny(img, 125,175)
cv.imshow('Edges', canny)
close_image()
```

## Contour detection


```python
contours, hierarchies = cv.findContours(canny, cv.RETR_LIST, cv.CHAIN_APPROX_NONE)

# after blur you'll find lesser contours
# no of contours found
len(contours)
```




    2482




```python
# thresholding - converts the image to binary
ret, thresh = cv.threshold(gray, 125, 125, cv.THRESH_BINARY)

cv.imshow('Thresh', thresh)
close_image()
```

## Visualize Contours


```python
blank = np.zeros(img.shape, dtype = 'uint8')
```


```python
# -1 contour index
cv.drawContours(blank, contours, -1, (0,255,0), thickness = 2)
cv.imshow('contours', blank)
close_image()
```


```python

```
