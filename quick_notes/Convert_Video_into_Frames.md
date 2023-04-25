```python
import cv2 as cv
import os

video_path = 'videos/side_angle_sample.mp4'
cap = cv.VideoCapture(video_path)

if not cap.isOpened():
    print('Error opening video file')

output_dir = 'frames'
if not os.path.exists(output_dir):
    os.makedirs(output_dir)

frame_count = 0

while True:
    ret, frame = cap.read()

    if not ret:
        break

    frame_count += 1
    output_path = os.path.join(output_dir, f'frame_{frame_count:04}.jpg')
    cv.imwrite(output_path, frame)

cap.release()
cv.destroyAllWindows()

```


```python

```
