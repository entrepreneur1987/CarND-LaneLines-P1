# **Finding Lane Lines on the Road** 

## Writeup Template


---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
- Make a pipeline that finds lane lines on the road
- Reflect on your work in a written report


[//]: # (Image References)

[image1]: ./examples/grayscale.jpg "Grayscale"

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps. 

In the first step, I converted the images to grayscale, then I blur it using *gaussian_blur* and got edges out of it using canny method.

In the second step, I got masked edges using the default vertices.

In the third step, I got hough lines using *get_hough_lines* helper method.

In the fourth step, I calculated solid lines by average slopes and exclude noises (those lines with their slopes outside normal range).

In the last step, I handled an important corner case which is left/right lines are crossing each other (challenge.mp4) by recalculating the top points of both left/right lanes.

Instead of modifing *draw_lines()* method, I implemented my own to support more complex challenges. 


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be when there are a lot of noises, it's not able to detect the exact lanes we want. This happens in challenge.mp4, when there are trees on the left, sometimes it failed to detect the lane.


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to do more calculation to exclude more noises.
