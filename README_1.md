# CS766 (Spring 2022) Homework 4 submitted by Harsh Sahu (hsahu@wisc.edu)

## Challenge 1a
* Calculates Homography between two Images
* Applies homography on a set of points in the source image and outputs corresponding points in the destination image
* Shows matching of corresponding points between the source and destination image

## Challenge 1b
* Calculates homography between the portrait image and the background
* Backward-warps the portrait image according to the background using the inverse of the calculated Homography matrix
* Superimpose the warped portrait onto the background. Used `interp2` function to fill in the missing pixels

## Challenge 1c
* Given a corresponding set of points on two images along with outliers, the RANSAC algorithm is implemented to remove the outliers
* Matching points are shown onto the two images after removing outliers using RANSAC

## Challenge 1d
### Overlay
Images are overlayed onto each other using a binary mask
### Blend
`bwdist` is used to create a mask where pixels close to the edges of the image are blurred out. Using this, two images are overlapped with each other, creating a fading effect at the junction.

## Challenge 1e
A function is created to take an arbitrary number of images and stitched them together to create a panorama. Three images of a mountain view are combined to create a mountain panorama.

## Challenge 1f
I have used two of my captured photos `chicago_1.png` and `chicago_2.png` of the same building during my trip to Chicago and created a panorama `chicago_panorama.png`

