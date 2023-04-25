## Video details


```python
import cv2

video_path = 'videos/side_angle_sample.mp4'
cap = cv2.VideoCapture(video_path)

if not cap.isOpened():
    print('Error opening video file')

frame_rate = cap.get(cv2.CAP_PROP_FPS)
resolution = (int(cap.get(cv2.CAP_PROP_FRAME_WIDTH)), int(cap.get(cv2.CAP_PROP_FRAME_HEIGHT)))

print(f'Frame rate: {frame_rate:.2f} fps')
print(f'Resolution: {resolution[0]} x {resolution[1]} pixels')

cap.release()
cv2.destroyAllWindows()

```

    Frame rate: 30.03 fps
    Resolution: 2160 x 1080 pixels
    

## Image details


```python
import cv2

image_path = 'images/virat_1.jpg'
image = cv2.imread(image_path)

if image is None:
    print('Error opening image file')

resolution = (image.shape[1], image.shape[0])

print(f'Resolution: {resolution[0]} x {resolution[1]} pixels')

```

    Resolution: 1656 x 1080 pixels
    
