# **Finding Lane Lines on the Road** 

## Writeup

### Finding Lane Lines on the Road

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 8 steps. First, I made sure that image is in appropriate format, then I transformed all yellow colors to solid white in order to make them clearly visible, then I adjusted gamma in order to avoid shadows and bright images, then I converted the images to grayscale, then I applied gaussian in order to filter noise, then I did canny edge detection, then selected region of interest and finally applied hough line detection algorithm. 

In order to draw a single line on the left and right lanes, I implemented the draw_lines_averaged_and_extrapolated() function. It does averaging and extrapolation of the line segments detected by pipeline.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when not white and yellow line will appear. 

Another shortcoming could be if scale on video will be too panoramic as a result parts of left lane will be hard to distinguish from parts of right lane.

Also, winding lane can not be good extrapolatated by single line.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use higher order polinomial extrapolation for lane lines.

Another potential improvement could be to use clever techinque (perhaps some sort of clustering) in order to separate parts of left lane from parts of right lane (using slope is not good, since lane might be jaggy)

Additionally, it is possible to try to use linear regression to approximate lanes.
