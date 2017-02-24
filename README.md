#**Finding Lane Lines on the Road**

##Writeup Template

###You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 8 steps.

step 1   Read in and grayscale the image
step 2   Define a kernel size and apply Gaussian smoothing
step 3   Define parameters for Canny and apply to get edges image
step 4   Mask edges image using region_of_interest() (ignore everything outside region of interest)
step 5   Define Hough transform parameters and run Hough transform on masked edge-detected image
step 6   Draw line segments
step 7   Draw lines extrapolated from line segments
step 8   Combine line image with original image to see how accurate the line annotations are.

I have tried two methods for doing the extrapolation

1. Averaging the lines
2. Using scipy.stats.linregress for finding out the line regression

For me line regression doesn;t work fine. so I opt to averaging the line and choose the slope which are 1.5 standard deviation from greater then mean slope. Also I choose lines which are greater then 50 in length.

###2. Identify potential shortcomings with your current pipeline

For challenging video, not able to consider the bumper of the car.
Has to take care of the Tree shadows as well.

###3. Suggest possible improvements to your pipeline

Need to take curve as well
One possible improvement would be considering better region of interest which is not dependent on the particular size of image.
