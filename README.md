# Finding Lane Lines on the Road

![Application of pipeline2](https://github.com/BrunoEduardoCSantos/Finding-lane-lines-on-the-road/blob/master/test_output_images/messigraysolidWhiteCurve.jpg.png)

## Overview

In this project several computer vision techniques are applied to detect lanes on the read and draw lines fitting them.

## Usage

**Step 1:** Set up [Anaconda](https://docs.anaconda.com/anaconda/install/) with OpenCV

**Step 2:** Open the P1.ipynb in a Jupyter Notebook (Python 3.5)

**Step 3:** Run the notebook

## Implementation
### Image processing pipeline

1. Apply gray scale to the initial image
2. Use [Gaussian blur](http://www.bogotobogo.com/OpenCV/opencv_3_tutorial_imgproc_gausian_median_blur_bilateral_filter_image_smoothing.php) technique to distinct the white lanes and input to canny edge method
3. Apply [Canny edge method](https://www.wikiwand.com/en/Canny_edge_detector) to find the edges in the image
4. Apply a mask to spot only the lanes
5. Use [Hough transformation](https://www.wikiwand.com/en/Hough_transform) to obtain the most suitable lines passing over the edges 
6. Obtain fitting lines 

### Fitting line implementation 
In order to draw a single line on the left and right lanes, I modified the ** draw_lines()** function by separating into positive and negative slope . Besides filter into two branches of positive/negative slope, I apply a range of acceptable values for slope according to the plot of all possible hough lines. This range was within [0.4, 0.95] for positive slopes and [-0.95,-0.4] for negative slopes. Afterwards, I evaluate the average slope for left and right lines (positive/negative slopes) in order to find a single line for both cases. Finally, using simple linear equation  y = mx +b , I obtained the parameter b as well as extrapolate the right and left lines.

