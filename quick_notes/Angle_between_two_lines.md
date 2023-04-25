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
# fit image to screen size
def fit_image(img):
    # Get screen resolution
    screen_width, screen_height = 1920, 1080  # Replace with your screen resolution
    window_size = min(screen_width, screen_height)

    # Resize image to fit window
    img_height, img_width, _ = img.shape
    scale = window_size / max(img_height, img_width)
    resized_img = cv.resize(img, None, fx=scale, fy=scale)
    
    return resized_img
```


```python
img_path = 'images/frame_1671.jpg'
img = cv.imread(img_path)

start_point = (2000, 240)
end_point1 = (2000, 690)
end_point2 = (1590, 0)
end_point3 = (1600, 270)
end_point4 = (625, 1100)
end_point5 = (500, 0)
end_point6 = (1600, 640)
end_point7 = (0, 800)

line_thickness = 10
line_color_c = (0,255,0)

cv.line(img, start_point, end_point1, line_color_c, line_thickness)
cv.line(img, start_point, end_point2, line_color_c, line_thickness)
cv.line(img, start_point, end_point3, line_color_c, line_thickness)
cv.line(img, end_point1, end_point4, line_color_c, line_thickness)
cv.line(img, end_point3, end_point5, line_color_c, line_thickness)
cv.line(img, end_point3, end_point6, line_color_c, line_thickness)
cv.line(img, end_point6, end_point7, line_color_c, line_thickness)
cv.line(img, end_point6, end_point1, line_color_c, line_thickness)

vector1 = np.array(end_point1) - np.array(start_point)
vector2 = np.array(end_point2) - np.array(start_point)

cosine_angle = np.dot(vector1, vector2) / (np.linalg.norm(vector1) * np.linalg.norm(vector2))
angle = np.arccos(cosine_angle)
angle_degrees = np.degrees(angle)

print('Angle between the two lines:', angle_degrees)

# re_img = fit_image(img)
# cv.imshow('Image with two lines', re_img)
# close_image()

plt.figure(figsize=(12,6))
plt.imshow(img)
plt.show()
```

    Angle between the two lines: 120.34324888423959
    


    
![png](output_3_1.png)
    



```python

```
