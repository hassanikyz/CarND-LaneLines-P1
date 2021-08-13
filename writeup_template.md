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

My pipeline consisted of 6 steps. 
1. Image is first converted to grayscale, this enables quicker edge detection (colors changing from white to black/gray is easier than in RGB pixels) 
2. Suppressed noise and spurious gradients by averaging pixels via gaussian blur
3. Edge detection
4. Define a region of interest so as to remove extra edges which are likely not part of lanes on the road
5. Drawing lines on an image in diff color (in this case red) where lanes are detected
6. Adding this image on top of the original image to mark the lanes

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by 
1. Segregated lines which are left and right using positive and negative gradient as key
2. Use longest line/edge as proxy for the entire lane
3. Extended the longest line up and down to mark it as lane

If you'd like to include images to show how the pipeline works, here is how to include an image: 

![alt text][image1]


### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be when lanes are curved and not straight, code treats all lanes as straight line


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to connect individual pieces of the lanes detected via edge detection by sorting them in a way lane fidelity remains. This can potentially make it work on curved lanes too.


