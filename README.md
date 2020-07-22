# Lane Detection with Real Time

## Overview
Lane detection is one of the most crucial technique of ADAS and has received significant attention recently. In this project, we achived lane detection with real time by numpy and multi-thread.

## Dependencies
* Python
* Numpy
* Opencv

## How to Run
Run `lane_detection.py`. The default video is project_video, if you want to process the "fog_video.mp4", change video_index to 1 in line 9.

## Process Pipeline

### Region of Interest
* Warp a certain region of the image to a bird’s eye view perspective to detect the lane pixels appropriately.
![image](https://github.com/dongdonghy/realtime_lane_detection/raw/master/images/ROI.jpg)

### Gradient and Color Thresholding
* Transform the image from RGB to HSV
* Calculate x directional gradient of l channel
* Color Threshold of s channel
* Combine the two binary thresholds
![image](https://github.com/dongdonghy/realtime_lane_detection/raw/master/images/threshold.jpg)

### Polynomial Fitting
* Find the peak of the left and right halves of the histogram
* Identify the x and y positions of all nonzero pixels in the image
* Step through the windows one by one
* Extract left and right line pixel positions
![image](https://github.com/dongdonghy/realtime_lane_detection/raw/master/images/result.jpg)

### Multi-Thread
* The adjacent frames are very similar to each other because of the high FPS
* Process the image every 5 frames by child thread, and add the result to the main frame
