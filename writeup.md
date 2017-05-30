# **Finding Lane Lines on the Road** 

## Writeup

### Finding Lane Lines on the Road

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"
[image_105_original]: ./test_images/105.jpg "Image_105.jpg"
[image_105_blurred_gray]: ./test_images_output/105_blurred_gray.jpg "Blurred_gray"
[image_105_bounded_edges]: ./test_images_output/105_bounded_edges.jpg "Bounded edges"
[image_105_edges]: ./test_images_output/105_edges.jpg "Edges"
[image_105_gamma_corrected]: ./test_images_output/105_gamma_corrected.jpg "Gamma corrected"
[image_105_gray]: ./test_images_output/105_gray.jpg "Gray"
[image_105_lines]: ./test_images_output/105_lines.jpg "Lines"
[image_105_white]: ./test_images_output/105_white.jpg "White"
[image_105]: ./test_images_output/105.jpg "Processed"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 8 steps.
First, I made sure that image is in appropriate format,
![alt text][image_105_original]
then I transformed all yellow colors to solid white in order to make them clearly visible,
![alt text][image_105_white]
then I adjusted gamma in order to avoid shadows and bright images,
![alt text][image_105_gamma_corrected]
then I converted the images to grayscale,
![alt text][image_105_gray]
then I applied gaussian in order to filter noise,
![alt text][image_105_blurred_gray]
then I did canny edge detection,
![alt text][image_105_edges]
then selected region of interest
![alt text][image_105_bounded_edges]
and finally applied hough line detection algorithm.
![alt text][image_105_lines]
![alt text][image_105]

In order to draw a single line on the left and right lanes, I implemented the draw_lines_averaged_and_extrapolated() function. It does averaging and extrapolation of the line segments detected by pipeline.


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when not white and yellow line will appear. 

Another shortcoming could be if scale on video will be too panoramic as a result parts of left lane will be hard to distinguish from parts of right lane.

Also, winding lane can not be good extrapolatated by single line.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to use higher order polinomial extrapolation for lane lines.

Another potential improvement could be to use clever techinque (perhaps some sort of clustering) in order to separate parts of left lane from parts of right lane (using slope is not good, since lane might be jaggy)

Additionally, it is possible to try to use linear regression to approximate lanes.
