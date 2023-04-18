## Smoothing and Blurring


```python
import cv2 as cv
import numpy as np
import matplotlib.pyplot as plt
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


```python
img = cv.imread('images/virat_1.jpg')
cv.imshow('Img', img)
close_image()
```

## Blur


```python
# blur an image
# kernel size has to be an odd number
blur = cv.GaussianBlur(img, (7,7), cv.BORDER_DEFAULT)
cv.imshow('Blur', blur)
close_image()
```

## Averaging in Blur 


```python
# averaging
avg = cv.blur(img, (3,3))
cv.imshow('Avg', avg)
close_image()
```

## Gaussian Blur


```python
# Gaussian - more natural blur
# assigns weights to the kernel pixels
```

## Using Median to reduce Noise


```python
# median - reduces noise
median = cv.medianBlur(img, 5)
cv.imshow('Avg', median)
close_image()
```

## Smudged version


```python
# bilateral
# diameter, 
# smudged version
bilateral = cv.bilateralFilter(img, 5, 30, 30)
cv.imshow('bil', bilateral)
close_image()
```


```python

```
