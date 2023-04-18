## Create Masks


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

## Create an array to store mask


```python
blank = np.zeros(img.shape[:2], dtype = 'uint8')
cv.imshow('Blank image', blank)
close_image()

mask = cv.circle(blank, (img.shape[1]//2, img.shape[0]//2), 100, 255, -1)
cv.imshow('mask', mask)
close_image()
```

## Apply Mask


```python
masked = cv.bitwise_and(img, img, mask=mask)
cv.imshow('masked', masked)
close_image()
```


```python
plt.imshow(masked)
plt.show()
```


    
![png](output_9_0.png)
    



```python

```
