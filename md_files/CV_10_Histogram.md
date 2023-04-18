## Histogram of Colors in an Image


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


```python
plt.imshow(img)
plt.show()
```


    
![png](output_5_0.png)
    



```python
# converting bgr to greyscale
gray = cv.cvtColor(img, cv.COLOR_BGR2GRAY)

# gray sclae histogram
gray_hist = cv.calcHist([gray], [0], None, [256], [0,256])

plt.plot(gray_hist)
plt.show()
```


    
![png](output_6_0.png)
    


## Hist for RGB images


```python
colors = ('b', 'g', 'r')
for i, col in enumerate(colors):
    hist = cv.calcHist([img], [i], None, [256], [0,256])
    plt.plot(hist, color=col)
    
plt.show()
```


    
![png](output_8_0.png)
    



```python

```
