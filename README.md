# imageprocessing
Develop a program to display grayscale image using read and write operation.

GRAY SCALE IMAGE
import cv2 
import numpy as np
image = cv2.imread('Rose.jpg') 
cv2.imshow('Old', image) 
cv2.waitKey() 
gray = cv2.cvtColor(image, cv2.COLOR_BGR2GRAY) 
cv2.imshow('Gray', gray) 
cv2.imwrite('sample.jpg',gray)
cv2.waitKey(0)   
cv2.destroyAllWindows()

![image](https://user-images.githubusercontent.com/72264974/104425840-26930200-55a7-11eb-958f-ab6221a2602f.png)
![image](https://user-images.githubusercontent.com/72264974/104426116-85f11200-55a7-11eb-9c9e-ccdb3156c59a.png)
