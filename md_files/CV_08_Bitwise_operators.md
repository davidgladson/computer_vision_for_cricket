## Bitwise Operations


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

## Read an image


```python
img = cv.imread('images/virat_1.jpg')
cv.imshow('Img', img)
close_image()
```

## Create an array


```python
# bitwise operates in a binary manner
blank = np.zeros((400, 400), dtype = 'uint8')
```

## Create a Rectangle & Circle


```python
rec = cv.rectangle(blank.copy(), (30, 30), (370, 370), 255, -1)
cir = cv.circle(blank.copy(), (200, 200), 200, 255, -1)

cv.imshow('rec', rec)
close_image()

cv.imshow('cir', cir)
close_image()
```

## Perform - AND, OR, NOT, XOR


```python
# AND, OR, NOT, XOR

# intersecting
biw_and = cv.bitwise_and(rec, cir)

# non-intersecting & intersecting regions
biw_or = cv.bitwise_or(rec, cir)

# flip bits
biw_not = cv.bitwise_not(rec, cir)

# non intersecting regions
biw_xor = cv.bitwise_xor(rec, cir)
```

## View the results


```python
cv.imshow('and', biw_and)
close_image()

cv.imshow('or', biw_or)
close_image()

cv.imshow('not', biw_not)
close_image()

cv.imshow('xor', biw_xor)
close_image()
```


```python

```
