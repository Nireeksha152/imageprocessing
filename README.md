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

#rotation of the image
import cv2 
import numpy as np
image = cv2.imread('Rose.jpg')
print(type(image))
cv2.imshow('Old', image) 
Height,Width=image.shape[0:2]
rotationMatrix=cv2.getRotationMatrix2D((Width/2,Height/2),45,.9)
rotatedImage = cv2.warpAffine(image, rotationMatrix, (Width, Height))
#numpy_horizontal_concat = np.concatenate((image, rotatedImage), axis=1)
cv2.imshow('new',rotatedImage )
cv2.waitKey(0)   
cv2.destroyAllWindows()

![image](https://user-images.githubusercontent.com/72264974/104427451-43c8d000-55a9-11eb-8865-a3869776913d.png)
![image](https://user-images.githubusercontent.com/72264974/104427622-7672c880-55a9-11eb-9452-896ce735491b.png)

#resizing the image using axis value
import cv2 as c
import numpy as np
img=c.imread('cat.jpg')
c.imshow('original',img)
print(img.shape[0:2])
c.waitKey()
nimg=c.resize(img,(0,0),fx=0.75,fy=0.75)
c.imshow('Result',nimg)
c.waitKey(0)
print(nimg.shape[0:2])
c.destroyAllWindows()

![image](https://user-images.githubusercontent.com/72264974/104427897-cd789d80-55a9-11eb-8b58-fc30ebb79696.png)
![image](https://user-images.githubusercontent.com/72264974/104427983-e719e500-55a9-11eb-9128-3d181381ae76.png)

