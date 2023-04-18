## Draw shapes & Write Text


```python
# import 
import cv2 as cv
import numpy as np
```

## Write on an image


```python
# read image
img = cv.imread('images/virat_1.jpg')

# write text
# here (255, 255) indicates the text starting point, (0,0,0) indicates black
cv.putText(img, "Virat Kohli", (225, 255), cv.FONT_HERSHEY_SIMPLEX, 3, (255,255,255), thickness = 2)

cv.imshow('Virat with text', img)

# wait for a key press
while True:
    key = cv.waitKey(0)

    # press 'd' key, to close the window
    if key == ord('d'):
        break

# close the window
cv.destroyAllWindows()
```

## Draw on a blank image


```python
# height width, color
# create a blank image with height as 500, width as 500, color as 3 channels (RGB)
# here uint - unsigned integer which takes less memory space
blank = np.zeros((500, 500, 3),dtype = 'uint8')

# paint the image with a color - blue
blank[:] = 0,0,255

# color a certain portion - height in between 200 to 300
# fill with green
blank[200:300, :] = 0,255,0

# draw a recangle
# here thickness indicates border thickness
cv.rectangle(blank, (0,0), (250, 250), (255, 0, 0), thickness = 2)

# fill a rectangle - start, end coordinates
# if thickness is -1, then no border
cv.rectangle(blank, (0,0), (250, 250), (255, 0, 0), thickness = -1)

# draw a circle - center & radius
cv.circle(blank, (250, 250), 40, (0,255,234), thickness = -1)

# draw a line - start, end points
cv.line(blank, (0,0), (10, 10), (0,255,0), thickness = 3)

# write text
# here (255, 255) indicates the text starting point, (0,0,0) indicates black
cv.putText(blank, "Hello", (225, 255), cv.FONT_HERSHEY_SIMPLEX, 1, (0,0,0), thickness = 2)

cv.imshow('Blank', blank)

# wait for a key press
while True:
    key = cv.waitKey(0)

    # press 'd' key, to close the window
    if key == ord('d'):
        break

# close the window
cv.destroyAllWindows()
```


```python

```
