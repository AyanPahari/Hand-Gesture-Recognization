
# Hand Gesture Recognization

I did this project about 4 years back during my bachelor's . I forgot to push it on github that time so doing it now ;)

## About the Project

We are going to recognize hand gestures from a video sequence. To recognize these gestures from a live video sequence, 
we first need to take out the hand region alone removing all the unwanted portions in the video sequence. 
After segmenting the hand region, we then count the fingers shown in the video sequence to instruct a robot based on the finger count. 
Thus, the entire problem could be solved using 2 simple step:

    1.	Find and segment the hand region from the video sequence.
    2.	Count the number of fingers from the segmented hand region in the video sequence.



## Requirements

- Python

        Python is the platform on this complete project is made. The version of this platform must be 2.7 or above.
- OpenCv 

        This is the basis library used in almost every program used in this project. Its version should be either 2.x or 3.x.
- Numpy library

        Used for type conversions, NumPy is a library for the Python programming language, adding support for large, 
        multi-dimensional arrays and matrices, along with a large collection of high-level mathematical functions to operate on these arrays.  
## Steps

#### 1.  Capture frames and convert to grayscale

    Our ROI is the hand region, so we capture the images of the hand and convert them to grayscale

![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)

#### 2.  Blur Image

    1. We used Gaussian Blurring on the original image. We blur the image for smoothing and to reduce noise and details from the image. 
       We are not interested in the details of the image but in the shape of the object to track.
    2. By blurring, we create smooth transitionfrom one color to another and reduce the edge content. 
       We use thresholding for image segmentation, to create binary images from grayscale images.

![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)

#### 3.  Thresholding

    1. In very basic terms, thresholding is like a Low Pass Filter by allowing onlyparticular color ranges to be highlighted as white while the other colors aresuppressed by showing them as black.
    2. We’ve used Otsu’s Binarization method. In this method, OpenCV automatically calculates/approximates the threshold value of a bimodal image from its image histogram. But for optimal results, we may need a clear background in front of the webcam which sometimes may not be possible.

![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)

#### 4.  Draw Contours

    Using the threshold image we draw the contours

![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)

#### 5. Find convex hull and convexity defects

    We now find the convex points and the defect points. The convex points are generally, the tip of the fingers. But there are other convex point too. So, we find convexity defects, which is the deepest point of deviation on the contour. By this we can find the number of fingers extended and then we can perform different functions accordingto the number of fingers extended.

![App Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)


## Screenshots

![Output Screenshot](https://via.placeholder.com/468x300?text=App+Screenshot+Here)

#### Note

The background of the red square should either be white or black to avoid any sort of outside noise.