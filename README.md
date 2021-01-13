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

program2: Develop the program to perform linear transformation on a image:Scaling and Rotation.
Rotation of the Image:
   The image can be rotated in various angles(90,180,270 and 360).OpenCV calculates the affine matrix that performas affine transformation ,which mean it doesnot preserves the
rotation of distance between points lying on the lines.

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

Program3:Develop a program to find the sum and mean of a set of images. 
 a.Create ‘n’ number of images and read them from the directory and perform the operations.

import cv2
import os
path = "D:/flower"
imgs = []

files = os.listdir(path)
for file in files:
    filepath=path+"\\"+file
    imgs.append(cv2.imread(filepath))
i=0
im = []
for im in imgs:
  
    im+=imgs[i]
    i=i+1
cv2.imshow("sum of four pictures",im)
meanImg = im/len(files)
cv2.imshow("mean of four pictures",meanImg)
cv2.waitKey(0)

![image](https://user-images.githubusercontent.com/72264974/104429624-d8ccc880-55ab-11eb-9179-5e7f2a085c6c.png)
![image](https://user-images.githubusercontent.com/72264974/104429716-f26e1000-55ab-11eb-9aaf-2f65bb506309.png)

Program4:
Develop the program to convert color image to gray image and binary image.

import cv2 as c
img=c.imread('i1.jpg')
c.imshow('colour image',img)
c.waitKey(0)
gray=c.imread('i1.jpg',0)
c.imshow('Result',gray)
c.waitKey(0)
ret,img1=c.threshold(gray,128,255,c.THRESH_BINARY)
c.imshow('image',img1)
c.waitKey(0)
c.destroyAllWindows()

![image](https://user-images.githubusercontent.com/72264974/104430258-73c5a280-55ac-11eb-98a9-f26728982392.png)
![image](https://user-images.githubusercontent.com/72264974/104430305-82ac5500-55ac-11eb-8ade-7f4d35fe1999.png)
![image](https://user-images.githubusercontent.com/72264974/104430363-95bf2500-55ac-11eb-812a-3e65f7eca34c.png)

Program5:Develop the program to change the image to fifferent color spaces.
import cv2 as c
img=c.imread('Rose.jpg')
c.imshow('Original',img)
c.waitKey(0)
nimg=c.cvtColor(img,c.COLOR_BGR2HSV)
c.imshow('Result1',nimg)
c.waitKey(0)
nimg1=c.cvtColor(img,c.COLOR_BGR2RGB)
c.imshow('Result2',nimg1)
c.waitKey(0)
nimg2=c.cvtColor(img,c.COLOR_BGR2LUV)
c.imshow('Result3',nimg2)
c.waitKey(0)
nimg3=c.cvtColor(img,c.COLOR_BGR2Lab)
c.imshow('Result4',nimg3)
c.waitKey(0)
c.destroyAllWindows()


![image](https://user-images.githubusercontent.com/72264974/104430674-01a18d80-55ad-11eb-9b7f-f6e4e71994b2.png)
![image](https://user-images.githubusercontent.com/72264974/104430743-1847e480-55ad-11eb-9226-2946fbba2d4e.png)
![image](https://user-images.githubusercontent.com/72264974/104430862-40374800-55ad-11eb-8d62-065f46c18199.png)
![image](https://user-images.githubusercontent.com/72264974/104430986-64932480-55ad-11eb-8b4f-d3b9eee45c0f.png)
![image](https://user-images.githubusercontent.com/72264974/104431067-7b397b80-55ad-11eb-8971-60104cea5f1e.png)

Program6:
Develop a program to create an image from 2D array (generate an array of random size).


import cv2 as c
import numpy as np
from PIL import Image
array = np.zeros([100, 200, 3], dtype=np.uint8)
array[:,:100] = [255, 130, 0] 
array[:,100:] = [0, 0, 255]
img = Image.fromarray(array)
img.save('image1.png')
img.show()
c.waitKey(0)


![image](https://user-images.githubusercontent.com/72264974/104431674-2b0ee900-55ae-11eb-8acc-2ea47fe110ce.png)

