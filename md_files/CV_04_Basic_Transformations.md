## Basic Transformations on Images


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

## Translation


```python
# -x, -y, x, y
def translate(img, x, y):
    # no of pixels you want to shift along x-y axes
    transMat = np.float32([[1,0,x], [0,1,y]])
    dimensions = (img.shape[1], img.shape[0])
    return cv.warpAffine(img, transMat, dimensions)
```


```python
translated = translate(img, 300, 100)
cv.imshow('translated', translated)
close_image()
```

## Rotation


```python
# clockwise, anti-cliockwise
def rotation(img, angle, rotPoint = None):
    (height, width) = img.shape[:2]
    
    # rotate around the center
    if rotPoint is None:
        rotPoint = (width//2, height//2)
    
    rotMat = cv.getRotationMatrix2D(rotPoint, angle, 1)
    dimensions = (width, height)
    
    return cv.warpAffine(img, rotMat, dimensions)
```


```python
rotated = rotation(img, 45)
cv.imshow('rotated', rotated)
close_image()
```

## Flip


```python
# 0 - vertical
# 1 - horizontal
# -1 - both vertical & horizontal
flip = cv.flip(img, 0)
cv.imshow('flip', flip)
close_image()
```


```python

```
