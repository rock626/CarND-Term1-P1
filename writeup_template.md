**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_output/grayscale.png "Grayscale"
[image2]: ./test_output/Hsv_filter.png "mask"
[image3]: ./test_output/Blur_Gray.png "Blur"
[image4]: ./test_output/Canny.png "edge"
[image5]: ./test_output/out_solidWhiteCurve.jpg "test_output"
[image6]: ./test_output/Out.png "All"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I did the following steps:

1.convert image to grayscale
![alt text][image1]
2.convert image to hsv and filter yellow,white regions using a mask
3.apply mask on grayscale image
![alt text][image2]
4.apply gaussian blur 
![alt text][image3]
5.apply canny edge detection using thresholds
![alt text][image4]
6.draw hough lines by specifing region of interest and hough transform parameters
7.use weighted_img to draw a transparent line
![alt text][image5]

For all test images, here is the output after passing through the pipeline:
![alt text][image6]

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by:
	1. calculate slope and use it differentiate between left and right lanes
	2. use 'polyfit' function to extrapolate left and right lanes

### 2. Identify potential shortcomings with your current pipeline

For solid white right, i didnt see any issues and lane detection is smooth.
For solid yellow left,one potential shortcoming would be what would happen the lanes are not smooth and in some of the frames, detected lane lines are distorted.

### 3. Suggest possible improvements to your pipeline

A possible improvement would be to take average of slope over last n frames and use that slope when a bad frame is encountered.
