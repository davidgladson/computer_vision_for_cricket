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
video_path = 'videos/side_angle_sample.mp4'
cap = cv.VideoCapture(video_path)

frame_rate = cap.get(cv.CAP_PROP_FPS)
width, height = int(cap.get(cv.CAP_PROP_FRAME_WIDTH)), int(cap.get(cv.CAP_PROP_FRAME_HEIGHT))

# Create a video writer object
fourcc = cv.VideoWriter_fourcc(*'mp4v')  # Change the codec as needed
out = cv.VideoWriter('videos/output.mp4', fourcc, 30, (width, height))

if not cap.isOpened():
    print('Error opening video file')


frame_count = 0

while True:
    ret, img = cap.read()
    if not ret:
        break
        
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

    out.write(img)

cap.release()
cv.destroyAllWindows()
```


```python

```


```python

```


```python

```
