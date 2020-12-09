
# **Finding Lane Lines on the Road** 


---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./test_images_output/Step1_gray_img.jpg "GrayScale"
[image2]: ./test_images_output/Step2_Gaussian_blur_img.jpg "GraussianBlur"
[image3]: ./test_images_output/Step3_Canny_img.jpg "CannyEdge"
[image4]: ./test_images_output/Step4_masked_Canny_img.jpg "CannyMasked"
[image5]: ./test_images_output/Step5_Hough_Transformed_img.jpg "HoughTransform"
[image6]: ./test_images_output/Step6_Super_Imposed_img.jpg "LaneLine"



---

### Reflection

My pipeline consisted of 6 steps as follows


#### Step 1. Convert Input image to Grayscale

First, we converted the source image to Grayscale

![image1]

#### Step 2 : Apply Gaussian Blur

Then we applied Gaussian Blur to reduce image noise and reduce detail reduce unwanted edge detection

![image2]

#### Step 3 : Edge detection using Canny Edge Detector 

This was followed with use of Canny Edge Detecion Algorithm to extract all the edges

![image3]

#### Step 4 : Find the Region of Interest

With the Cannied Image, we find the Region of Interest and mask the remaining portion

![image4]

#### Step 5 : Detect lanes lines using Hough's Transform

In this step, we apply Hough's transform to find the lines which satisfy as lane lines.
For all such found lines, omitting the ones having slope out of bounds, we classify the remaining as either left lane line or right lane line.

We then get the slope and intecepts for all the left lane lines and calculate the average slope and intecept. The same is done for all the right lane lines as well. Using the average intercept and slope, we fit in a line , which would be the calulated lane line.


![image5]

#### Step 6 : Superimpose the lane lines on the original image

We then superimpose the lane lines calulated from step 5 over the original image.

![image6]



### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be that if the curvature of the slope exceeds a paritular threshold, there would be no lane lines drawn.

Another shortcoming could be that the parameters considered for Canny Edge Detection, Hough's Transform, Region of Interest are static and could lead to scenarios where lanes might not be detected correctly.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to using CNN to calculate the Region of Interest Dynamically.

Another potential improvement could be to calculate and fit in the lane lines to accomodate the curvature of the road.

