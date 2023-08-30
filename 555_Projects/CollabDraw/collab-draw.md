- uses Redux toolkit, express, react, socket.io, roughjs(for drawing)
- using useLayoutEffect() in whiteboard.js instead of useEffect() because the former one happens before browser paint , very imp to get access to canvas
- importing rough from 'roughjs' was not working so I imported from 'roughjs/bundled/rough.esm'
- drawing from top to bottom and bottom to top are different , so always make x1 and y1 as smaller numbers i.e swap coordinates.
- I had a problem in syncing the other user who joined late, so instead of updating a single element we update the whole elements array to new array and send it to all users except the current one
![](Pasted_image_20230829174419.png)

![](Pasted_image_20230829174739.png)

![](Pasted_image_20230829195447.png)


![](Pasted_image_20230830120834.png)

# WorkFlow of Drawing
- On mouse down create a rough element and track the x1,y1,x2,y2 pos (x1=x2 and y1=y2), set selectedElement to current created element.
- on mouse move just keep updating x2,y2
- on mouse up setAction to null from drawing and set selectedElement to null
- when the elements are updated our useLayoutEffect runs which depend upon the the elements and draw the elements on our canvas.

# RUBBER WORKFLOW
![](Pasted_image_20230830125918.png)

![](Pasted_image_20230830130013.png)

