# **Finding Lane Lines on the Road** 

## Table of contents

---

1. Flow of processing  
  1.1 Color selection  
  1.2 Gray scalling  
  1.3 Gaussian smoothing  
  1.4 Canny edge detection  
  1.5 Masked by region  
  1.6 Hough transform line detection  
  1.7 Draw pipe lines  

2. Especially examined points  
  2.1 Length weight addition
  2.2 Set slope criteria

3. Conclusion


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

## 1. Flow of processing

### 1.1 Color selection  

Load and examine the following image 

[//]: # (Image References)

[image1]: ./examples/0.png "Original image"

### 1.2 Gray scalling  

[//]: # (Image References)

[image1]: ./examples/1.png "Gray scale image"

### 1.3 Gaussian smoothing  

[//]: # (Image References)

[image1]: ./examples/1.png "Gray scale image"

### 1.4 Canny edge detection  
[image1]: ./examples/1.png "Gray scale image"

### 1.5 Masked by region  
[image1]: ./examples/1.png "Gray scale image"

### 1.6 Hough transform line detection  
[image1]: ./examples/1.png "Gray scale image"

### 1.7 Draw pipe lines  
[image1]: ./examples/1.png "Gray scale image"



### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I .... 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by ...

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when ... 

Another shortcoming could be ...


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...
