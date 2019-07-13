# **Finding Lane Lines on the Road** 

## Table of contents

---

1. Flow of processing  
  1.1 Load original images  
  1.2 Color selection  
  1.3 Gray scalling  
  1.4 Gaussian smoothing  
  1.5 Canny edge detection  
  1.6 Masked by region  
  1.7 Hough transform line detection  
  1.8 Draw pipe lines  

2. Especially examined points  
  2.1 Length weight addition  
  2.2 Set slope criteria

3. Conclusion


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

## 1. Flow of processing


### 1.1 Original images  
Load and examine the following image
![png](examples/0.png)

### 1.2 Color selection  
![png](examples/1.png)

### 1.3 Gray scalling  
![png](examples/2.png)

### 1.4 Gaussian smoothing  
![png](examples/3.png)

### 1.5 Canny edge detection  
![png](examples/4.png)

### 1.6 Masked by region  
![png](examples/5.png)

### 1.7 Hough transform line detection  
![png](examples/6.png)

### 1.8 Draw pipe lines 
![png](examples/7.png)

---

## 2. Especially examined points  

### 2.1 Length weight addition  

![png](examples/21.png)

### 2.2 Set slope criteria  

![png](examples/22.png)

## 3. Conclusion
This project was successful because the video images clearly show the lane lines are detected properly and lines are smoothly processed.

This straight line detection feature is very effective on long straight roads. However, under practical circumstances, limitations may be necessary due to the possibility of false detection of weather (any tire marks on snow road) , long shadows of buildings projected diagonally or road cracks etc.

In addition, since the position of the vanishing point greatly moves in the frame in the case of a steep curve or a steep up-down road such as a mountain road, another algorithm must be used in line detection.

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
