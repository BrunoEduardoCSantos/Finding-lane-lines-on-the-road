# Finding Lane Lines on the Road 

In this project several computer vision techniques are applied to detect lanes on the read and draw lines fitting them.

## Reflection

My pipeline consisted of 5 steps as follows:
1. Apply gray scale to the initial image
2. Use Gaussian blur technique to distinct the white lanes and input to canny edge method
3. Apply Canny edge method to find the edges in the image
4. Apply a mask to spot only the lanes
5. Use Hough transformation to obtain the most suitable lines passing over the edges 
6. Obtain fitting lines 

In order to draw a single line on the left and right lanes, I modified the draw_lines() function by separating into positive and negative slope . Besides filter into two branches of positive/negative slope, I apply a range of acceptable values for slope according to the plot of all possible hough lines. This range was within [0.4, 0.95] for positive slopes and [-0.95,-0.4] for negative slopes. Afterwards, I evaluate the average slope for left and right lines (positive/negative slopes) in order to find a single line for both cases. Finally, using simple linear equation  y = mx +b , I obtained the parameter b as well as extrapolate the right and left lines.


I would also like to include the images evolving during the process of finding lanes in the image:

1. Pipeline

![Application of pipeline](https://github.com/BrunoEduardoCSantos/Finding-lane-lines-on-the-road/blob/master/test_images_lines/houghlinessolidWhiteCurve.jpg.jpg)

 2. Fitting lines
 
![Application of pipeline2](https://github.com/BrunoEduardoCSantos/Finding-lane-lines-on-the-road/blob/master/test_output_images/messigraysolidWhiteCurve.jpg.png)


One potential shortcoming would be what would happen when showing horizontal lanes line in the image. The current drawline function can't handle this case.

A possible improvement would be to remove horizontal lines without removing the real lane lines.

Another potential improvement could be to application HSV filter to help canny edge method to spot better the lanes in the image.
