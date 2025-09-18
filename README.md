# Image-Acquisition-from-Web-Camera
## AIM:

To write a python program using OpenCV to capture the image from the web camera and do the following image manipulations.
i) Write the frame as JPG 
ii) Display the video 
iii) Display the video by resizing the window
iv) Rotate and display the video

## SOFTWARE USED:
Anaconda - Python 3.7
## ALGORITHM:
### Step 1:
Use cv2.VideoCapture(0) to access web camera
<br>

### Step 2:
Use cv2.imread to read the video or image
<br>

### Step 3:
Use cv2.imwrite to save the image
<br>

### Step 4:
Use cv2.imshow to show the video
<br>

### Step 5:
End the program and close the output video window by pressing 'q'.
<br>

## PROGRAM:
``` Python
### Developed By: HIRUTHIK SUDHAKAR
### Register No: 212223240054

from IPython.display import display, Javascript
from google.colab.output import eval_js
from base64 import b64decode
import cv2
import numpy as np
from google.colab.patches import cv2_imshow

def capture_frame():
    js = Javascript('''
    async function takePhoto() {
      const div = document.createElement('div');
      const video = document.createElement('video');
      div.appendChild(video);
      document.body.appendChild(div);
      const stream = await navigator.mediaDevices.getUserMedia({video: true});
      video.srcObject = stream;
      await video.play();
      const canvas = document.createElement('canvas');
      canvas.width = video.videoWidth;
      canvas.height = video.videoHeight;
      canvas.getContext('2d').drawImage(video, 0, 0);
      stream.getTracks().forEach(track => track.stop());
      div.remove();
      return canvas.toDataURL('image/jpeg', 1.0);
    }
    ''')
    display(js)
    data = eval_js('takePhoto()')
    binary = b64decode(data.split(',')[1])
    nparr = np.frombuffer(binary, np.uint8)
    frame = cv2.imdecode(nparr, cv2.IMREAD_COLOR)
    return frame

## i) Write the frame as JPG file
frame = capture_frame()
cv2.imwrite("captured_image.jpg", frame)
print("Image saved as captured_image.jpg")
cv2_imshow(frame)




## ii) Display the video
frame = capture_frame()
cv2_imshow(frame)





## iii) Display the video by resizing the window
frame = capture_frame()
height, width, _ = frame.shape
smaller_frame = cv2.resize(frame, (0,0), fx=0.5, fy=0.5)
image = np.zeros_like(frame)
image[:height//2, :width//2] = smaller_frame
cv2_imshow(image)




## iv) Rotate and display the video
frame = capture_frame()
rotated = cv2.rotate(frame, cv2.ROTATE_90_CLOCKWISE)
cv2_imshow(rotated)








```
## OUTPUT:

### i) Write the frame as JPG image
![(https://github.com/mohan8900/Image_Acqusition-_using_Web_Camera/blob/main/306834696-5c319921-b55e-4ec5-a6f2-f2294b0a8e72.png)](https://github.com/mohan8900/Image_Acqusition-_using_Web_Camera/blob/main/306834696-5c319921-b55e-4ec5-a6f2-f2294b0a8e72.png)



</br>
</br>


### ii) Display the video
![Screenshot 2024-02-21 213311](https://github.com/Jaiganesh235/Image_Acqusition-_using_Web_Camera/assets/118657189/d29f2b17-edf9-4bbe-906e-b6e5a9424d12)


</br>
</br>


### iii) Display the video by resizing the window
![Screenshot 2024-02-21 213416](https://github.com/Jaiganesh235/Image_Acqusition-_using_Web_Camera/assets/118657189/49686dd1-a328-4909-a5f1-ddf0567ecff6)



</br>
</br>



### iv) Rotate and display the video
![Screenshot 2024-02-21 213518](https://github.com/Jaiganesh235/Image_Acqusition-_using_Web_Camera/assets/118657189/2fe12628-6724-41d5-9e06-15bbfa8eacb2)



</br>
</br>


## RESULT: 
Thus the image is accessed from webcamera and displayed using openCV.
