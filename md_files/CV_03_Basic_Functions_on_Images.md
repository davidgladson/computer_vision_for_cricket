## Basic Functions on Images


```python
import cv2 as cv
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

### Read an image


```python
# read an image
img = cv.imread('images/virat_1.jpg')
cv.imshow('Virat', img)
close_image()
```

### Convert an image to greyscale


```python
# converting bgr to greyscale
gray = cv.cvtColor(img, cv.COLOR_BGR2GRAY)
cv.imshow('Gray', gray)
close_image()
```

### Blur an image


```python
# blur an image
# kernel size has to be an odd number
blur = cv.GaussianBlur(img, (7,7), cv.BORDER_DEFAULT)
cv.imshow('Blur', blur)
close_image()
```

### Edge detection in image


```python
# create an edge cascade - find the edges (ex: canny edge detection)
# for edge detection - pass in blur to get less edges
canny = cv.Canny(blur, 125,175)
cv.imshow('Edges', canny)
close_image()
```

### Dilate an image


```python
# dilate an image
dilated = cv.dilate(canny, (3,3), iterations = 2)
cv.imshow('Diilated', dilated)
close_image()
```

### Erode an image


```python
# eroding
eroded = cv.erode(dilated, (3,3), iterations = 2)
cv.imshow('Eroded', eroded)
close_image()
```

### Resize an image


```python
# resize
# ignores the aspect ratio
resized = cv.resize(img, (500,500))
# helps in clarity
resized = cv.resize(img, (500,500), interpolation = cv.INTER_LINEAR)
cv.imshow('Resized', resized)
close_image()
```

### Crop an image


```python
# cropping
cropped = img[100:1200,600:1300]
cv.imshow('Cropped', cropped)
close_image()
```
