## Installations


```python
# !pip install opencv-python
```

## Resources

- https://github.com/jasmcaus/opencv-course.git
- https://docs.opencv.org/4.x/d9/df8/tutorial_root.html

## Reading Images


```python
import cv2 as cv
```


```python
# read an image
img = cv.imread('images/virat_1.jpg')
cv.imshow('Virat', img)

# wait for a key event
while True:
    key = cv.waitKey(0)

    # if the key event is the 'd' key, break out of the loop
    if key == ord('d'):
        break

# close the window
cv.destroyAllWindows()
```

## Reading Videos


```python
# 0- webcam, 1 - 2nd cam
# press d to exit the video
capture = cv.VideoCapture("videos/dk_last_ball.wmv")

while True:
    # a boolean to say whether the frame is read or not
    isTrue, frame = capture.read()
    cv.imshow('Video', frame)
    
    # if the letter d is pressed, break out of the loop
    if cv.waitKey(25) & 0xFF == ord('d'):
        break
        
capture.release()
cv.destroyAllWindows()
```


```python
# error: OpenCV(4.5.4) D:\a\opencv-python\opencv-python\opencv\modules\imgproc\src\color.cpp:182: error: (-215:Assertion failed) !_src.empty() in function 'cv::cvtColor'
# in case of the above error - no frames left to read
```

## Rescale & Resize - Image & Video files


```python
def rescaleFrame(frame, scale = 0.75):
    # images, videos & live video
    width = int(frame.shape[1]*scale)
    height = int(frame.shape[0]*scale)
    dimensions = (width, height)
    
    return cv.resize(frame, dimensions, interpolation = cv.INTER_AREA)
```


```python
capture = cv.VideoCapture("videos/dk_last_ball.wmv")

while True:
    # a boolean to say whether the frame is read or not
    isTrue, frame = capture.read()
    frame_resized = rescaleFrame(frame, 0.5)
    
    cv.imshow('Video', frame_resized)
    
    # if the letter d is pressed, break out of the loop
    if cv.waitKey(25) & 0xFF == ord('d'):
        break
        
capture.release()
cv.destroyAllWindows()
```


```python
img = cv.imread('images/virat_1.jpg')
resized_image = rescaleFrame(img)

img = cv.imshow('Image rescaled', resized_image)

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

```


```python

```
