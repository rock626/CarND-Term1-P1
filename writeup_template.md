#**Finding Lane Lines on the Road** 

##Writeup Template

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"
[image1]: ./examples/grayscale.jpg "mask"
[image1]: ./examples/grayscale.jpg "Blur"
[image1]: ./examples/grayscale.jpg "edge"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. First, I converted the images to grayscale, then I did the following steps:

1.convert image to grayscale
2.convert image to hsv and filter yellow,white regions using a mask
3.apply mask on grayscale image
4.apply gaussian blur 
5.apply canny edge detection using thresholds
6.draw hough lines by specifing region of interest and hough transform parameters
7.use weighted_img to draw a transparent line

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by:
	1. calculate slope and use it differentiate between left and right lanes
	2. use 'polyfit' function to extrapolate left and right lanes


