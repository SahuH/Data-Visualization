# CS766 (Spring 2022) Homework 3 submitted by Harsh Sahu (hsahu@wisc.edu)

## Walkthrough 1
* Threshold for Sobel edge detection: `0.105`
* Threshold for Canny edge detection: `0.20`

## Challenge 1a
Value of thresholds used:
* hough_1.png: `0.12`
* hough_2.png: `0.10`
* hough_3.png: `0.10`

## Challenge 1b
* In order to cover all values of &theta; between 0 to 180 degrees, no. of bins used for &theta; are: `180`
* Maximum size of &rho; can be equal to the hypotenuse of the image. For the given images, the maximum value of hypotenuse is about 780 pixels. So, in order to sufficiently represent all pixel values, no. of bins used for &rho; are: `800`

**No voting of adjacent pixels is used:** 
As the no. of bins is just right to represent all pixel values, voting to combine adjacent bin values is not implemented.

## Challenge 1c
A standard threshold method is used to find the peaks in hough accumulator.
After a lot of trial and error, the values of threshold for hough transforms are decided to be:
* hough_1.png: `110`
* hough_2.png: `50`
* hough_3.png: `55`

## Challenge 1d
As threshold method is used in 1c, same threshold are used here as well.

The following algorithm is followed to detect end-points, 
* For each image, edge image is considered, which was created in challenge 1a
* Traverse each line (or each value of (&theta;, &rho;)), starting with point at x = 0
* Move forward on the line pixel by pixel until a non-zero pixel is encountered. It is assigned as the starting point of the line segment
* Move forward on the line pixel by pixel until again a zero pixel is encountered. Now, this point is assigned as the end point of the line segment
* Plot the newly found line segment
* Repeat the process until the line terminates at the end of the image
* Repeat the process for all lines (for all values of (&theta;,&rho;))

In order to remove noisy edges with non-zero value aross multiple adjacent pixels, a convolution is also performed on edge image (created in challenge 1a). The formed convolved image is finally used to detect end-points.
