# Line Follower
This algorithm is handled by the `line-follower` module.

## Basic operation
The algorithm begins by converting what it sees into two masks: one looks for 
an acceptable range of red values, and another looks for an acceptable range of blue values.
The image produced using the red mask checks the four sides of the image to check if the red line intersects with that face.
If it does, the combination of faces with red lines indicates the shape of the line. Context then indicates what this 
shape means.

## Flochart
TODO

## Pseudocode
TODO
