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

My pipeline includes 2 main steps: extract lane lines from a image and combine the lanes and the image together.

#### Step 1: Extract lane lines

**step 1.1 Extract lines**

In `get_lines` function:

1. convert the image to grayscale
2. apply gaussian smoothing
3. apply Canny
4. create a masked image
5. run Hough on edge detected image

**step 1.2 Smooth lines**

In `average_lines` function:

1. filter lines by angle with y-axis and locations in the image
2. transform filtered lines into Hough space where each line corresponds to a dot
3. get average values of dots in Hough space
4. transform the dot in Hough space into a line in normal space

### Output of Step 1

In the output of cell 6, I list all six images labeled by lane lines and the region of interest.

### 2. Identify potential shortcomings with your current pipeline

The generated lane lines sometimes sway slightly around the exact position of lane lines. 


### 3. Suggest possible improvements to your pipeline

One possible solution is to enchance the `average_lines` algorithm. 
We can select some dots from each line segment and do linear regression to get a wide-enough line which covers most of the dots.
