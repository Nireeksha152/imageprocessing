# imageprocessing
Program1:Develop a program to display grayscale image using read and write operation.

GRAY SCALING:
      Grayscaling is the process of converting an image from other color spaces e.g RGB, CMYK, HSV, etc. to shades of gray. It varies between complete black and complete white.
cv2.imread() this method loads an image from specified file.
cv2.imwrite() this method is use to write the image.
cv2.cvtColor() this method is used to convert an image from one color space to another.
cv2.destroyAllWindows() If we have multiple window open and we donot need those to be open we can use this method to close those all
cv2.waitKey(0) this metjod will display the output window infinetely until any key is pressed

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
