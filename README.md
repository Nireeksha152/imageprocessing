# imageprocessing
Program1:
Develop a program to display grayscale image using read and write operation.

GRAY SCALING:
   Grayscaling is the process of converting an image from other color spaces e.g RGB, CMYK, HSV, etc. to shades of gray. It varies between complete black and complete white.
      
cv2.imread() this method loads an image from specified file.
cv2.imwrite() this method is use to write the image.
cv2.cvtColor() this method is used to convert an image from one color space to another.
cv2.destroyAllWindows() If we have multiple window open and we donot need those to be open we can use this method to close those all
cv2.waitKey(0) this metjod will display the output window infinetely until any key is pressed
cv2.imshow() method is used to display an image in a window. The window automatically fits to the image size.


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

program2: 
  Develop the program to perform linear transformation on a image:Scaling and Rotation.
  Linear transformation:
        Piece-wise linear transformation is type of gray level transformations that is used for image enhancement.It is an spatial domain method.It is used for manipulation of 
an image so the result is more suitable than the original for specific application.        
Rotation of the Image:
   The image can be rotated in various angles(90,180,270 and 360).OpenCV calculates the affine matrix that performas affine transformation ,which mean it doesnot preserves the
rotation of distance between points lying on the lines.
Scaling:
    Image resizing refers to the scaling of images.It helps in reducing the number of pixel from an image and that has several advantages.Resizing an image means changing  the
  dimension of it  by changing its width alone,height alone or both.
  
  
  
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
output:
![image](https://user-images.githubusercontent.com/72264974/104427897-cd789d80-55a9-11eb-8b58-fc30ebb79696.png)
![image](https://user-images.githubusercontent.com/72264974/104427983-e719e500-55a9-11eb-9128-3d181381ae76.png)
........
Program3:Develop a program to find the sum and mean of a set of images. 
 a.Create ‘n’ number of images and read them from the directory and perform the operations.
Mean:
   'mean' value gives the contribution of individual pixel intensity for the entire image & variance is normally used to find how each pixel varies from the neighbouring pixel (or centre pixel) and is used in classify into different regions

The OS module in python provides functions for interacting with the operating system. OS, comes under Python’s standard utility modules. This module provides a portable way of using operating system dependent functionality. The *os* and *os.path* modules include many functions to interact with the file system.



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

output:
![image](https://user-images.githubusercontent.com/72264974/104429624-d8ccc880-55ab-11eb-9179-5e7f2a085c6c.png)
![image](https://user-images.githubusercontent.com/72264974/104429716-f26e1000-55ab-11eb-9aaf-2f65bb506309.png)
......

Program4:
Develop the program to convert color image to gray image and binary image.
Gray Image:
  Grayscale is a range of monochromatic shades from black to white. Therefore, a grayscale image contains only shades of gray and no color.
Many image editing programs allow you to convert a color image to black and white, or grayscale. This process removes all color information, leaving only the luminance of each pixel. Since digital images are displayed using a combination of red, green, and blue (RGB) colors, each pixel has three separate luminance values. Therefore, these three values must be combined into a single value when removing color from an image.

Binary Image:
   A binary image is the type of image where each pixel is black or white.Binary images are images whose pixels have only two possible intensity values they normally displayed as black and white ,numerically the two values are often 0 for black and either 1 or 255 for  white.binary image  are often produced by thresholding a grayscale or color image in order to separate  an object in the image from background.
 cv2.threshold():. For every pixel, the same threshold value is applied. If the pixel value is smaller than the threshold, it is set to 0, otherwise it is set to a maximum value. The function cv.threshold is used to apply the thresholding. The first argument is the source image, which should be a grayscale image. The second argument is the threshold value which is used to classify the pixel values. The third argument is the maximum value which is assigned to pixel values exceeding the threshold . 
   
   
   
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
output:

![image](https://user-images.githubusercontent.com/72264974/104430258-73c5a280-55ac-11eb-98a9-f26728982392.png)
![image](https://user-images.githubusercontent.com/72264974/104430305-82ac5500-55ac-11eb-8ade-7f4d35fe1999.png)
![image](https://user-images.githubusercontent.com/72264974/104430363-95bf2500-55ac-11eb-812a-3e65f7eca34c.png)
........

Program5:Develop the program to change the image to different color spaces.
Color spaces in Opencv:
Color spaces are a way to represent the color channels present in the image that gives the image that particular hue. There are several different color spaces and each has its own significance.Some of the popular color spaces are RGB (Red, Green, Blue), CMYK (Cyan, Magenta, Yellow, Black), HSV (Hue, Saturation, Value).
cv2.imread() this method loads an image from specified file.
c.cvtColor(img,c.COLOR_BGR2HSV): used to convert BGR color space to HSV color spaces
c.cvtColor(img,c.COLOR_BGR2RGB):used to convert BGR color space to RGB color spaces
 c.cvtColor(img,c.COLOR_BGR2LUV):used to convert BGR color space to LUV color spaces
 c.cvtColor(img,c.COLOR_BGR2Lab):used to convert BGR color space to Labcolor spaces
 cv2.destroyAllWindows() If we have multiple window open and we donot need those to be open we can use this method to close those all
cv2.waitKey(0) this metjod will display the output window infinetely until any key is pressed
cv2.imshow() method is used to display an image in a window. The window automatically fits to the image size.

#code

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

output:
![image](https://user-images.githubusercontent.com/72264974/104430674-01a18d80-55ad-11eb-9b7f-f6e4e71994b2.png)
![image](https://user-images.githubusercontent.com/72264974/104430743-1847e480-55ad-11eb-9226-2946fbba2d4e.png)
![image](https://user-images.githubusercontent.com/72264974/104430862-40374800-55ad-11eb-8d62-065f46c18199.png)
![image](https://user-images.githubusercontent.com/72264974/104430986-64932480-55ad-11eb-8b4f-d3b9eee45c0f.png)
![image](https://user-images.githubusercontent.com/72264974/104431067-7b397b80-55ad-11eb-8971-60104cea5f1e.png)

........
Program6:
Develop a program to create an image from 2D array (generate an array of random size).
 A image is an array or a matrix of squarepixe arranged in column and rows.
 2D arary means an array of arrays in this type of array the position of an data elements is refered by two indicies instead of one.
 PIL: Python Imaging Library (abbreviated as PIL) (in newer versions known as Pillow) is a free and open-source additional library for the Python programming language that        adds support for opening, manipulating, and saving many different image file formats. 
 The numpy.zeros() function returns a new array of given shape and type, with zeros.
 cv2.waitKey(0) this metjod will display the output window infinetely until any key is pressed
 
 #code
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
output:

![image](https://user-images.githubusercontent.com/72264974/104431674-2b0ee900-55ae-11eb-8acc-2ea47fe110ce.png)
...........
program7: program to  display the neighbouhood elements of  matrix:

import numpy as np
i=0
j=0
a= np.array([[1,2,3,4,5], [2,3,4,5,6],[3,4,5,6,7],[4,5,6,7,8],[5,6,7,8,9]])
print("a :\n",str(a))
def neighbors(radius, rowNumber, columnNumber):
     return [[a[i][j] if  i >= 0 and i < len(a) and j >= 0 and j < len(a[0]) else 0
                for j in range(columnNumber-1-radius, columnNumber+radius)]
                    for i in range(rowNumber-1-radius, rowNumber+radius)]
neighbors(1, 2, 3)
 ......
 output:
  a :
 [[1 2 3 4 5]
 [2 3 4 5 6]
 [3 4 5 6 7]
 [4 5 6 7 8]
 [5 6 7 8 9]]
[[2, 3, 4], [3, 4, 5], [4, 5, 6]]

 ...........
 Program 8:Program to find the sum  of neighbour values in  a matrix:
   
import numpy as np

M = [[1,2,3,4,5], [2,3,4,5,6],[3,4,5,6,7],[4,5,6,7,8],[5,6,7,8,9]]

M = np.asarray(M)
N = np.zeros(M.shape)

def sumNeighbors(M,x,y):
    l = []
    for i in range(max(0,x-1),x+2): 
        for j in range(max(0,y-1),y+2):
            try:
                t = M[i][j]
                l.append(t)
            except IndexError: 
                pass
    return sum(l)-M[x][y]

for i in range(M.shape[0]):
    for j in range(M.shape[1]):
        N[i][j] = sumNeighbors(M, i, j)

print ("Original matrix:\n", M)
print ("Summed neighbors matrix:\n", N) 
....
output:
 Original matrix:
 [[1 2 3 4 5]
 [2 3 4 5 6]
 [3 4 5 6 7]
 [4 5 6 7 8]
 [5 6 7 8 9]]
Summed neighbors matrix:
 [[ 7. 13. 18. 23. 15.]
 [13. 24. 32. 40. 27.]
 [18. 32. 40. 48. 32.]
 [23. 40. 48. 56. 37.]
 [15. 27. 32. 37. 23.]]
 ...........
 
 
 **program 9:
 program to overload the operators:**
 

#include <iostream>
using namespace std;
class matrix
{
 int r1, c1, i, j, a1;
 int a[10][10];

public:int get()
 {
  cout << "Enter the row and column size for the  matrix\n";
  cin >> r1;
  cin >> c1;
   cout << "Enter the elements of the matrix\n";
  for (i = 0; i < r1; i++)
  {
   for (j = 0; j < c1; j++)
   {
    cin>>a[i][j];

   }
  }
 
 
 };
 void operator+(matrix a1)
 {
 int c[i][j];
  
   for (i = 0; i < r1; i++)
   {
    for (j = 0; j < c1; j++)
    {
     c[i][j] = a[i][j] + a1.a[i][j];
    }
   
  }
  cout<<"addition is\n";
  for(i=0;i<r1;i++)
  {
   cout<<" ";
   for (j = 0; j < c1; j++)
   {
    cout<<c[i][j]<<"\t";
   }
   cout<<"\n";
  }

 };

  void operator-(matrix a2)
 {
 int c[i][j];
  
   for (i = 0; i < r1; i++)
   {
    for (j = 0; j < c1; j++)
    {
     c[i][j] = a[i][j] - a2.a[i][j];
    }
   
  }
  cout<<"subtraction is\n";
  for(i=0;i<r1;i++)
  {
   cout<<" ";
   for (j = 0; j < c1; j++)
   {
    cout<<c[i][j]<<"\t";
   }
   cout<<"\n";
  }
 };

 void operator*(matrix a3)
 {
  int c[i][j];

  for (i = 0; i < r1; i++)
  {
   for (j = 0; j < c1; j++)
   {
    c[i][j] =0;
    for (int k = 0; k < r1; k++)
    {
     c[i][j] += a[i][k] * (a3.a[k][j]);
    }
  }
  }
  cout << "multiplication is\n";
  for (i = 0; i < r1; i++)
  {
   cout << " ";
   for (j = 0; j < c1; j++)
   {
    cout << c[i][j] << "\t";
   }
   cout << "\n";
  }
 };

};

int main()
{
 matrix p,q;
 p.get();
 q.get();
 p + q;
 p - q;
 p * q;
return 0;
}

 **output:**
 
 Enter the row and column size for the  matrix
2
2
Enter the elements of the matrix
7
5
6
9
Enter the row and column size for the  matrix
2
2
Enter the elements of the matrix
4
5
6
1
addition is
 11	10	
 12	10	
subtraction is
 3	0	
 0	8	
multiplication is
 58	40	
 78	39	
 
 
 
 
 
 
 
