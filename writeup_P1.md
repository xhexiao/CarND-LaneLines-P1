**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

###1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 6 steps:

1. I converted the images to grayscale
2. then I applied the Gaussian smoothing to the image
3. in this step I used the Canny transform to detect the edges in the image
4. after I defined the vertices of a polyon mask, I ran the "region_of_interest" function to filter out the rest of the image to 		make sure that only the road surface ahead 
5. running the "hough_lines" function provided, I selected only the lines out of all the "edges" I got from the step 3 and by setting the adjusting different arguments I made sure only lane lines are being selected; further, the lanes lines are drew out in red
6. in this last step, I overlap this image of red lane lines and black backround over the original image


In order to draw a single line on the left and right lanes, I modified the draw_lines() function by grouping the lanes detected by the Hough transform into two seperate arrays, since right lanes and left lanes have different slopes. In each group, I took out the outliers by narrowing down the value of the slope. And I calculated the intercepts for the rest of the lane lines and also took out some of the outliers to make sure that what has left is plausible. Since I only need one continuous line for each lane, namely one slope and one intercept respectively, I got the median value from the arrays and give them to my final lane lines. Following is the comparison of using the original draw_lines() function and the modified one:


[image2]: ./examples/lane_detection.jpg "Lane Detection"
[image3]: ./examples/lane_detection.jpg "Lane Detection_modified"


###2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when 

Another shortcoming could be ...


###3. Suggest possible improvements to your pipeline

A possible improvement would be to ...

Another potential improvement could be to ...