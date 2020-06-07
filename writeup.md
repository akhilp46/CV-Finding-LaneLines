# **Finding Lane Lines on the Road** 

The goal of this project is to make a pipeline that finds lane lines on the road.

[//]: # (Image References)

[image1]: ./test_images/solidWhiteCurve.jpg "Og"
[image2]: ./test_images/gray1.jpg "Grayscale"
[image3]: ./test_images/canny1.jpg "CannyTransform"
[image4]: ./test_images/result.jpg "AnnotatedImage"

---
My pipeline consists of the following. First, I convert the image to grayscale, then I blur the image a bit using a Gaussian Noise kernal. 
Original Image          |  Grayscale
:----------------------:|:-----------------------:
![alt-text][image1]   |  ![alt-text][image2]

A Canny transform is performed to highlifght several lines and edges in the image. 

Canny Transform         | 
:----------------------:|
![alt-text][image3]   | 

Second, a 'region of interest' is established in front of the vehicle, where on would expect lane lines on the road. Finally, a hough line transform is performed to find points corresponding to long partially continuous lines within the region of interest. These points are then used to determine which points/lines belong to the left or right side of the lane. Once seperated, points/lines are averaged among their respective sides to figure out the average slope and intercept of the line for each side. Using the slope and intercept of the left and right lines, they are draw on top of the original image. 

Result                  | 
:----------------------:|
![alt-text-1][image4]   | 

One potential shortcoming could be when a car or some other object is in the region of interest. The pipeline could potenitally highlight some lines on the car or object in this region. To fix this, some more calibration/refinement of the parameters choose for the Canny transform and hough lines transform need to be done. Another potential shortcoming would be the poor performance of the pipeline for curved roads. The Hough Lines transform only spits out straight lines, therfore, depending on the region of interest, the annotated lines might shoot past the curve of the lanes.

A possible improvement would be to develop a better way to detect lanes that curve. Another improvement might be to make the region of interest a bit more dynamic. As it is currently coded, the lines are only detect in a specific trapezoid in from the bottom of the image. This would work for another image with a different resolution

