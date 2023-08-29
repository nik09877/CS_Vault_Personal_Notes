- uses Redux toolkit, express, react, socket.io, roughjs(for drawing)
- using useLayoutEffect() in whiteboard.js instead of useEffect() because the former one happens before browser paint , very imp to get access to canvas
- importing rough from 'roughjs' was not working so I imported from 'roughjs/bundled/rough.esm'
- drawing from top to bottom and bottom to top are different , so always make x1 and y1 as smaller numbers i.e swap coordinates.
![](Pasted_image_20230829174419.png)

![](Pasted_image_20230829174739.png)

![](Pasted_image_20230829195447.png)