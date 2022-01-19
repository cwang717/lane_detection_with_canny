# **Finding Lane Lines on the Road** 

## Writeup Template

### You can use this file as a template for your writeup if you want to submit it as a markdown file. But feel free to use some other method and submit a pdf if you prefer.

---

**Finding Lane Lines on the Road**

The goals / steps of this project are the following:
* Make a pipeline that finds lane lines on the road
* Reflect on your work in a written report

---

### Reflection

### 1. Describe your pipeline. As part of the description, explain how you modified the draw_lines() function.

My pipeline consisted of 5 steps: 
1. Convert the image to a grayscale one.
2. Apply Gaussian smoothing to the graycale image to suppress noise.
3. Use Canny algorithm to detect edges on the smoothed grayscale image.
4. Filter out the edges out of our interested region.
5. Plot the edges onto the original image.

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by catogorizing the remaining edges after step 4 based on whether their slopes are positive or negative. Then in each group, I fited the ends of the edges with a line to average their slopes and extrapolated to the top and bottom of the region of interest. 

### 2. Identify potential shortcomings with your current pipeline


One potential shortcoming would be what would happen when the road is curved, the straight lane mark lines do not fit the real lane marks well.  

Another shortcoming could be the vulnerability to noise resulted from tree shadows, dirt stains on the road surface, and color difference of different road segments. 


### 3. Suggest possible improvements to your pipeline

A possible improvement would be to average the lane mark postions in the most recent frames (e.g., 5 frames) to add more robustness to current lane mark detection. Since there are some temporal continuities in real-world videos, the lane mark positions in the most recent frames can provide relavent information especially when the current frame is of much noise. 

Another potential improvement could be to add weights relavent to the edge length to edges remaining after step 4 before averaging their positions. It can help reduce the impact of noise, which are usually shorter edges. 
