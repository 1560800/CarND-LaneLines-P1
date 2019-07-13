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

![png](examples/0.png)
### 1.2 Color selection  
I performed the following to extract the yellow line on the white road of the challenge.
```python
def yellow_white_extraction(img):

    yellow_white_image = np.copy(img)
    red_threshold = 80
    green_threshold = 180
    blue_threshold = 20
    rgb_threshold = [red_threshold, green_threshold, blue_threshold]
    
    thresholds = (img[:,:,0] < rgb_threshold[0]) \
                | (img[:,:,1] < rgb_threshold[1]) \
                | (img[:,:,2] < rgb_threshold[2])
    yellow_white_image[thresholds] = [0,0,0]
    
    return  yellow_white_image
```
![png](examples/1.png)

### 1.3 Gray scalling  
I used cv2.cvtColor to gray scalling.  
![png](examples/2.png)

### 1.4 Gaussian smoothing  
I used cv2.GaussianBlur to gaussian smoothing.  
![png](examples/3.png)

### 1.5 Canny edge detection 
I used cv2.Canny to detect edges.  
![png](examples/4.png)

### 1.6 Masked by region  
I used cv2.fillPoly to masked by region. 
Actually, only the inside of the yellow frame in the photo below remains, and the rest is masked black.  
![png](examples/5.png)

### 1.7 Hough transform line detection 
I used cv2.HoughLinesP to make hough transform lines.  
The edges extracted only this time were made colorful to make them easy to understand.  
![png](examples/6.png)

### 1.8 Draw pipe lines  
The slope and intercept of the line segment were calculated from the coordinates of the extracted edge.  
If the slope is negative then it is the left lane, if it is positive it is the right lane.  
Refer Chapter 2 for details on combining slopes and intercept groups to create a single pipeline.  
![png](examples/7.png)

---

## 2. Especially examined points  

### 2.1 Length weight addition  
The method of averaging only slope and intercept of the extracted edge has a large error.  
The influence of lope and intercept is equal for long lines and short lines,  
but long lines have small errors and short lines have large errors.  
Apply weighting to each slope and intercept in proportion to the total length of edge,  
and improve them by combining them.
![png](examples/21.png)

### 2.2 Set slope criteria  
We need to remove edges other than lanes, such as building shadows.  
As one of the judgment criteria, the slope close to the horizon has a high possibility of a dummy other than the lane,  
so we set criteria of the slope.
As for the criteria of inclination, it was judged as NG if the angle is shallower  
than the line connecting the lower corner of the screen from the vanishing point.  
![png](examples/23.png)

## 3. Conclusion
This project was successful because the video images clearly show the lane lines are detected properly and lines are smoothly processed.

This straight line detection feature is very effective on long straight roads. However, under practical circumstances, limitations may be necessary due to the possibility of false detection of weather (any tire marks on snow road) , long shadows of buildings projected diagonally or road cracks etc.

In addition, since the position of the vanishing point greatly moves in the frame in the case of a steep curve or a steep up-down road such as a mountain road, another algorithm must be used in line detection.
