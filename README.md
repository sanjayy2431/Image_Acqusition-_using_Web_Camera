# Image_Acqusition-_using_Web_Camera

## Developed By:Sanjay V
## Register No:212223230188
## Aim
 
Aim:
 
To write a python program using OpenCV to capture the image from the web camera and do the following image manipulations.
i) Write the frame as JPG 
ii) Display the video 
iii) Display the video by resizing the window
iv) Rotate and display the video

## Software Used
Anaconda - Python 3.7
## Algorithm
### Step 1:
Import OpenCV Package.

### Step 2:
Capture Video from Webcam. Use VideoCapture(0) to access the webcam and start capturing video.

### Step 3:
Read Video or Image. Utilize 'imread' to read a video frame or image from the webcam.

### Step 4:
Save Image to File. Employ 'imwrite' to save the captured image to a file.

### Step 5:
Display Video or Image. Use 'imshow' to display the captured video frame or image, and end Program with 'q'. Allow the program to be terminated by pressing the 'q' key.

## Program:
``` Python
### Developed By:Sanjay V
### Register No:212223230188

## i) Write the frame as JPG file
import cv2
videoCaptureObject = cv2.VideoCapture(0)
while (True):
    ret,frame = videoCaptureObject.read()
    cv2.imwrite("img.jpeg",frame)
    result = False
videoCaptureObject.release()
cv2.destroyAllWindows()


         OR

import cv2

videoCaptureObject = cv2.VideoCapture(0)
max_frames = 4  # Maximum number of frames to capture
frame_count = 0

while frame_count < max_frames:
    ret, frame = videoCaptureObject.read()
    cv2.imwrite(f"img_{frame_count}.jpeg", frame)
    frame_count += 1

videoCaptureObject.release()
cv2.destroyAllWindows()




## ii) Display the video
import cv2
videoCaptureObject = cv2.VideoCapture(0)
while(True):
    ret,frame = videoCaptureObject.read()
    cv2.imshow('myimage',frame)
    if cv2.waitKey(1) == ord('q'):
        break
videoCaptureObject.release()
cv2.destroyAllWindows()




## iii) Display the video by resizing the window
import cv2
import numpy as np
cap = cv2.VideoCapture(0)
while True:
    ret, frame = cap.read() 
    width = int(cap.get(3))
    height = int(cap.get(4))
    image = np.zeros(frame.shape, np.uint8) 
    smaller_frame = cv2.resize(frame, (0,0), fx = 0.5, fy=0.5) 
    image[:height//2, :width//2] = smaller_frame
    image[height//2:, :width//2] = smaller_frame
    image[:height//2, width//2:] = smaller_frame 
    image [height//2:, width//2:] = smaller_frame
    cv2.imshow('myimage', image)
    if cv2.waitKey(1) == ord('q'):
        break
cap.release()
cv2.destroyAllWindows()




## iv) Rotate and display the video
import cv2
import numpy as np
cap = cv2.VideoCapture(0)
while True:
    ret, frame = cap.read() 
    width = int(cap.get(3))
    height = int(cap.get(4))
    image = np.zeros(frame.shape, np.uint8) 
    smaller_frame = cv2.resize(frame, (0,0), fx = 0.5, fy=0.5) 
    image[:height//2, :width//2] = cv2.rotate(smaller_frame,cv2.ROTATE_180)
    image[height//2:, :width//2] = cv2.rotate(smaller_frame,cv2.ROTATE_180)
    image[:height//2, width//2:] = smaller_frame 
    image [height//2:, width//2:] = smaller_frame
    cv2.imshow('myimage', image)
    if cv2.waitKey(1) == ord('q'):
        break
cap.release()
cv2.destroyAllWindows()









```
## Output

### i) Write the frame as JPG image
![image](https://github.com/Ragu-123/Image_Acqusition-_using_Web_Camera/assets/113915622/44cf5382-6880-46fd-b49e-19cefdceb7b5)



### ii) Display the video
![WhatsApp Image 2024-02-22 at 13 51 13_c94dd397](https://github.com/Ragu-123/Image_Acqusition-_using_Web_Camera/assets/113915622/36aff539-4413-4a35-b0e0-f8e53b59046d)


### iii) Display the video by resizing the window
![WhatsApp Image 2024-02-22 at 13 53 33_9d275659](https://github.com/Ragu-123/Image_Acqusition-_using_Web_Camera/assets/113915622/41da4d20-5aa7-445e-96aa-04ba087ea1aa)




### iv) Rotate and display the video
![WhatsApp Image 2024-02-22 at 13 56 32_8697fb4d](https://github.com/Ragu-123/Image_Acqusition-_using_Web_Camera/assets/113915622/706c3b05-9a2e-4f3a-aac1-a32ad9936cfb)





## Result:
Thus the image is accessed from webcamera and displayed using openCV.
