```python
import cv2 as cv
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
# read image
image = cv.imread('images/virat_1.jpg')
output = image.copy()

# starting points of the box
x = 800
y = 200

# dimensions of the box
width = 400
height = 850

# draw & assign label
bbox = (x, y, width, height)
label = 'virat kohli'
cv.rectangle(output, (x, y), (x + width, y + height), (0, 255, 0), 2)
cv.putText(output, label, (x, y - 10), cv.FONT_HERSHEY_SIMPLEX, 0.5, (0, 255, 0), 2)

# output
cv.imshow('Img', output)
close_image()
```


```python
# # show image in matplotlib
# plt.imshow(output)
# plt.show()
```
