## Knowing Color Spaces & Color Channels


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

## BGR, Gray Scale, LAB

In color code, LAB stands for the CIELAB color space, which is a color space defined by the International Commission on Illumination (CIE).

The LAB color space is designed to approximate human perception of color and is used in color science and computer vision applications. It is a three-dimensional color space that describes color using three coordinates: L for lightness, A for the green-red axis, and B for the blue-yellow axis.


```python
img = cv.imread('images/virat_1.jpg')

# converting bgr to greyscale
gray = cv.cvtColor(img, cv.COLOR_BGR2GRAY)
cv.imshow('Gray', gray)
close_image()
```


```python
# bgr to lab 
lab = cv.cvtColor(img, cv.COLOR_BGR2LAB)
cv.imshow('Lab', lab)
close_image()
```

## Display using Matplotlib


```python
# opencv displays images in bgr
# matplotlib dislay images in rgb
```


```python
plt.imshow(img)
plt.show()
```


    
![png](output_9_0.png)
    



```python
rgb = cv.cvtColor(img, cv.COLOR_BGR2RGB)
cv.imshow('Rgb', rgb)
close_image()
```


```python
plt.imshow(rgb)
plt.show()
```


    
![png](output_11_0.png)
    


## HSV to BGR, LAB to BGR


```python
# cv.COLOR_HSV2BGR
# cv.COLOR_LAB2BGR
```

## Color channels


```python
b, g, r = cv.split(img)
```


```python
cv.imshow('b', b)
close_image()

cv.imshow('r', r)
close_image()

cv.imshow('g', g)
close_image()
```


```python
# 3 channels, 1 channel
img.shape, b.shape
```




    ((1080, 1656, 3), (1080, 1656))



## Display in Blue, Green, Red channels


```python
blank = np.zeros(img.shape[:2], dtype = 'uint8')

blue = cv.merge([b, blank, blank])
green = cv.merge([blank, g, blank])
red = cv.merge([blank, blank, r])

cv.imshow('blue', blue)
close_image()

cv.imshow('green', green)
close_image()

cv.imshow('red', red)
close_image()
```


```python

```
