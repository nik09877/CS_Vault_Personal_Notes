# Problems
- uses Redux toolkit, express, react, socket.io, roughjs(for drawing)
- using useLayoutEffect() in whiteboard.js instead of useEffect() because the former one happens before browser paint , very imp to get access to canvas
- importing rough from 'roughjs' was not working so I imported from 'roughjs/bundled/rough.esm'
- drawing from top to bottom and bottom to top are different , so always make x1 and y1 as smaller numbers i.e swap coordinates.
- I had a problem in syncing the other user who joined late, so instead of updating a single element we update the whole elements array to new array and send it to all users except the current one
- In Global state we are storing elements and type
- Each element consists of { x1,y1,x2,y2,id,type}
- in case of pencil it is {id,type,points[] array}
- in case of text it is {id,type,x1,y1,textContent}
- When you are moving the mouse we need to check which element it points to currently.
- in MOVING ELEMENTS WorkFlow we have to find whether the user mouse position lies with in an element i.e `getElementAtPosition()` function
- When resizing elements the edge case is when you resize element diagonally and drag it down , it's size will decrease and become 0 and after that it will increase and become another element, but here the element coordinates are scrambled, so we need to readjust the element coordinates when `mouseUp` event is fired.
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

# PENCIL WORKFLOW
![](Pasted_image_20230830135823.png)
![](Pasted_image_20230830141852.png)
- used perfect free hand npm
- It takes points[] array and does the drawing 

# TEXT WORKFLOW
![](Pasted_image_20230830153018.png)

![](Pasted_image_20230830155327.png)

- jumping effect problem
```Javascript
//If we are currently writing and we click somewhere else we should return from handleMouseDown function
if (selectedElement && action === actions.WRITING) {
      return;
    }
in handleOnBlur do
{
	setAction(null);
    setSelectedElement(null);
}
```

# RESIZING AND MOVING ELEMENTS WORKFLOW
![](Pasted_image_20230831130556.png)
![](Pasted_image_20230831143251.png)
![](Pasted_image_20230831144901.png)

# Moving Lines
![](Pasted_image_20230831184454.png)

# Moving PENCIL DRAWN ELEMENTS
- Treat it as a collection of several points i.e apply same logic as moving Lines

# SHARING CURSOR POSITION
- on Mouse Move we get a `clientX,clientY` from the `event` variable
- Here we need to emit cursor position i.e `{clientX,clientY,userId/socketId}` to all other clients
- This event gets fired thousands of time so we need to restrict it to send up to 20 times
```Javascript
const handleMouseMove = (event) => {
	const { clientX, clientY } = event;
	    //EMIT CURSOR POSITION TO OTHER CLIENTS
	
	    lastCursorPosition = { x: clientX, y: clientY };
	
	    if (emitCursor) {
	
	      emitCursorPosition({ x: clientX, y: clientY });
	
	      emitCursor = false;
	
	      setTimeout(() => {
	
	        emitCursor = true;
	
	        emitCursorPosition(lastCursorPosition);
	
	      }, 50);
	
	}
}
```