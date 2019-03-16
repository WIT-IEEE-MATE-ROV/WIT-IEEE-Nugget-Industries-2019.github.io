# Line Follower
This algorithm is handled by the `line-follower` module.

## Basic Operation
The algorithm begins by converting what it sees into two masks: one looks for 
an acceptable range of red values, and another looks for an acceptable range of blue values.
The image produced using the red mask checks the four sides of the image to check if the red line intersects with that face.
If it does, the combination of faces with red lines indicates the shape of the line. Context then indicates what this 
shape means.

Given the inputs of an x position, y position, orientation, and length, the `damoverlay` creates a new window with an empty grid of the dam foundation and the blue line that represents the crack. The location of the blue line is determined by multiplying the x and y positions by a scalar equal to the width of one grid tile. The blue line's orientation influences whether a horizontal or vertical line is drawn. The length up to three significant digits is also printed in the same tile as the blue line.

## Flowchart
TODO

## Pseudocode
TODO
