# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 

First, I converted the images to grayscale, 
Second, obtained edge of object from grayscale image using Canny Edge detection.
thid, select the possible region which contain the only line
forth, determine the long line by using hough transformation
Finally, combine the determin line with the original image 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function
first I initialized left point for left slope and right point for right slope which is smaller then or bigger then expected value.
And while going through loop, try to located the smallest x-axis point for left slope and the biggest xaxis point for right slope.
Once it located the point, it replace with new initialized point. 
Once it complete the loop, using the info for two point, I drew the line. But if the starting point of the line is greater then for left slope or lesser then for right slope, I used the hight of the image to extend the line before drow the line on to the image.

If you'd like to include images to show how the pipeline works, here is how to include an image: 

[image1] : ./test_images_output/solidWhiteCurve.jpg "solidWhiteCurve"
[image1] : ./test_images_output/solidWhiteRight.jpg "solidWhiteRight"
[image1] : ./test_images_output/solidYellowCurve.jpg "solidYellowCurve"
[image1] : ./test_images_output/solidYellowCurve2.jpg "solidYellowCurve2"
[image1] : ./test_images_output/solidYellowLeft.jpg "solidYellowLeft"
[image1] : ./test_images_output/whiteCarLaneSwitch.jpg "whiteCarLaneSwitch"


### 2. Identify potential shortcomings with your current pipeline

when I draw_line, I used fixed value to manully extend the line. So when the hough line doesn't meet it could end up unexpected line.
So when I ran though stream of image (video), I was able to identify some moment, my program wasn't able to determine the line property.


### 3. Suggest possible improvements to your pipeline

I need spend more time to figure it out to draw_line and debug other possible scenario. 
Such as when the car was driving through curve with various different object such as city.
I think the canny edge could identify the object in stead of line.

and when the driver goes up hill or down hill, the possible region could be change.
So the program should have better way to identify the possible region.

