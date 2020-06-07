# **Finding Lane Lines on the Road** 

The goal of this project is to make a pipeline that finds lane lines on the road.
---

My pipeline consistes of the following. First, I convert the image to grayscale, then I blur the image a bit using a Gaussian Noise kernal. A Canny transform is performed to highlifght several lines and edges in the image. Second, a 'region of interest' is established in front of the vehicle, where on would expect lane lines on the road. Finally, a hough line transform is performed to find points corresponding to long partially continuous lines within the region of interest. These points are then used to determine which points/lines belong to the left or right side of the lane. Once seperated, points/lines are averaged among their respective sides to figure out the average slope and intercept of the line for each side. Using the slope and intercept of the left and right lines, they are draw on top of the original image. 

