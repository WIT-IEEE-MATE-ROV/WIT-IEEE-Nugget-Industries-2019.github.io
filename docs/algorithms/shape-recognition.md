# Shape Detection
This algorithm is handled by the `shape-detection` module.

## Shape Recognition
For this competition, we were required to use machine vision to detect varying organisms placed under a rock. To accomplish this we used OpenCV, With this library, we can analyze images and extract data from them. The organisms we need to classify differ in size and shape, knowing this we planned to use the number of contours each organism has to differentiate between them. We begin this by first grabbing a frame from our video stream and masking it. Our mask consists of a combination of restricting HSV values, Dilation, and Morphology. Using this we are able to filter out much of the noise in the image and move on to the contour detection. To pull the contours out of an image we used the Cv2.Findcontours command, Once we have found all of the contours in the image we can count them to determine what organisms are under the rock. However, if the organism has four counters an additional check is required to determine if it is a square or a rectangle. So when the code encounters a four contour object it takes the ratio of length to width of the object based on its pixels. If it's in our range for a square then its a square organism and if not then its a rectangular organism.
The `addoverlay` function takes the number of squares, rectangles, triangles, and circles from the `detectsquares`, `detecttriangles`, and `detectcircles` functions and displays them next to the symbol of the respective shape on top of the live video feed.

## Flowchart
![Flowchart](./flowchart.png)

## Output Image
![Output Image](./output.png)
